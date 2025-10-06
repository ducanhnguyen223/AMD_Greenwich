FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src

# COPY project file(s)
COPY *.csproj .   # vì Dockerfile đã ở folder StudentManagement, nên *.csproj ở đây
RUN dotnet restore

# Copy toàn bộ code
COPY . .

# Publish
RUN dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "StudentManagement.dll"]
