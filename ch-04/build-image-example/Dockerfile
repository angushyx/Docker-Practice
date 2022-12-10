FROM ruby:3.1.2-alpine
ENV AUTHOR=angushyx

EXPOSE 3000

CMD ["bundle", "exec", "ruby", "whoami.rb", "-p", "3000", "-o", "0.0.0.0"]

WORKDIR /app

RUN apk add --update --no-cache \
    build-base \
    curl

COPY . .


RUN gem install bundler:2.3.19 && \
    bundle install -j4 --retry 3 && \
    bundle clean --force && \
    find /usr/local/bundle -type f -name '*.c' -delete && \
    find /usr/local/bundle -type f -name '*.o' -delete && \
    rm -rf /usr/local/bundle/cache/*.gem

