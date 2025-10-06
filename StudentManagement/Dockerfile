# Stage 1: Build
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src

# Copy solution file & project(s)
COPY *.sln .
COPY StudentManagement/*.csproj StudentManagement/
# Nếu bạn có thêm project con, copy tương tự

# Restore dependencies
RUN dotnet restore

# Copy toàn bộ source
COPY . .

# Publish (sử dụng Release config)
WORKDIR /src/StudentManagement
RUN dotnet publish -c Release -o /app/publish

# Stage 2: Runtime
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS runtime
WORKDIR /app

# Copy output từ build stage
COPY --from=build /app/publish .

# Nếu bạn dùng biến PORT hoặc cần pass env, có thể đặt ENV ở đây

ENTRYPOINT ["dotnet", "StudentManagement.dll"]
