FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build-env
WORKDIR /app

COPY *.csproj .
#COPY . ./
RUN dotnet restore

COPY . ./

#ENV ASPNETCORE_URLS=http://*:1000

RUN dotnet publish -c Relase -o out

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet","Test.Api.dll"]



