# Backend — UniEvent

API do UniEvent desenvolvida com Django e Django REST Framework.

## Requisitos

- Python 3.12 ou superior
- PostgreSQL
- `pip`
- ambiente virtual Python

## Instalação

A partir da raiz do repositório:

### Linux/macOS

```bash
cd backend
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements/development.txt
cp .env.example .env
python manage.py migrate
python manage.py runserver
```

### Windows PowerShell

```powershell
cd backend
py -m venv .venv
.\.venv\Scripts\Activate.ps1
py -m pip install --upgrade pip
pip install -r requirements/development.txt
Copy-Item .env.example .env
py manage.py migrate
py manage.py runserver
```

O servidor de desenvolvimento ficará disponível em `http://127.0.0.1:8000/`.

## PostgreSQL

Crie um banco local para o projeto antes de rodar as migrations.

Exemplo no `psql`:

```sql
CREATE DATABASE unievent;
```

Depois ajuste o arquivo `.env` conforme seu ambiente:

```env
DATABASE_NAME=unievent
DATABASE_USER=postgres
DATABASE_PASSWORD=postgres
DATABASE_HOST=localhost
DATABASE_PORT=5432
DATABASE_CONN_MAX_AGE=60
```

O arquivo `.env` é local e não deve ser commitado. O repositório mantém apenas `.env.example`.

## Settings

Por padrão, `manage.py`, ASGI e WSGI utilizam:

```text
config.settings.development
```

Os ambientes disponíveis são:

- `config.settings.base`: configuração comum;
- `config.settings.development`: desenvolvimento local;
- `config.settings.production`: produção.

Em produção, é obrigatório definir pelo menos:

```text
DJANGO_SECRET_KEY
ALLOWED_HOSTS
DATABASE_NAME
DATABASE_USER
DATABASE_PASSWORD
DATABASE_HOST
DATABASE_PORT
```

## Apps preparados

- `accounts`
- `events`
- `registrations`
- `attendance`
- `certificates`

Os models, services e endpoints de cada domínio serão implementados nas Issues específicas.

## Estrutura comum

`common/` contém pontos compartilhados para:

- exceções;
- permissões;
- paginação;
- services utilitários;
- funções gerais.

## Banco de dados

O banco definitivo do UniEvent é PostgreSQL, acessado pelo driver Psycopg 3.

Para validar a configuração:

```bash
python manage.py check
python manage.py migrate
```
