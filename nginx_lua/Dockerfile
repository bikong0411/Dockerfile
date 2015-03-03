FROM ubuntu:14.10
MAINTAINER sky <bikong0411@gmail.com>
ENV REFRESH_DATE 2015-01-22
RUN apt-get -y update
RUN apt-get -y install wget make gcc g++  libpcre3 libpcre3-dev  openssl libssl-dev git
RUN mkdir -p /root/install
WORKDIR /root/install
RUN  wget http://luajit.org/download/LuaJIT-2.0.2.tar.gz
RUN  tar zxf LuaJIT-2.0.2.tar.gz
WORKDIR /root/install/LuaJIT-2.0.2
RUN  make && make install

RUN ln -s /usr/local/lib/libluajit-5.1.so.2 /usr/lib/libluajit-5.1.so.2

WORKDIR /root/install
RUN git clone https://github.com/agentzh/echo-nginx-module.git
RUN git clone https://github.com/simpl/ngx_devel_kit.git
RUN git clone https://github.com/chaoslawful/lua-nginx-module.git
RUN wget http://nginx.org/download/nginx-1.4.2.tar.gz
RUN tar zxf nginx-1.4.2.tar.gz
WORKDIR /root/install/nginx-1.4.2
ENV LUAJIT_LIB /usr/local/lib
ENV LUAJIT_INC /usr/local/include/luajit-2.0
RUN  ./configure --prefix=/usr/local/nginx-1.4.2 --add-module=../echo-nginx-module --add-module=../lua-nginx-module --add-module=../ngx_devel_kit
RUN make -j2
RUN make install
RUN ln -s /usr/local/nginx-1.4.2 /usr/local/nginx
COPY conf/nginx.conf /usr/local/nginx/conf/nginx.conf

EXPOSE 80
ENTRYPOINT ["/usr/local/nginx/sbin/nginx"]
CMD ["/usr/local/nginx/sbin/nginx"]
