# Build stage
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copy project file(s) từ thư mục này
COPY *.csproj .      # vì Dockerfile đang trong folder chứa .csproj
RUN dotnet restore

# Copy toàn bộ code
COPY . .  
RUN dotnet publish -c Release -o /app/publish

# Runtime stage
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "StudentManagement.dll"]
