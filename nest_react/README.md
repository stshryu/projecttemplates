# React & NestJS template

This template requires at the least `npm` and `npx` to be available on your machine. Install using `brew` or whatever package manager you'd like to get node.

Project structure should look like this:

```
root
├── client/
│   ├── Dockerfile
│   ├── ... 
├── server/
│   ├── Dockerfile 
│   ├── ... 
├── docker-compose.yml
└── README.md
```

There are two `Dockerfile`s that exist in this template, both should exist within their own folders called `client/` and `server/`. Move them, and rename them to `Dockerfile` or create your own inside of those directories.

You can find the project structure in `docker-compose.yml`, as it defines the context for the frontend as `client/` and the context for the backend to be `server/`.

## Client Setup 

`npm install -g create-react-app`

`npx create-react-app client --template typescript`

Normally, we'd use a dynamic application name, but in this case setting `client` as the project name allows us to align it properly with what `compose` is expecting when we spin up the instance.

## Server Setup

`npm install -g @nestjs.cli`

`nest new server`

Again, we could use a different name, just make sure to change it in the related `Dockerfile` and within `docker-compose.yml`.

## Run 

`docker-compose up --build`

Should run both containers, compose will also spin up `MongoDB` and `Redis` as containers as well which will be available for either service to access. If you want to add profiles you can do so, they aren't included in this project but are useful for spinning up select services.

`docker-compose --profile frontend up --build`

For example could be used to ONLY spin up the React frontend.
