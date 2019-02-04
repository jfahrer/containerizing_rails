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

COPY . .

RUN bundle install

CMD ["rails", "console"]
