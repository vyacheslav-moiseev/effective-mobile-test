FROM nginx:1.25-alpine

RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

HEALTHCHECK --interval=10s --timeout=2s --retries=3 CMD wget -qO- http://localhost || exit 1

CMD ["nginx", "-g", "daemon off;"]