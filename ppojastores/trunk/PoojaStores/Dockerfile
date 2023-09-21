FROM mcr.microsoft.com/dotnet/sdk:3.1 as build
WORKDIR /app
COPY *.csproj ./
RUN dotnet restore
COPY . ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build /app/out .
EXPOSE 80
ENTRYPOINT ["dotnet" , "PoojaStores.dll"]


======================================================
# 2nd Way
FROM mcr.microsoft.com/dotnet/sdk:3.1 
WORKDIR /app/
COPY PoojaStores /app/
RUN dotnet build
RUN dotnet publish -c Release -o out
EXPOSE 5000
ENTRYPOINT ["dotnet", "run", "--urls", "http://0.0.0.0:5000"]
