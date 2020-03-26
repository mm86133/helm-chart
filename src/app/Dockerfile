FROM mcr.microsoft.com/dotnet/core/sdk:3.1-alpine AS build-env
WORKDIR /app

# Copy everything else and bui
COPY . ./
RUN ls -la
#WORKDIR /app/app/
RUN ls -la

#RUN dotnet restore --configfile /app/Nuget.config
RUN dotnet publish -c Release -o /app/out
# Build runtime image
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-alpine
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "app.dll"]