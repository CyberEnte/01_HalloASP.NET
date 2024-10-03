# Stage 1: Build the application
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env
WORKDIR /App

# Copy the content of 01_HalloASP.NET folder
COPY ./01_HalloASP.NET/ ./

# Restore as distinct layers
RUN dotnet restore
# Build and publish a release
RUN dotnet publish -c Release -o out

# Stage 2: Run the application
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /App

# Copy the published output from the build-env
COPY --from=build-env /App/out .

# Run the application
ENTRYPOINT ["dotnet", "01_HalloASP.NET.dll"]