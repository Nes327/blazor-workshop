FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build

WORKDIR /app

COPY ./src/BlazingPizza.sln ./
COPY ./src/BlazingPizza.Client ./BlazingPizza.Client
COPY ./src/BlazingPizza.ComponentsLibrary ./BlazingPizza.ComponentsLibrary
COPY ./src/BlazingPizza.Server ./BlazingPizza.Server
COPY ./src/BlazingPizza.Shared ./BlazingPizza.Shared

RUN dotnet restore ./BlazingPizza.Server/BlazingPizza.Server.csproj

RUN dotnet publish ./BlazingPizza.Server/BlazingPizza.Server.csproj -c Release -o /publish

FROM mcr.microsoft.com/dotnet/aspnet:7.0

WORKDIR /app

COPY --from=build /publish .

ENTRYPOINT ["dotnet", "BlazingPizza.Server.dll"]
