FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY . .
# Тепер він точно знайде шлях, бо API лежить у підпапці, а Dockerfile в корені
RUN dotnet publish "ApiWrapper/ApiWrapper.csproj" -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "ApiWrapper.dll"]