# Beauty Advisor - knowing the client!
# Matuy Unisex & SPA
- **Description**: 

  We are a company dedicated to the manufacture of perfumes for all genders and ages.
  Our goal is to collect data from our customers to predict future information about them via machine learning, in addition to knowing them better and understanding who consumes our brand.

- **Data Source**:

  Random fake data, created and manipulated by us

- **Type of analysis**:

  Marketing Inbound, Business model, Databases, Dashboards

**We have tried to document the project as best as possible, enjoy our Readme...**

# Startup the project

**Create a python3 virtualenv and activate it**:

```bash
mkdir backend-beautyAdvisor
cd backend-beautyAdvisor
# create new env
pyenv virtualenv beautyAdvisor
# activate new env
pyenv activate beautyAadvisor
# update pip
pip install --upgrade pip
```

## Git |Github Repository:  <img src="/Users/haroldinho/code/haroldo-oliveira/My_Projects/Enzyme_Academy/proyecto/img/git-vs-github.png" alt="git-vs-github" style="zoom:8%;" />

**Create a new repository on the command line**

Go to see the project, manage issues,
setup you ssh public key, ...

```bash
git init 
git add README.md 
git commit -m "first commit" 
git branch -M main 
```
**or Push an existing repository from the command line**

```bash
git remote add origin https://github.com/USERNAME/REPOSITORYNAME.git
git branch -M main
git push -u origin main
```

## Let's install Docker

The installation is fairly straightforward,  In order to use Docker you first need to install it. You can either **install Docker on a Desktop machine** (both Windows and Mac), or on a server (Linux based installations).

## psycopg2 :  <img src="/Users/haroldinho/code/haroldo-oliveira/My_Projects/Enzyme_Academy/proyecto/img/psycopg2.jpg" alt="psycopg2" style="zoom:10%;" />

**Installation**:

```bash
pip install psycopg2
```
## How to create a Postgres database:  <img src="/Users/haroldinho/code/haroldo-oliveira/My_Projects/Enzyme_Academy/proyecto/img/PostgreSQ.jpg" alt="PostgreSQ" style="zoom:25%;" />

```bash
docker run --name matui-db -it -e POSTGRES_PASSWORD=pass123 -p 5432:5432 -d postgres
```
**But what does it do?**

Last section of the command grabs the latest '**postgres**' Docker image from the Docker Hub

- **-d**: means that you enable Docker to run the container in the background

- **-p**: plus the port numbers means you map the containers port 5432 to the external port 5432 - this allows you to connect to it from the outside

- **-it**: run it interactively

- **POSTGRES_PASSWORD**: sets the password to docker. This is the password that gives you access to your database

- **—name**: property gives your container a name and means you can easily find it back

**Run docker compose**:

```bash
docker-compose up --build
```


Now you can connect to this brand new Postgres database in any tool that allows you to communicate with databases. I tend to use PgAdmin or DBeaver.

You need to use the following connection details to actually connect to the DB:

- Host: localhost
- Port: 5432
- User: postgres
- Password: pass123



**Create a python3 virtualenv and activate it**:

```bash
#create new env
pyenv virtualenv beautyAdvisor
# activate new env
pyenv activate beautyAadvisor
# update pip
pip install --upgrade pip
```

**Clone the project and install it**:

```bash
git clone git@github.com:{group}/backend-BeautyAdvisor.git
cd backend-BeautyAdvisor
pip install -r requirements.txt
```

# Used Libraries:

## fastapi:  <img src="/Users/haroldinho/code/haroldo-oliveira/My_Projects/Enzyme_Academy/proyecto/img/fastapi.png" alt="fastapi" style="zoom:28%;" />

FastAPI is a modern, fast (high-performance), web framework for building APIs with Python 3.7+ based on standard Python type hints.

**Documentation**: https://fastapi.tiangolo.com
**Source Code**: https://github.com/tiangolo/fastapi

