FROM mcr.microsoft.com/dotnet/core/sdk:3.1-bionic as build-env

WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o netcore_prom

##

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-bionic

WORKDIR /app

COPY --from=build-env /app/netcore_prom ./

EXPOSE 80

ENTRYPOINT ["dotnet", "Werter.Monitoramento.Api.dll"]