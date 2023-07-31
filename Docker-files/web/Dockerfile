FROM nginx
LABEL "Project"="Containerization_Project"
LABEL "Author"="CMT35"

# Remove the default nginx configuration file 
RUN rm-rf /etc/nginx/conf.d/default.conf
# Copy our custom conf file (nginvproapp.conf) to the default conf directory
COPY nginvproapp.conf /etc/nginx/conf.d/default.conf