**Installation**:

```bash
pip install fastapi
```
**Create a FastAPI "instance"**:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
async def root():
    return {"message": "Hello World"}
```

You will also need an ASGI server, for production, we choose **Uvicorn**

## uvicorn:   <img src="/Users/haroldinho/code/haroldo-oliveira/My_Projects/Enzyme_Academy/proyecto/img/uvicorn.png" alt="uvicorn" style="zoom:12%;" />

Uvicorn is an ASGI web server implementation for Python.

**Documentation**: https://www.uvicorn.org/
**Source Code**: https://github.com/encode/uvicorn

**Installation**:

This will install uvicorn with minimal (pure Python) dependencies.

```bash
pip install "uvicorn[standard]"
```
**Now Run it!**

**Run the live server with**:

```bash
uvicorn main:app --reload

INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
INFO:     Started reloader process [28720]
INFO:     Started server process [28722]
INFO:     Waiting for application startup.
INFO:     Application startup complete.

```
The command **uvicorn main:app** refers to:
-  **main**: the file main.py (the Python "module").
-  **app**: the object created inside of main.py with the line app = FastAPI().
-  **--reload**: make the server restart after code changes. Only do this for development.

In the output, there's a line with something like:

```bash
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
```
 **Check it!!!**

Open your browser at [http://127.0.0.1:8000](http://127.0.0.1:8000/).

**Interactive API docs**...

Now go to http://127.0.0.1:8000/docs.

<img src="/Users/haroldinho/Library/Application Support/typora-user-images/Captura de Pantalla 2022-09-30 a las 2.35.32.png" alt="Captura de Pantalla 2022-09-30 a las 2.35.32" style="zoom:40%;" />

## peewee:  <img src="/Users/haroldinho/code/haroldo-oliveira/My_Projects/Enzyme_Academy/proyecto/img/peewee3-logo.webp" alt="peewee3-logo" style="zoom:15%;" />

Peewee is a simple and small ORM (Object-Relational mapping). It has few (but expressive) concepts, making it easy to learn and intuitive to use.

**Documentation**: https://docs.peewee-orm.com/en/latest/index.html

**Source Code**: https://github.com/coleifer/peewee

- a small, expressive ORM
- python 2.7+ and 3.4+ (developed with 3.6)
- supports sqlite, mysql, postgresql and cockroachdb
- tons of extensions

```python
from peewee import *

db = PostgresqlDatabase('mydatabase', host='localhost', port=5432, user='postgres', password='postgres')
class MyUser (Model):
   name=TextField()
   city=TextField(constraints=[SQL("DEFAULT 'Mumbai'")])
   age=IntegerField()
   class Meta:
      database=db
      db_table='MyUser'

db.connect()
db.create_tables([MyUser])
```

## FastAPIwee : Optional!

## <img src="/Users/haroldinho/code/haroldo-oliveira/My_Projects/Enzyme_Academy/proyecto/img/fastapiwee.png" alt="fastapiwee" style="zoom:25%;" />


Made for FastAPI web framework and PeeWee ORM.

A fast and simple (I hope) way to create REST API based on PeeWee models.

**Documentation**: https://fastapiwee.qqmber.wtf/

**Source Code**: https://github.com/Ignisor/FastAPIwee/

**Requirements**:

-  Python 3.6+
-  FastAPI
-  Peewee

**Installation**:

```bash
pip install FastAPIwee
```

Define Peewee models in example.py:

```python
import peewee as pw

DB = pw.SqliteDatabase('/tmp/fastapiwee_example.db')


class TestModel(pw.Model):
    id = pw.AutoField()
    text = pw.TextField()
    number = pw.IntegerField(null=True)
    is_test = pw.BooleanField(default=True)

    class Meta:
        database = DB


class AnotherModel(pw.Model):
    id = pw.AutoField()
    text = pw.TextField(default='Cucumber')

    class Meta:
        database = DB
```



