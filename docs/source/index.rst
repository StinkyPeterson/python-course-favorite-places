Любимые места
=============

Service for saving favorite places.

Зависимости
===========

1. fastapi>=0.85.1,<0.86.0
2. fastapi-pagination>=0.10.0,<0.11.0
3. geocoder>=1.38.1,<1.39.0
4. uvicorn>=0.19.0,<0.20.0
5. sqlmodel>=0.0.8,<0.1.0
6. alembic>=1.8.1,<1.9.0
7. asyncpg>=0.26.0,<1.0.0
8. pika>=1.3.1,<1.4.0
9. httpx>=0.23.0,<0.24.0
10. pytest>=7.1.3,<7.2.0
11. pytest-cov>=4.0.0,<4.1.0
12. pytest-mock>=3.10.0,<3.11.0
13. pytest-httpx>=0.21.1,<0.22.0
14. pytest-asyncio>=0.20.1,<0.21.0
15. Sphinx>=5.3.0,<5.4.0
16. sphinx-rtd-theme>=1.0.0,<2.0.0
17. isort>=5.10.1,<5.11.0
18. flake8>=5.0.4,<5.1.0
19. pylint>=2.15.4,<2.16.0
20. mypy>=0.982,<1.0
21. black>=22.10.0,<22.11.0


Установка
=========

Install the appropriate software:

1. [Docker Desktop](https://www.docker.com).
2. [Git](https://github.com/git-guides/install-git).
3. [PyCharm](https://www.jetbrains.com/ru-ru/pycharm/download) (optional).

Использование
=============

    git clone https://github.com/StinkyPeterson/python-course-favorite-places.git
1. To configure the application copy `.env.sample` into `.env` file:

    .. code-block::console
        cp .env.sample .env
    This file contains environment variables that will share their values across the application.
    The sample file (`.env.sample`) contains a set of variables with default values.
    So it can be configured depending on the environment.

2. Build the container using Docker Compose:

    .. code-block::console
     docker compose build
    This command should be run from the root directory where `Dockerfile` is located.
    You also need to build the docker container again in case if you have updated `requirements.txt`.

3. To run application correctly set up the database.
   Apply migrations to create tables in the database:

    .. code-block::console
        docker compose run favorite-places-app alembic upgrade head
4. Now it is possible to run the project inside the Docker container:

    .. code-block::console
        docker compose up
   When containers are up server starts at [http://0.0.0.0:8010/docs](http://0.0.0.0:8010/docs). You can open it in your browser.



Работа с базой данных
---------------------

To first initialize migration functionality run:

    .. code-block::console
        docker compose exec favorite-places-app alembic init -t async migrations
This command will create a directory with configuration files to set up asynchronous migrations' functionality.

To create new migrations that will update database tables according updated models run this command:

    .. code-block::console
        docker compose run favorite-places-app alembic revision --autogenerate  -m "your description"
To apply created migrations run:

    .. code-block::console
        docker compose run favorite-places-app alembic upgrade head
Автоматизация
=============

The project contains a special `Makefile` that provides shortcuts for a set of commands:

1. Build the Docker container:

.. code-block::console
    make build
2. Generate Sphinx documentation run:

    .. code-block::console
        make docs-html
3. Autoformat source code:

    .. code-block::console
        make format
4. Static analysis (linters):

    .. code-block::console
        make lint
5. Autotests:

    .. code-block::console
        make test
    The test coverage report will be located at `src/htmlcov/index.html`.
    So you can estimate the quality of automated test coverage.

6. Run autoformat, linters and tests in one command:

    .. code-block::console
        make all
    Run these commands from the source directory where `Makefile` is located.

Тестирование
============

To run tests use the following command:

    .. code-block::console
        make all

Базовый
--------
.. automodule:: clients.base.base
    :members:

Geo
---
.. automodule:: clients.geo
    :members:

Schemas
-------
.. automodule:: clients.base.base
    :members:


Integrations
============

Database
--------
.. automodule:: integrations.db.session
    :members:

Events
------
.. automodule:: integrations.events.events
    :members:
.. automodule:: integrations.events.schemas
    :members:

Models
======
.. automodule:: models.mixins
    :members:
.. automodule:: models.places
    :members:

Repositories
============
.. automodule:: repositories.base_repository
    :members:
.. automodule:: repositories.places_repository
    :members:

Settings
========
.. automodule:: settings
    :members:

Schemas
=======
.. automodule:: schemas.base
    :members:
.. automodule:: schemas.places
    :members:
.. automodule:: schemas.routes
    :members:

Services
========
.. automodule:: services.places_service
    :members:

Transport
=========
.. automodule:: transport.handlers.places
    :members: