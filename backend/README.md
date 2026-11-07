# Backend — UniEvent

API do UniEvent desenvolvida com Django e Django REST Framework.

## Requisitos

- Python 3.12 ou superior
- `pip`
- ambiente virtual Python
- acesso ao projeto UniEvent no Neon

## Banco de dados — Neon PostgreSQL

O PostgreSQL do UniEvent é hospedado no Neon.

Cada integrante deve usar a connection string disponibilizada no Neon Console e armazená-la **somente** em `backend/.env`.

### 1. Obter a connection string

No Neon Console:

```text
Project UniEvent
→ Connect
→ Connection string
→ Pooled connection
```

Para a aplicação Django, prefira a URL **pooled**.

Ela terá formato semelhante a:

```text
postgresql://USER:PASSWORD@HOST-pooler.REGION.aws.neon.tech/DATABASE?sslmode=require
```

> Nunca envie a URL real para o GitHub, Issues, Pull Requests ou documentação.

### 2. Criar o arquivo local de ambiente

Linux/macOS:

```bash
cd backend
cp .env.example .env
```

Windows PowerShell:

```powershell
cd backend
Copy-Item .env.example .env
```

Depois substitua apenas o valor de `DATABASE_URL` pela connection string real do Neon.

## Instalação

### Linux/macOS

```bash
cd backend
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements/development.txt
cp .env.example .env
# Edite DATABASE_URL no .env
python manage.py check
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
# Edite DATABASE_URL no .env
py manage.py check
py manage.py migrate
py manage.py runserver
```

O servidor ficará disponível em `http://127.0.0.1:8000/`.

## Variáveis de ambiente

```text
DJANGO_SECRET_KEY
DEBUG
ALLOWED_HOSTS
DATABASE_URL
DATABASE_CONN_MAX_AGE
```

O arquivo `.env` é ignorado pelo Git. Apenas `.env.example` é versionado.

## Settings

Por padrão, `manage.py`, ASGI e WSGI utilizam:

```text
config.settings.development
```

Os ambientes disponíveis são:

- `config.settings.base`;
- `config.settings.development`;
- `config.settings.production`.

## Apps preparados

- `accounts`
- `events`
- `registrations`
- `attendance`
- `certificates`

## Estrutura comum

`common/` contém pontos compartilhados para exceções, permissões, paginação, services e utilitários.

## Validando a conexão

Com o `.env` configurado:

```bash
python manage.py check
python manage.py migrate
```

Se ambos concluírem sem erros, o Django está conectado ao Neon corretamente.

## Autenticação

O projeto continuará utilizando autenticação implementada no Django. **Neon Auth não é necessário para o UniEvent neste momento.**
