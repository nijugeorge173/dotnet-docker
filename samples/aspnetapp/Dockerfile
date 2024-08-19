# Learn about building .NET container images:
# https://github.com/dotnet/dotnet-docker/blob/main/samples/README.md

FROM mcr.microsoft.com/dotnet/aspnet:8.0

ADD aspnetapp/newrelic-dotnet-agent_amd64.tar.gz /app

COPY build/. /app

EXPOSE 8080

# Enable the agent
ENV CORECLR_ENABLE_PROFILING=1 \
CORECLR_PROFILER={36032161-FFC0-4B61-B559-F6C5D41BAE5A} \
#CORECLR_NEWRELIC_HOME=/usr/local/newrelic-dotnet-agent \
#CORECLR_PROFILER_PATH=/usr/local/newrelic-dotnet-agent/libNewRelicProfiler.so \
CORECLR_NEWRELIC_HOME=/app/newrelic-dotnet-agent \
CORECLR_PROFILER_PATH=/app/newrelic-dotnet-agent/libNewRelicProfiler.so \
NEW_RELIC_LICENSE_KEY=eu01xx2fca99a6cabde4af2e29a8919bFFFFNRAL \
NEW_RELIC_APP_NAME=DOTNET-GZ \
NEW_RELIC_LOG=MyApp.log \
NEW_RELIC_LOG_ENABLED=true \
NEWRELIC_LOG_LEVEL=info \
NEW_RELIC_LOG_CONSOLE=true \
NEWRELIC_PROFILER_LOG_DIRECTORY=/var/log \
NEWRELIC_LOG_DIRECTORY=/var/log 

WORKDIR /app
ENTRYPOINT ["./aspnetapp"]
