#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 80
ENV ASPNETCORE_URLS=http://+:80

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
ARG BUILD_CONFIGURATION=Release
WORKDIR /src
COPY . .
RUN dotnet restore
RUN dotnet publish -c $BUILD_CONFIGURATION -o /app

FROM base AS final
WORKDIR /app
COPY --from=build /app/ .
ENTRYPOINT ["dotnet", "HelloWorldApp.dll"]