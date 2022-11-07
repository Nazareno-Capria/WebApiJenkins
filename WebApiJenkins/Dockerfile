FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /WebApi
ENV ASPNETCORE_URLS http://+:45159
EXPOSE 45159

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ./*.csproj ./
RUN dotnet restore
COPY . .
RUN dotnet publish -c Release -o out

FROM base AS final
WORKDIR /WebApi
COPY --from=build /src/out .
ENTRYPOINT ["dotnet", "./WebApiJenkins.dll"]