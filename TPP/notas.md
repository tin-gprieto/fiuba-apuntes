
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

### Docker

Create a super user

docker exec -it web python3 manage.py createsuperuser --email admin.martin@ludo.com --dni 42817479 --is_student True --is_teacher True

Create a student user

docker exec -it web python3 manage.py shell -c "from backend.models import User, Student; \
user = User.objects.create_user(dni='42817479', email='martin@ludo.com', password='ludo1234', is_student=True, is_teacher=False, first_name='Martín', last_name='GP'); \
Student.objects.create(user=user, padron='105738', inscripto=True, image=None)"

## Front

### Java

    sudo apt install openjdk-17-jdk
    sudo update-alternatives --config java

Seleccionar Java 17.0
