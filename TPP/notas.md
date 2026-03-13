
# Extra dependencies

## Backend

### Enviroment

    python3 -m 
    source .venv/bin/activate
    pip3 install -r requirements.txt

### Basics

    sudo apt install python3 python3-venv python3-pip libpq-dev python3-dev cmake

### PostgreSQL (alternativa a Docker)

    sudo apt install -y postgresql postgresql-contrib

Inside postgres=#:

    CREATE ROLE ludo WITH LOGIN PASSWORD 'ludo';
    ALTER ROLE ludo CREATEDB;
    CREATE DATABASE ludo OWNER ludo;

Checks:

    psql -U ludo -d ludo -h localhost -W

## Front

### Java

    sudo apt install openjdk-17-jdk
    sudo update-alternatives --config java

Seleccionar Java 17.0
