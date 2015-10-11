FROM devruby

# Install MeCab
RUN mkdir -p /usr/src/mecab \
    && curl -SL https://mecab.googlecode.com/files/mecab-0.996.tar.gz \
       | tar -xzC /usr/src/mecab \
    && cd /usr/src/mecab/mecab-0.996 \
    && ./configure --enable-utf8-only && make && make install \
    && ldconfig

# Install IPADic
RUN curl -SL https://mecab.googlecode.com/files/mecab-ipadic-2.7.0-20070801.tar.gz \
       | tar -xzC /usr/src/mecab \
    && cd /usr/src/mecab/mecab-ipadic-2.7.0-20070801 \
    && ./configure --with-charset=utf8  && make && make install \
    && echo "dicdir = /usr/local/lib/mecab/dic/ipadic" > /usr/local/etc/mecabrc

# gem natto
RUN gem install natto

# Cleanup
RUN rm -rf /usr/src/mecab

CMD ["/bin/bash"]


