FROM ruby:2.7.0-preview1-alpine3.10
RUN apk update && apk add build-base nodejs postgresql-dev wget git tzdata less
ENV RAILS_ENV=development
ENV RACK_ENV=development
ENV RAILS_SERVE_STATIC_FILES true
ENV RAILS_LOG_TO_STDOUT true
ENV NLS_LANG=AMERICAN_AMERICA.UTF8
ENV RAILS_ROOT /var/www/hbt-api
RUN mkdir -p $RAILS_ROOT
WORKDIR $RAILS_ROOT
COPY Gemfile Gemfile
COPY Gemfile.lock Gemfile.lock
COPY entrypoint.sh /usr/bin/
RUN bundle install --binstubs && \
    chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]

COPY . .

LABEL maintainer="Antonio Rosas <antonio@avispa.tech>"

CMD ["bundle", "exec", "puma", "-C", "config/puma.rb"]