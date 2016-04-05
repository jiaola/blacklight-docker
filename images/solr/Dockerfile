FROM solr:5.5

MAINTAINER David Jiao <dazhi.jiao@gmail.com>

USER root

ENV PATH /opt/solr/bin:${PATH}
ENV SOLR_HOME /var/solr/data/
ENV BLACKLIGHT_CORE ${SOLR_HOME}blacklight/

RUN mkdir -p ${BLACKLIGHT_CORE}

ADD solr.xml ${SOLR_HOME}
ADD core.properties ${BLACKLIGHT_CORE}

ADD ./gitdownloader-1.0.jar /opt/solr/gitdownloader-1.0.jar

RUN java -jar /opt/solr/gitdownloader-1.0.jar https://api.github.com/repos/projectblacklight/blacklight/contents/solr/conf ${BLACKLIGHT_CORE}conf

VOLUME ["/var/solr"]

WORKDIR /opt/solr
CMD ["sh", "-c", "solr start -f"]
# CMD solr start -f
