# Django Project Template

This assumes your base system has `django-admin` available as a command to run.

If you don't have that available install it using `pip3 install django`.

Otherwise, running:

`django-admin startproject [project-name]`

Inside of the directory with the `Dockerfile` should create a new directory called `[project-name]. The project structure should look something like so:

```
root
├── Dockerfile
├── docker-compose.yml
├── manage.py
├── requirements.txt
└── [project-name] 
    └── ...
```

Remember to set the `settings.py` up correctly based on the database you want to have running, in this case our project uses

`PyMongo` as the database engine, which means we'll manually be using the client wherever needed. This means you need to comment out the `DATABASES` configuration in `settings.py`.

However if you want to use one of the built-in's (PostgreSQL, MariaDB, MySQL, Oracle, SQLite) you'd need to uncomment that block and add in the relevant DB connection information.
