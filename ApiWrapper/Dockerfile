FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Копіюємо всі файли проекту, щоб Docker бачив структуру рішення
COPY . .

# Відновлюємо залежності для вашого API
RUN dotnet restore "ApiWrapper/ApiWrapper.csproj"

# Збираємо API
RUN dotnet publish "ApiWrapper/ApiWrapper.csproj" -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "ApiWrapper.dll"]