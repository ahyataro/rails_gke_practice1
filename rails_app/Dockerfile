FROM ruby:2.4.0
ENV LANG C.UTF-8
RUN apt-get update -qq && apt-get install -y build-essential nodejs
RUN mkdir /myapp
WORKDIR /myapp
ADD Gemfile Gemfile.lock /myapp/

ENV RAILS_ENV production

ADD . /myapp

RUN bundle install --path vendor/bundle

CMD \
    bundle exec rails db:create && \
    bundle exec rails db:migrate && \
    bundle exec rake assets:precompile && \
    bundle exec unicorn -c config/unicorn.rb -E production
