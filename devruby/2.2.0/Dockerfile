FROM devbase

ENV RUBY_MAJOR 2.2
ENV RUBY_VERSION 2.2.0

RUN apt-get update && apt-get install -y --no-install-recommends \
            bison libgdbm-dev ruby \
            && rm -rf /var/lib/apt/lists/* \
            && mkdir -p /usr/src/ruby \
            && curl -SL "http://cache.ruby-lang.org/pub/ruby/$RUBY_MAJOR/ruby-$RUBY_VERSION.tar.bz2" \
                    | tar -xjC /usr/src/ruby --strip-component=1 \
            && cd /usr/src/ruby \
            && autoconf \
            && ./configure --disable-install-doc \
            && make -j"$(noproc)" \
            && make install \
            && apt-get purge -y --auto-remove bison libgdbm-dev ruby \
            && rm -r /usr/src/ruby

RUN echo 'gem: --no-rdoc --no-ri' >> "$HOME/.gemrc"

ENV GEM_HOME /usr/local/bundle
ENV PATH $GEM_HOME/bin:$PATH

RUN gem install bundler \
    && bundle config --global path "$GEM_HOME" \
    && bundle config --global bin "$GEM_HOME/bin"

ENV BUNDLE_APP_CONFIG $GEM_HOME

CMD ["/bin/bash"]


