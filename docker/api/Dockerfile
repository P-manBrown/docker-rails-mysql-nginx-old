FROM ruby:3.1.2
ARG APP_NAME=myapp-backend
ARG USER_NAME=ruby
ENV TZ=Asia/Tokyo

WORKDIR /${APP_NAME}

COPY Gemfile /${APP_NAME}/Gemfile
COPY Gemfile.lock  /${APP_NAME}/Gemfile.lock
RUN bundle install

COPY /docker/api/entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]

RUN adduser ${USER_NAME} && \
    chown -R ${USER_NAME} /${APP_NAME} && \
    chown -R ${USER_NAME} ${GEM_HOME}
USER ${USER_NAME}

EXPOSE 3000

CMD ["rails", "server", "-b", "0.0.0.0"]