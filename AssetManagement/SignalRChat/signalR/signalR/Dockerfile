FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /app

COPY signalR.csproj .
RUN dotnet restore signalR.csproj

COPY . .
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS runtime
WORKDIR /app
COPY --from=build /app/out ./

ENTRYPOINT ["dotnet", "signalR.dll"]