# Stage build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copy solution và project file(s)
COPY *.sln .
COPY StudentManagement/*.csproj StudentManagement/
RUN dotnet restore

# Copy toàn bộ source vào
COPY . .

WORKDIR /src/StudentManagement
RUN dotnet publish -c Release -o /app/publish

# Stage runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .

# Nếu muốn expose port (theo .NET 8 mặc định là 8080)
ENV ASPNETCORE_URLS=http://+:8080

ENTRYPOINT ["dotnet", "StudentManagement.dll"]
