FROM python:3.10-slim
WORKDIR /app
#COPY queue_exporter.py /app/
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 5000-5200

#Conector
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build_conector
ARG ConectorSolution=HubinIO.Connectors.VtexV3
ENV ConectorSolution=$ConectorSolution
WORKDIR /src
#COPY ["/src/${ConectorSolution}/${ConectorSolution}.csproj", "src/${ConectorSolution}/"]
#COPY ["/src/${ConectorSolution}.Domain/${ConectorSolution}.Domain.csproj", "src/${ConectorSolution}.Domain/"]
#COPY ["/src/${ConectorSolution}.Repository/${ConectorSolution}.Repository.csproj", "src/${ConectorSolution}.Repository/"]
#COPY ["/Nuget.Config", "/src"]
##RUN dotnet restore "src/${ConectorSolution}/${ConectorSolution}.csproj" --configfile Nuget.Config
##COPY . .
##WORKDIR "/src/src/${ConectorSolution}"
##RUN dotnet build "${ConectorSolution}.csproj" -c Release-Kubernetes -o /app/build#
##Conector
#FROM build_conector AS publish_conector
#RUN dotnet publish "${ConectorSolution}.csproj" -c Release-Kubernetes -o /app/publish

#Imagem final conector + agent conector
#variabel ambiente eh substituida pelo jenkins (nao foi possivel trabalhar com variavel no argumento FROM)
#FROM 830972547162.dkr.ecr.us-east-1.amazonaws.com/wevo/hubin-io-agent-connector-v3:beta-latest
FROM 830972547162.dkr.ecr.us-east-1.amazonaws.com/wevo/hubin-io-agent-connector-v3:{__ambiente__}-latest
WORKDIR /app/Connectors
#COPY --from=publish_conector /app/publish .
#WORKDIR /app
#ENTRYPOINT ["dotnet", "Wevo.IO.Agent.Connector.Runtime.API.dll"]
#WORKDIR /app/Connectors
#RUN pip install flask requests
#ENV TARGET_URL=""
#EXPOSE 9000
CMD ["dotnet"]
