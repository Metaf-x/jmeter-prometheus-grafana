# Базовый образ Apache JMeter
FROM alpine/jmeter:5.4.1

# Создание необходимых директорий
RUN mkdir -p /jmeter/lib/ext && \
  mkdir -p /jmeter/lib

# Установка плагинов напрямую через wget
RUN wget https://repo1.maven.org/maven2/kg/apc/jmeter-plugins-cmn-jmeter/0.7/jmeter-plugins-cmn-jmeter-0.7.jar  -O /jmeter/lib/ext/jmeter-plugins-cmn-jmeter-0.7.jar && \
  wget https://repo1.maven.org/maven2/kg/apc/jmeter-plugins-casutg/2.10/jmeter-plugins-casutg-2.10.jar  -O /jmeter/lib/ext/jmeter-plugins-casutg-2.10.jar && \
  wget https://repo1.maven.org/maven2/com/blazemeter/jmeter-plugins-wsc/0.7/jmeter-plugins-wsc-0.7.jar  -O /jmeter/lib/ext/jmeter-plugins-wsc-0.7.jar

# Копирование конфигурации Prometheus
COPY plugins/jmeter-prometheus-plugin-0.7.1.jar /jmeter/lib/ext/

# Фиксим пути
ENV JMETER_HOME=/opt/apache-jmeter
ENV PATH=$JMETER_HOME/bin:$PATH
WORKDIR /tests