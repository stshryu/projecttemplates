# FastAPI Project Template

First, there are better generic templates for FastAPI: [You can find them here.](https://github.com/tiangolo/full-stack-fastapi-template)

However this project template is more specific to using React, Mongo and Redis.

## Project Structure

```root
├── client/
│   ├── frontendDockerfile
│   ├── ...
├── server/
│   ├── fastapiDockerfile
│   ├── requirements.txt
│   ├── ...
├── docker-compose.yml
└── README.md
```

The frontend engine can be created with whatever you want, in this template we're using React.

## Frontend Setup

`npm install -g create-react-app`

`npx create-react-app client --template typescript`

Installs, and creates a directory called `client/` in the root which you should move, and rename the `frontendDockerfile` -> `Dockerfile` into. Remember, if you want to you can change the `client/` directory or app name to anything you want, just fix the references in `docker-compose.yml`.

## FastAPI Setup

There isn't a built-in command to start a FastAPI server, it's lightweight enough that you can just start with a basic `main.py` and work from there.

Keep in mind that the `fastapiDockerfile` has a command in it that specifies `[ ..., "main:app", ... ]`. This refers to the file `main.py` and the FastAPI application definition `app = FastAPI()` in order to run the project successfully. If you want to change the name, or change the export remember to change it in the `Dockerfile` as well.

The `requirements.txt` file should also exist on the same level as the `fastapiDockerfile` wherever you put it.

## Run 

`docker-compose up --build` 

Is sufficient for running the project. This `compose` however also uses profiles, which means when you run the above command, the only services that will spin up are `MongoDB` and `Redis`.

In order to get the backend up and running you have to add to the command:

`docker-compose --profile server up --build`

If you want to run both frontend, backend and all the requisite services you can specify it like so:

`docker-compose --profile dev up --build`
