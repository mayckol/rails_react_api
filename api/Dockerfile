FROM ruby:2.7.2
# throw errors if Gemfile has been modified since Gemfile.lock
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs

RUN bundle config --global frozen 1

RUN mkdir -p /app/api
WORKDIR /app/api

RUN gem install bundler:2.2.2

COPY Gemfile /app/api/Gemfile
COPY Gemfile.lock /app/api/Gemfile.lock

RUN bundle config --global frozen 0
RUN bundle install

COPY . .

# COPY ./docker-entrypoint.sh /
# RUN chmod +x /docker-entrypoint.sh

# ENTRYPOINT ["/docker-entrypoint.sh"]
# EXPOSE 3001

# CMD ["bundle", "exec", "rails", "server", "-b", "0.0.0.0"]