FROM mcr.microsoft.com/dotnet/sdk:10.0

EXPOSE 5100

ARG API_NAME=my-api
ARG GIT_USER='John Doe'
ARG GIT_EMAIL='john.doe@test.be'

WORKDIR /app

RUN dotnet new solution -o . -n ${API_NAME}
RUN dotnet new webapi -controllers --no-https -o ${API_NAME}
RUN dotnet new classlib -o ${API_NAME}.Domain
RUN dotnet sln add ./${API_NAME}
RUN dotnet sln add ./${API_NAME}.Domain
RUN dotnet add reference --project ./${API_NAME} ./${API_NAME}.Domain

COPY ./launchSettings.json ./${API_NAME}/Properties

WORKDIR /app/${API_NAME}

CMD ["dotnet", "watch"]


