django-inlinecss-redux
======================

.. image:: https://travis-ci.org/WhyNotHugo/django-inlinecss-redux.svg?branch=master
  :target: https://travis-ci.org/WhyNotHugo/django-inlinecss-redux
  :alt: Travis CI build status

About
-----

Inlining CSS is necessary for email generation and sending but is currently a
surprisingly large hassle.

This library aims to make it a breeze in the Django template language.

This library is a fork of ``django-inlinecss``, which doesn't seem to have any
activity or maintained any more. We'd gladly merge back any changes if it
revives.

Usage
-----

Step 1: Dependencies
~~~~~~~~~~~~~~~~~~~~

- BeautifulSoup
- cssutils
- Python 2.7+,3.4+
- Django 1.6+


Step 2: Install django_inlinecss-redux
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Add ``django_inlinecss`` to your ``settings.py``:

.. code-block:: python

    INSTALLED_APPS = (
        'django.contrib.auth',
        'django.contrib.webdesign',
        'django.contrib.contenttypes',
        '...',
        '...',
        '...',
        'django_inlinecss',
    )

Step 3: Use the templatetag
~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Place your CSS file somewhere staticfiles can find it
2. Create your template:

.. code-block:: html

    {% load inlinecss %}
    {% inlinecss "css/extra-padding.css" %}
        <html>
            <body>
                <div class='lots-o-padding'>
                    Something in need of styling.
                </div>
            </body>
        </html>
    {% endinlinecss %}

Step 4: Prepare to be Wowed
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: html

    <html>
        <body>
            <div style="padding-left: 10px; padding-right: 10px; padding-top: 10px;" class="lots-o-padding">
                Something in need of styling.
            </div>
        </body>
    </html>

Acknowledgements
----------------

Thanks to Tanner Netterville for his efforts on [Pynliner](https://github.com/rennat/pynliner).

Thanks to Thomas Yip for his unit tests on the `soupselect` module. These tests
helped on getting the core CSS2 selectors to work.

License
-------

MIT license. See LICENSE.md for more detail.
