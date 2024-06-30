#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["MALONES_PRE-FINALS_ASSIGNMENT-1/MALONES_PRE-FINALS_ASSIGNMENT-1.csproj", "MALONES_PRE-FINALS_ASSIGNMENT-1/"]
RUN dotnet restore "MALONES_PRE-FINALS_ASSIGNMENT-1/MALONES_PRE-FINALS_ASSIGNMENT-1.csproj"
COPY . .
WORKDIR "/src/MALONES_PRE-FINALS_ASSIGNMENT-1"
RUN dotnet build "MALONES_PRE-FINALS_ASSIGNMENT-1.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "MALONES_PRE-FINALS_ASSIGNMENT-1.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "MALONES_PRE-FINALS_ASSIGNMENT-1.dll"]