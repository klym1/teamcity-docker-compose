FROM jetbrains/teamcity-minimal-agent:latest

RUN apt-get update && apt-get install -y \
    wget \
    git \
    software-properties-common
    
RUN wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

RUN dpkg -i packages-microsoft-prod.deb

RUN add-apt-repository universe \
 && apt-get install -y apt-transport-https \
 && apt-get update \
 && apt-get install -y dotnet-sdk-2.2

RUN dotnet tool install --global dotnet-sonarscanner

ENV PATH="${PATH}:/root/.dotnet/tools"
