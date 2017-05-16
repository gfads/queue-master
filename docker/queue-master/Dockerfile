FROM weaveworksdemos/msd-java:latest


WORKDIR /usr/src/app
COPY *.jar ./app.jar

RUN mkdir -p /usr/src/app/certs && \
    echo -n " \
!#/bin/sh \
keytool -import -alias kay.cs.ubc.ca -file /usr/src/app/certs/ca.pem \
/usr/local/bin/java.sh -jar ./app.jar --port=80 \
" > load-ca.sh && chmod +x load-ca.sh


ENV JAVA_OPTS "-Djava.security.egd=file:/dev/urandom"
#ENTRYPOINT ["/usr/local/bin/java.sh","-jar","./app.jar", "--port=80"]
ENTRYPOINT ["./load-ca.sh"]
