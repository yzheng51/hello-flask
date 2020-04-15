# hello-flask

## Deployment

Use uuid module to generate secret key randomly

```python
>>> import uuid
>>> uuid.uuid4().hex
'3d6f45a5fc12445dbac2f59c3b6c7cb1'
```

Create a '.env' file to store environment variables

```sh
touch .env
```

Write secret key and database name to '.env'

```sh
SECRET_KEY=3d6f45a5fc12445dbac2f59c3b6c7cb1
DATABASE_FILE=data-prod.db
```

Initialisation

```sh
python -m venv venv              # Create virtual environment
. venv/bin/activate              # Activate virtual environment
pip install -r requirements.txt  # Install all depedencies
flask initdb                     # Initialise database
flask admin                      # Create admin account
```

Production deployment with gunicorn

```sh
pip install gunicorn
gunicorn -w 4 -b 127.0.0.1:4000 wsgi:app
```

## Run unit tests

```sh
python -m coverage run --omit=*/tests/*,*/venv/* tests/test_watchlist.py
```

Show report after `coverage run` command

```sh
coverage report
```
