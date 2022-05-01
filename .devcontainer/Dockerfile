# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.231.6/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version (use hirsuite or bionic on local arm64/Apple Silicon): hirsute, focal, bionic
#ARG VARIANT="hirsute"
#FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

#FROM nginx:1.10.1-alpine
#COPY src/html /usr/share/nginx/html

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>


FROM node:16-alpine as builder
WORKDIR /app          
COPY package*.json .  
RUN npm ci
COPY . .
RUN ./node_modules/.bin/ng build --production  

FROM nginx:latest
COPY --from=builder /app/.devcontainer/Timed-Quiz-main /usr/share/nginx/html
#COPY ./nginx/nginx.conf /etc/nginx/conf.d/default.conf