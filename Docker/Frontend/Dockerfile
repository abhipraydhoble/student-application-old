FROM amazonlinux
RUN yum update -y && \
    yum install -y httpd 
COPY index.html /var/www/html/index.html
EXPOSE 80
CMD ["httpd", "-D", "FOREGROUND"]
