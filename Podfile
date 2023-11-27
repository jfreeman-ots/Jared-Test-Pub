# Use the official ASP.NET Core runtime image as a base image
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app
EXPOSE 80

# Use the official ASP.NET Core SDK image to build the application
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src

# Copy the project files to the container
COPY . .

# Publish the application
RUN dotnet publish -c Release -o /app

# Build the final image with the runtime image and the published application
FROM base AS final
WORKDIR /app
COPY --from=build /app .

# Specify the entry point for the container
ENTRYPOINT ["dotnet", "TodoApp01.dll"]
