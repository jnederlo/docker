FROM			ruby

RUN				apt-get update
RUN				gem install rails
RUN				apt-get install nodejs -y
RUN				apt-get install build-essential -y

EXPOSE			3000

COPY			. /opt/app

ONBUILD WORKDIR	/opt/app/rubySample/webapp

ONBUILD RUN		bundle install

ONBUILD RUN		rails db:migrate
ONBUILD RUN		rails db:seed

