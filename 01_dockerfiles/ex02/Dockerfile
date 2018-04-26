FROM debian

RUN apt-get update -y && \
	apt-get upgrade -y && \
	apt-get install -y gcc zlib1g ruby ruby-dev && \
	gem update --system && \
	gem install rails
