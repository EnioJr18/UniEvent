# Backend — UniEvent

API do UniEvent desenvolvida com Django e Django REST Framework.

## Requisitos

- Python 3.12 ou superior
- `pip`
- ambiente virtual Python

> O PostgreSQL será configurado na Issue #2. A Issue #1 utiliza SQLite apenas como banco temporário de bootstrap para permitir validar o projeto Django antes da configuração do banco definitivo.

## Instalação

A partir da raiz do repositório:

### Linux/macOS

```bash
cd backend
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements/development.txt
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
py manage.py migrate
py manage.py runserver
```

O servidor de desenvolvimento ficará disponível em `http://127.0.0.1:8000/`.

## Settings

Por padrão, `manage.py`, ASGI e WSGI utilizam:

```text
config.settings.development
```

Os ambientes disponíveis são:

- `config.settings.base`: configuração comum;
- `config.settings.development`: desenvolvimento local;
- `config.settings.production`: produção.

Em produção, é obrigatório definir:

```text
DJANGO_SECRET_KEY
ALLOWED_HOSTS
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

O banco definitivo do UniEvent é PostgreSQL. A conexão será implementada na Issue #2.
