# ===== BUILD STAGE =====
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Copy toàn bộ project (vì Dockerfile nằm cùng cấp với .csproj)
COPY . ./

RUN dotnet restore
RUN dotnet publish -c Release -o out

# ===== RUNTIME STAGE =====
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "StudentManagement.dll"]
