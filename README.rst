
.. image:: https://raw.githubusercontent.com/Nekmo/telegram-upload/master/logo.png
    :width: 100%

|


.. image:: https://img.shields.io/github/workflow/status/Nekmo/telegram-upload/Tests.svg?style=flat-square&maxAge=2592000
  :target: https://github.com/Nekmo/telegram-upload/actions?query=workflow%3ATests
  :alt: Latest Tests CI build status

.. image:: https://img.shields.io/pypi/v/telegram-upload.svg?style=flat-square
  :target: https://pypi.org/project/telegram-upload/
  :alt: Latest PyPI version

.. image:: https://img.shields.io/pypi/pyversions/telegram-upload.svg?style=flat-square
  :target: https://pypi.org/project/telegram-upload/
  :alt: Python versions

.. image:: https://img.shields.io/codeclimate/maintainability/Nekmo/telegram-upload.svg?style=flat-square
  :target: https://codeclimate.com/github/Nekmo/telegram-upload
  :alt: Code Climate

.. image:: https://img.shields.io/codecov/c/github/Nekmo/telegram-upload/master.svg?style=flat-square
  :target: https://codecov.io/github/Nekmo/telegram-upload
  :alt: Test coverage

.. image:: https://img.shields.io/requires/github/Nekmo/telegram-upload.svg?style=flat-square
     :target: https://requires.io/github/Nekmo/telegram-upload/requirements/?branch=master
     :alt: Requirements Status


###############
telegram-upload
###############
Telegram-upload uses your personal Telegram account to upload and download files up to 2GiB (bots are limited to 50
MiB). Turn Telegram into your personal cloud!

To **install telegram-upload**, run this command in your terminal:

.. code-block:: console

    $ sudo pip3 install -U telegram-upload

This is the preferred method to install telegram-upload, as it will always install the most recent stable release.
`More info in the documentation <https://docs.nekmo.org/telegram-upload/installation.html>`_


To use this program you need an Telegram account and your *App api_id/api_hash* (get it in
`my.telegram.org <https://my.telegram.org/>`_). The first time you use telegram-upload it requests your telephone,
api_id and api_hash. Bot tokens can not be used with this program (bot uploads are limited to 50MB). To **send files**
(by default it is uploaded to saved messages):

.. code-block:: console

    $ telegram-upload file1.mp4 /path/to/file2.mkv

Credentials are saved in ``~/.config/telegram-upload.json`` and ``~/.config/telegram-upload.session``. You must make
sure that these files are secured. You can copy these files to authenticate ``telegram-upload`` on more machines, but
it is advisable to create a session file for each machine. Upload options are available
`in the documentation <https://docs.nekmo.org/telegram-upload/usage.html#telegram-upload>`_.


You can **download the files** again from your saved messages (by default) or from a channel. All files will be
downloaded until the last text message.

.. code-block:: console

    $ telegram-download

The ``--delete-on-success`` option allows you to delete the Telegram message after downloading the file. This is
useful to send files to download to your saved messages and avoid downloading them again. You can use this option to
download files on your computer away from home.

`Read the documentation <https://docs.nekmo.org/telegram-upload/usage.html#telegram-download>`_ for more info.


Interactive mode
================
The **interactive option** (``--interactive``) allows you to choose the dialog and the files to download or upload with
a **terminal wizard**. It even **supports mouse**!

.. code-block:: console

    $ telegram-upload --interactive    # Interactive upload
    $ telegram-download --interactive  # Interactive download



Features
========

* Upload multiples files (up to 2GiB per file)
* Download files.
* Add video thumbs.
* Delete local or remote file on success.
* File name, path in caption

Docker
======
Run telegram-upload without installing it on your system using Docker. Instead of ``telegram-upload``
and ``telegram-download`` you should use ``upload`` and ``download``. Usage::


    docker run -v <files_dir>:/files/
               -v <config_dir>:/config
               -it nekmo/telegram-upload:master
               <command> <args>

* ``<files_dir>``: upload or download directory.
* ``<config_dir>``: Directory that will be created to store the telegram-upload configuration.
  It is created automatically.
* ``<command>``: ``upload`` and ``download``.
* ``<args>``: ``telegram-upload`` and ``telegram-download`` arguments.

For example::

    docker run -v /media/data/:/files/
               -v $PWD/config:/config
               -it nekmo/telegram-upload:master
               upload file_to_upload.txt


