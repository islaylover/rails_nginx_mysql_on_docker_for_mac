# Base image
FROM nginx

# install depedencies
RUN apt-get update -qq && apt-get -y install apache2-utils

# establish where Nginx should look for files
ENV RAILS_ROOT /var/www/rails_app

WORKDIR $RAILS_ROOT
RUN mkdir -p log

# Copy Nginx config template
COPY nginx/app.conf /tmp/docker_example.nginx

# substitute variable references in the Nginx config template for real values from the environment
# put the final config in its place
RUN envsubst '$RAILS_ROOT' < /tmp/docker_example.nginx > /etc/nginx/conf.d/default.conf

EXPOSE 80

# run nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]