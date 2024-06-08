FROM ubuntu:22.04


# Install Nginx
RUN apt-get update && apt-get install -y nginx libnginx-mod-rtmp ffmpeg tzdata

RUN mkdir /var/www/html/stream
# Copy the custom nginx.conf to the container
COPY nginx.conf /etc/nginx/nginx.conf

RUN mkdir /var/www/html/rtmp
COPY stat.xsl /var/www/html/rtmp/stat.xsl
#RUN cp /usr/share/doc/libnginx-mod-rtmp/examples/stat.xsl /var/www/html/rtmp/stat.xsl #BUG: stat.xsl not found in /usr/share/doc/libnginx-mod-rtmp/examples/

#copy site configuration
COPY streamer /etc/nginx/sites-enabled/streamer

#start nginx deamon
CMD ["nginx", "-g", "daemon off;"]