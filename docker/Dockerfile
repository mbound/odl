FROM anapsix/alpine-java:8_jdk as getodl

RUN mkdir /odl
WORKDIR /odl

ENV basename karaf
ENV release 0.8.4

RUN apk add openssl
RUN wget "https://nexus.opendaylight.org/content/repositories/public/org/opendaylight/integration/${basename}/${release}/${basename}-${release}.tar.gz"
RUN tar xvzf ${basename}-${release}.tar.gz && mv ${basename}-${release} opendaylight

FROM anapsix/alpine-java:8_jdk

RUN mkdir -p /root/odl
WORKDIR /root/odl

COPY --from=getodl /odl/opendaylight .

# 8181 : API
# 6633 : Openflow
# 8101 : ODL cli

EXPOSE 8181 6633 8101 8080

CMD ./bin/karaf

