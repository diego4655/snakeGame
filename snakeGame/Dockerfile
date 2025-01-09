FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR snakeGame

EXPOSE 80
EXPOSE 5000


#COPY PROJECT FILES
COPY ./*.csproj ./
RUN dotnet restore


#COPY EVERYTHING ELSE
COPY . .
RUN dotnet publish -c Release -o out


#BUILD IMAGE
FROM mcr.microsoft.com/dotnet/sdk:8.0
WORKDIR /snakeGame
COPY --from=build /snakeGame/out .
ENTRYPOINT ["dotnet", "snakeGame.dll"]



