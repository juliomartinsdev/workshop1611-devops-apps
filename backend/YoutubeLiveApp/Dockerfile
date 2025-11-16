FROM --platform=$BUILDPLATFORM mcr.microsoft.com/dotnet/sdk:7.0-alpine AS builder
ARG TARGETARCH
WORKDIR /youtube-live-app
COPY . .
ENV ASPNETCORE_ENVIRONMENT Development
ENV URLS http://0.0.0.0:80
RUN dotnet publish -a $TARGETARCH -c Release -o build /youtube-live-app/YoutubeLiveApp.csproj

FROM mcr.microsoft.com/dotnet/aspnet:7.0-alpine AS runner
WORKDIR /youtube-live-app
COPY --from=builder /youtube-live-app/build /youtube-live-app/
EXPOSE 80
ENTRYPOINT ["dotnet", "/youtube-live-app/YoutubeLiveApp.dll"] 