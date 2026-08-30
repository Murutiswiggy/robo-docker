FROM nginx:1.24.0
RUN rm -rf /usr/share/nginx/html/
RUN rm -rf /usr/share/nginx/html/*

COPY static /usr/share/nginx/html/
COPY nginx.conf /usr/share/nginx/html/*