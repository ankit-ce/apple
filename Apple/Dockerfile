#Get base image from Microsoft
#FROM mcr.microsoft.com/dotnet/core/aspnet:2.1 AS base
#WORKDIR /app
#EXPOSE 80
#EXPOSE 1938

#FROM mcr.microsoft.com/dotnet/core/sdk:2.1 AS build
#WORKDIR /src
#COPY Apple/Apple.csproj Apple/
#RUN dotnet restore Apple/Apple.csproj
#COPY . .
#WORKDIR /src/Apple
#RUN dotnet build Apple.csproj -c Release -o /app



#FROM build AS publish
#RUN dotnet publish Apple.csproj -c Release -o /app

#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app .
#ENTRYPOINT ["dotnet", "Apple.dll"]

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish Apple.csproj -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "Apple.dll"]