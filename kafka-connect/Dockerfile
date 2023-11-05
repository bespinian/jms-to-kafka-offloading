FROM confluentinc/cp-kafka-connect:7.5.1

USER root

RUN yum update -y && yum install -y unzip

RUN mkdir -p /usr/local/share/kafka/plugins/kafka-connect-jms

# Fetch the kafka-connect-jms zip file and extract its contents
RUN wget -O /tmp/kafka-connect-jms-5.0.1.zip https://github.com/lensesio/stream-reactor/releases/download/5.0.1/kafka-connect-jms-5.0.1.zip && \
    unzip /tmp/kafka-connect-jms-5.0.1.zip -d /usr/local/share/kafka/plugins/kafka-connect-jms && \
    rm /tmp/kafka-connect-jms-5.0.1.zip

# Fetch the activemq-client jar and activemq-all jar files and place them in the same directory
RUN wget -O /usr/local/share/kafka/plugins/kafka-connect-jms/activemq-client-5.12.3.jar https://repo1.maven.org/maven2/org/apache/activemq/activemq-client/5.12.3/activemq-client-5.12.3.jar && \
    wget -O /usr/local/share/kafka/plugins/kafka-connect-jms/activemq-all-5.12.3.jar https://repo1.maven.org/maven2/org/apache/activemq/activemq-all/5.12.3/activemq-all-5.12.3.jar

# Cleanup
RUN yum remove -y wget unzip && yum clean all

USER appuser