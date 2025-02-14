.. SPDX-FileCopyrightText: 2021 Veit Schiele
..
.. SPDX-License-Identifier: BSD-3-Clause

Installation
============

Anforderungen
-------------

.. code-block:: console

    $ pipenv install fastapi
    Adding fastapi to Pipfile's [packages]…
    ✔ Installation Succeeded
    Locking [dev-packages] dependencies…
    ✔ Success!
    Locking [packages] dependencies…
    ✔ Success!
    …

Optionale Anforderungen
~~~~~~~~~~~~~~~~~~~~~~~

Für die Produktion benötigt ihr außerdem einen `ASGI
<https://asgi.readthedocs.io/en/latest/>`_-Server wie `uvicorn
<http://www.uvicorn.org/>`_:

.. code-block:: console

    $ pipenv install uvicorn
    Adding uvicorn to Pipfile's [packages]…
    ✔ Installation Succeeded
    Locking [dev-packages] dependencies…
    ✔ Success!
    Locking [packages] dependencies…
    ✔ Success!
    Updated Pipfile.lock (051f02)!
    …

Pydantic kann die folgenden optionalen Abhängigkeiten verwenden:

`ujson <https://github.com/ultrajson/ultrajson>`_
    für schnelleres JSON-Parsing.
`email_validator <https://github.com/JoshData/python-email-validator>`_
    zur E-Mail-Validierung.

Starlette kann die folgenden optionalen Abhängigkeiten verwenden:

:doc:`requests <../../requests/index>`
    wenn ihr den ``TestClient`` verwenden wollt.
`aiofiles <https://github.com/Tinche/aiofiles>`_
    wenn ihr ``FileResponse`` oder ``StaticFiles`` verwenden wollt.
`jinja2 <https://jinja.palletsprojects.com/>`_
    wenn ihr die Standard-Template-Konfiguration verwenden wollt.
`python-multipart <https://andrew-d.github.io/python-multipart/>`_
    wenn ihr das Parsen von Formularen mit ``request.form()`` unterstützen
    wollt.
`itsdangerous <https://itsdangerous.palletsprojects.com/>`_
    erforderlich für die Unterstützung von ``SessionMiddleware``.
`pyyaml <https://pyyaml.org/wiki/PyYAMLDocumentation>`_
    für die Unterstützung von Starlette’s ``SchemaGenerator``.
`graphene <https://graphene-python.org/>`_
    für die Unterstützung von ``GraphQLApp``.
`ujson <https://github.com/ultrajson/ultrajson>`__
    wenn ihr ``UJSONResponse`` verwenden wollt.
`orjson <https://github.com/ijl/orjson>`_
    wenn ihr ``ORJSONResponse`` verwenden wollt.

Sie können installiert werden, z.B. mit:

.. code-block:: console

    $ pipenv install fastapi[ujson]

Alternativ könnt ihr alle installieren mit:

.. code-block:: console

    $ pipenv install fastapi[all]
