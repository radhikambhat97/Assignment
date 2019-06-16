#FROM ubuntu

#RUN apt-get update
#ENV DEBIAN_FRONTEND=noninteractive 
#RUN apt-get install -y nginx
#RUN rm -f /etc/nginx/sites-enabled/default

#COPY nginx.conf /etc/nginx/sites-enabled/default

#RUN systemctl nginx restart

#EXPOSE 80 
#FROM nginx

#MAINTAINER Kailash Verma <kailashverma2402@gmail.com>

#RUN rm -f /etc/nginx/nginx.conf

#ADD nginx.conf /etc/nginx/nginx.conf

#RUN service nginx restart

#EXPOSE 80
FROM ubuntu

#MAINTAINER Chris Fidao

RUN apt-get update \
    && apt-get install -y nginx \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && echo "daemon off;" >> /etc/nginx/nginx.conf

COPY default /etc/nginx/sites-available/default

EXPOSE 80
CMD ["nginx"]
