FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env
WORKDIR /YogurtTheCommunity

COPY . ./
RUN dotnet restore YogurtTheCommunity.csproj
RUN dotnet build YogurtTheCommunity.csproj -c Release -o build
RUN dotnet publish YogurtTheCommunity.csproj -c Release -o out /p:UseAppHost=false

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /YogurtTheCommunity
COPY --from=build-env /YogurtTheCommunity/out .
ENTRYPOINT ["dotnet", "YogurtTheCommunity.dll"]
