FROM ruby:2.3.1
ENV LANG C.UTF-8
RUN apt-get update -qq && apt-get install -y build-essential nodejs
RUN mkdir /myapp
WORKDIR /myapp
ADD Gemfile Gemfile.lock /myapp/

ENV RAILS_ENV production

ADD . /myapp

RUN bundle install --path vendor/bundle

CMD \
    bundle exec rails db:migrate && \
    bundle exec rake assets:precompile && \
    bundle exec unicorn_rails -c config/unicorn.rb -E production -D

