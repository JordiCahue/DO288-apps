# Use the httpd-parent image as base
FROM httpd:2.4

ENV DOCROOT=/var/www/html

LABEL io.k8s.description="A basic Apache http server child image, uses ONBUILD" \
      io.k8s.display-name="Apache http server" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="apache, httpd"

COPY src/ ${DOCROOT}/

RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf.d/httpd.conf && \
    chgrp -R 0 /var/log/httpd24 /var/run/httpd && \
    chmod -R g=u /var/log/httpd24 /var/run/httpd

EXPOSE 8080

USER 1001

CMD httpd -DFOREGROUND 

