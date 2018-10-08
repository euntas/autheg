# autheg/autheg-backend/Dockerfile
FROM ruby:2.5

ARG UID
RUN adduser rails --uid $UID --disabled-password --gecos ""
# 可以透過 $UID 給予不同的 user ID，並且進到任何的 container 都可以用相同的 user ID
# --disabled-password - 讓 rails 無法用密碼登入
# --gecos 用戶的詳細訊息（如姓名，年齡，電話等），因為 adduser 會提示你輸入用戶的密碼和相關的finger訊息，但是這個可以用選項--gecos來覆蓋。

ENV APP /usr/src/app
RUN mkdir $APP
WORKDIR $APP

COPY Gemfile* $APP/
RUN bundle install -j3 --path vendor/bundle
# Gems and yarn packages are installed into the mounted volumes. 
# This will stop you from needing to rebuild the whole Docker image every time you change the Gemfile or package.json.

COPY . $APP/

CMD ["bin/rails", "server", "-p", "8080", "-b", "0.0.0.0"]
# 這裡原本是 rails，但實際在 run 的時候會有 error，因此改為 bin/rails
