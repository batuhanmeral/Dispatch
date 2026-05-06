# Kurulum ve Çalıştırma

## Gereksinimler

- Python 3.14+
- PostgreSQL
- WeasyPrint sistem bağımlılıkları (PDF export için)

Linux örneği:

```bash
sudo apt install libpango-1.0-0 libpangocairo-1.0-0 libgdk-pixbuf2.0-0 libffi-dev
```

## Kurulum

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## `.env` örneği

```env
SECRET_KEY=django-insecure-change-me
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1

DB_NAME=esms_db
DB_USER=postgres
DB_PASSWORD=postgres
CORS_ALLOWED_ORIGINS=http://localhost:3000
```

## Veritabanı

```bash
python manage.py migrate
python manage.py createsuperuser
```

## Uygulamayı çalıştırma

```bash
python manage.py runserver
```

## Demo veri (opsiyonel)

```bash
python manage.py seed_demo --reset
```

Varsayılan kullanıcılar:

- `admin / admin123` (ADMIN)
- Manager/Agent/Employee örnek kullanıcılar: `pass123`

## Kısa bakım komutları

```bash
python manage.py check
python -m compileall -q .
```
