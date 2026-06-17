FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
# Копіюємо тільки файл проекту, щоб відновити залежності
COPY ["ApiWrapper.csproj", "./"]
RUN dotnet restore "ApiWrapper.csproj"

# Копіюємо решту коду
COPY . .
RUN dotnet publish "ApiWrapper.csproj" -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "ApiWrapper.dll"]