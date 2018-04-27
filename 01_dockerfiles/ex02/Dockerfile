FROM debian

RUN apt-get update -y
RUN apt-get upgrade -y
RUN apt-get install -y \
			ca-certificates \
			curl \
			wget \
			bzr \
			git \
			mercurial \
			openssh-client \
			subversion \
			procps \
			autoconf \
			automake \
			bzip2 \
			dpkg-dev \
			file \
			g++ \
			gcc \
			imagemagick \
			libbz2-dev \
			libc6-dev \
			libcurl4-openssl-dev \
			libdb-dev \
			libevent-dev \
			libffi-dev \
			libgdbm-dev \
			libgeoip-dev \
			libglib2.0-dev \
			libjpeg-dev \
			libkrb5-dev \
			liblzma-dev \
			libmagickcore-dev \
			libmagickwand-dev \
			libncurses5-dev \
			libncursesw5-dev \
			libpng-dev \
			libpq-dev \
			libreadline-dev \
			libsqlite3-dev \
			libssl-dev \
			libtool \
			libwebp-dev \
			libxml2-dev \
			libxslt-dev \
			libyaml-dev \
			make \
			patch \
			xz-utils \
			zlib1g-dev \
			bison \
			dpkg-dev \
			ruby \
			ruby-dev \
			sqlite3

ENV GEM_HOME /usr/local/bundle
ENV BUNDLE_PATH="$GEM_HOME" \
	BUNDLE_BIN="$GEM_HOME/bin" \
	BUNDLE_SILENCE_ROOT_WARNING=1 \
	BUNDLE_APP_CONFIG="$GEM_HOME"
ENV PATH $BUNDLE_BIN:$PATH
RUN mkdir -p "$GEM_HOME" "$BUNDLE_BIN" \
	&& chmod 777 "$GEM_HOME" "$BUNDLE_BIN"

ONBUILD RUN gem update --system
ONBUILD RUN gem install rails
ONBUILD EXPOSE 3000
ONBUILD COPY [".", "/opt/app"]
ONBUILD WORKDIR /opt/app
