test:
	docker-compose run --rm app sh -c "python manage.py test --noinput"

user:
	docker-compose run --rm app sh -c "python manage.py createsuperuser"

migrations:
	docker-compose run --rm app sh -c "python manage.py makemigrations"

migrate:
	docker-compose run --rm app sh -c "python manage.py migrate"

format:
	brunette ../app --config=setup.cfg

dev:
	git checkout dev
	git pull origin dev
	pip install -r ../etc/requirements.txt
	docker-compose run --rm app sh -c "python manage.py migrate"

check:
	python manage.py makemigrations --dry-run --check
	python manage.py test --noinput
	brunette ../app --check --diff --config=setup.cfg

ilocal:
	pip install -r ../etc/requirements.txt

init:
	make ilocal
	cp ../.env.sample ./app/core/.env
	cp ../.env.sample ./.env
