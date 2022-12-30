GET-API usage
=====


Installation
++++++++++++

.. http:get:: /api/v3/projects/(string:project_slug)/

    Retrieve details of a single project.

    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl -H "Authorization: Token <token>" https://readthedocs.org/api/v3/projects/pip/

        .. code-tab:: python

            import requests
            URL = 'https://readthedocs.org/api/v3/projects/pip/'
            TOKEN = '<token>'
            HEADERS = {'Authorization': f'token {TOKEN}'}
            response = requests.get(URL, headers=HEADERS)
            print(response.json())

    **Example response**:

    .. sourcecode:: json

        {
            "id": 12345,
            "name": "Pip",
            "slug": "pip",
            "created": "2010-10-23T18:12:31+00:00",
            "modified": "2018-12-11T07:21:11+00:00",
            "language": {
                "code": "en",
                "name": "English"
            },
            "programming_language": {
                "code": "py",
                "name": "Python"
            },
            "repository": {
                "url": "https://github.com/pypa/pip",
                "type": "git"
            },
            "default_version": "stable",
            "default_branch": "master",
            "subproject_of": null,
            "translation_of": null,
            "urls": {
                "documentation": "http://pip.pypa.io/en/stable/",
                "home": "https://pip.pypa.io/"
            },
            "tags": [
                "distutils",
                "easy_install",
                "egg",
                "setuptools",
                "virtualenv"
            ],
            "users": [
                {
                    "username": "dstufft"
                }
            ],
            "active_versions": {
                "stable": "{VERSION}",
                "latest": "{VERSION}",
                "19.0.2": "{VERSION}"
            },
            "_links": {
                "_self": "/api/v3/projects/pip/",
                "versions": "/api/v3/projects/pip/versions/",
                "builds": "/api/v3/projects/pip/builds/",
                "subprojects": "/api/v3/projects/pip/subprojects/",
                "superproject": "/api/v3/projects/pip/superproject/",
                "redirects": "/api/v3/projects/pip/redirects/",
                "translations": "/api/v3/projects/pip/translations/"
            }
        }

    :query string expand: allows to add/expand some extra fields in the response.
                          Allowed values are ``active_versions``, ``active_versions.last_build`` and
                          ``active_versions.last_build.config``. Multiple fields can be passed separated by commas.

    .. note::

       .. FIXME: we can't use :query string: here because it doesn't render properly

      :doc:`Read the Docs for Business </commercial/index>`, also accepts

      :Query Parameters:

         * **expand** (*string*) -- with ``organization`` and ``teams``.
