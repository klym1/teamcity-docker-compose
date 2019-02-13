FROM jetbrains/teamcity-minimal-agent:latest

RUN curl -L https://packagecloud.io/golang-migrate/migrate/gpgkey | apt-key add -
RUN echo "deb https://packagecloud.io/golang-migrate/migrate/ubuntu/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/migrate.list

RUN apt-get update && apt-get install -y \
    wget \
    git \
    migrate \
    software-properties-common
    
RUN wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

RUN dpkg -i packages-microsoft-prod.deb

RUN add-apt-repository universe \
 && apt-get install -y apt-transport-https \
 && apt-get update \
 && apt-get install -y dotnet-sdk-2.2

RUN dotnet tool install --global dotnet-sonarscanner
RUN dotnet tool install --global coverlet.console

ENV PATH="${PATH}:/root/.dotnet/tools"
