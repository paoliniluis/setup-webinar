FROM eclipse-temurin:21-jre-noble AS runner

ENV FC_LANG en-US LC_CTYPE en_US.UTF-8
ARG version

WORKDIR /app/

RUN apt-get update && \
  apt-get upgrade -y && \
  # I'm removing the noto fonts on purpose
  apt-get install -y ca-certificates ca-certificates-java && \
  apt-get clean && \
  curl https://s3.amazonaws.com/rds-downloads/rds-combined-ca-bundle.pem -o /usr/local/share/ca-certificates/rds-combined-ca-bundle.pem && \
  curl https://cacerts.digicert.com/DigiCertGlobalRootG2.crt.pem -o /usr/local/share/ca-certificates/DigiCertGlobalRootG2.crt.pem && \
  update-ca-certificates && \
  mkdir -p /plugins && chmod a+rwx /plugins && \
  keytool -list -cacerts && \
  curl https://downloads.metabase.com/enterprise/${version}/metabase.jar -o metabase.jar && \
  chmod -R a+rwX /app/

# expose our default runtime port
EXPOSE 3000

# run it
ENTRYPOINT ["java", "-jar", "metabase.jar"]