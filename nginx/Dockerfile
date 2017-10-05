FROM nginx:1.11.7
RUN rm -f /etc/nginx/conf.d/*
ADD nginx.conf /etc/nginx/conf.d/
CMD /usr/sbin/nginx -g 'daemon off;' -c /etc/nginx/conf.d/nginx.conf