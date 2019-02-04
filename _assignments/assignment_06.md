# Assignment 6 - Utilizing layers
In order to speed up our build process, we should take advantage of Docker's build cache. Right now we re-install all gems whenever we make a change to our source code and rebuild the image. That takes time and is annoying. We can easily work around this by copying the `Gemfile` and `Gemfile.lock` separately. Change your Dockerfile so that it looks more like this:
```
FROM jfahrer/ruby-on-ice:2.5.3-alpine

RUN apk add --update --no-cache \
      bash \
      build-base \
      nodejs \
      sqlite-dev \
      tzdata \
      postgresql-dev

RUN gem update bundler

WORKDIR /usr/src/app

COPY Gemfile Gemfile.lock ./
RUN bundle install

COPY . .

CMD ["rails", "console"]
```

The key change here is that we copy our `Gemfile` and `Gemfile.lock` separately and run bundle install BEFORE we copy all of the source code. As long as the two haven't changed, we can use the intermediate image from the build cache.

Rebuild the image with the changes in place:
```
docker image build -t your_docker_id/rails_app:v1 .
```

To make sure it works, let's make a small change to our source code. Simply add or change some text in `app/views/books/index.html.erb` and then rebuild the image. You should see that the `RUN bundle install` instruction is not executed but retrieved from the cache.

## Bonus
* Try invalidating the build cache by adding an empty line to your `Gemfile`

[Back to the overview](../README.md#assignments)
