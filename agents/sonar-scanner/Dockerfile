FROM jetbrains/teamcity-minimal-agent:latest

RUN apt-get update && apt-get install -y \
    gnupg2 \
    wget \
    locales

# nodejs
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - && apt-get -y install nodejs
# gulp
RUN npm install -g gulp-cli

WORKDIR /root

RUN curl --insecure -o ./sonarscanner.zip -L https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.3.0.1492-linux.zip && \
    unzip sonarscanner.zip && \
    rm sonarscanner.zip && \
    mv sonar-scanner-3.2.0.1227-linux sonar-scanner

ENV SONAR_RUNNER_HOME=/root/sonar-scanner
ENV PATH $PATH:/root/sonar-scanner/bin

COPY sonar-runner.properties ./sonar-scanner/conf/sonar-scanner.properties

# Use bash if you want to run the environment from inside the shell, otherwise use the command that actually runs the underlying stuff
#CMD /bin/bash
CMD sonar-scanner -Dsonar.projectBaseDir=./src