.. This file contains a series of comments that are used to include sections of this README in other files. Do not modify these comments unless you know what you are doing. tag:intro-begin

Intall certbot on AWS Linux2
-----------------------------
```
# configure Nginx, and setup 80 port
sudo yum install python27-devel git
sudo git clone https://github.com/BigMurry/certbot.git /opt/letsencrypt
sudo /opt/letsencrypt/letsencrypt-auto --debug

# stop nginx service
sudo /opt/letsencrypt/certbot-auto certonly --standalone -d relay.udap.io

# edit nginx.conf and modify cert part
sudo service nginx restart
```

Credits to:
1. [Gifford Nowland](https://medium.com/@gnowland/deploying-lets-encrypt-on-an-amazon-linux-ami-ec2-instance-f8e2e8f4fc1f)
2. [Andre Nakkurt](https://medium.com/@andrenakkurt/great-guide-thanks-for-putting-this-together-gifford-nowland-c3ce0ea2455)

Original README
--------------------
Certbot is part of EFF’s effort to encrypt the entire Internet. Secure communication over the Web relies on HTTPS, which requires the use of a digital certificate that lets browsers verify the identity of web servers (e.g., is that really google.com?). Web servers obtain their certificates from trusted third parties called certificate authorities (CAs). Certbot is an easy-to-use client that fetches a certificate from Let’s Encrypt—an open certificate authority launched by the EFF, Mozilla, and others—and deploys it to a web server.

Anyone who has gone through the trouble of setting up a secure website knows what a hassle getting and maintaining a certificate is. Certbot and Let’s Encrypt can automate away the pain and let you turn on and manage HTTPS with simple commands. Using Certbot and Let's Encrypt is free, so there’s no need to arrange payment.

How you use Certbot depends on the configuration of your web server. The best way to get started is to use our `interactive guide <https://certbot.eff.org>`_. It generates instructions based on your configuration settings. In most cases, you’ll need `root or administrator access <https://certbot.eff.org/faq/#does-certbot-require-root-administrator-privileges>`_ to your web server to run Certbot.

Certbot is meant to be run directly on your web server, not on your personal computer. If you’re using a hosted service and don’t have direct access to your web server, you might not be able to use Certbot. Check with your hosting provider for documentation about uploading certificates or using certificates issued by Let’s Encrypt.

Certbot is a fully-featured, extensible client for the Let's
Encrypt CA (or any other CA that speaks the `ACME
<https://github.com/ietf-wg-acme/acme/blob/master/draft-ietf-acme-acme.md>`_
protocol) that can automate the tasks of obtaining certificates and
configuring webservers to use them. This client runs on Unix-based operating
systems.

To see the changes made to Certbot between versions please refer to our
`changelog <https://github.com/certbot/certbot/blob/master/CHANGELOG.md>`_.

Until May 2016, Certbot was named simply ``letsencrypt`` or ``letsencrypt-auto``,
depending on install method. Instructions on the Internet, and some pieces of the
software, may still refer to this older name.

Contributing
------------

If you'd like to contribute to this project please read `Developer Guide
<https://certbot.eff.org/docs/contributing.html>`_.

This project is governed by `EFF's Public Projects Code of Conduct <https://www.eff.org/pages/eppcode>`_.

.. _installation:

How to run the client
---------------------

The easiest way to install and run Certbot is by visiting `certbot.eff.org`_,
where you can find the correct instructions for many web server and OS
combinations.  For more information, see `Get Certbot
<https://certbot.eff.org/docs/install.html>`_.

.. _certbot.eff.org: https://certbot.eff.org/

Understanding the client in more depth
--------------------------------------

To understand what the client is doing in detail, it's important to
understand the way it uses plugins.  Please see the `explanation of
plugins <https://certbot.eff.org/docs/using.html#plugins>`_ in
the User Guide.

Links
=====

.. Do not modify this comment unless you know what you're doing. tag:links-begin

Documentation: https://certbot.eff.org/docs

Software project: https://github.com/certbot/certbot

Notes for developers: https://certbot.eff.org/docs/contributing.html

Main Website: https://certbot.eff.org

Let's Encrypt Website: https://letsencrypt.org

Community: https://community.letsencrypt.org

ACME spec: http://ietf-wg-acme.github.io/acme/

ACME working area in github: https://github.com/ietf-wg-acme/acme

|build-status| |coverage| |docs| |container|

.. |build-status| image:: https://travis-ci.com/certbot/certbot.svg?branch=master
   :target: https://travis-ci.com/certbot/certbot
   :alt: Travis CI status

.. |coverage| image:: https://codecov.io/gh/certbot/certbot/branch/master/graph/badge.svg
   :target: https://codecov.io/gh/certbot/certbot
   :alt: Coverage status

.. |docs| image:: https://readthedocs.org/projects/letsencrypt/badge/
   :target: https://readthedocs.org/projects/letsencrypt/
   :alt: Documentation status

.. |container| image:: https://quay.io/repository/letsencrypt/letsencrypt/status
   :target: https://quay.io/repository/letsencrypt/letsencrypt
   :alt: Docker Repository on Quay.io

.. Do not modify this comment unless you know what you're doing. tag:links-end

System Requirements
===================

See https://certbot.eff.org/docs/install.html#system-requirements.

.. Do not modify this comment unless you know what you're doing. tag:intro-end

.. Do not modify this comment unless you know what you're doing. tag:features-begin

Current Features
=====================

* Supports multiple web servers:

  - apache/2.x
  - nginx/0.8.48+
  - webroot (adds files to webroot directories in order to prove control of
    domains and obtain certs)
  - standalone (runs its own simple webserver to prove you control a domain)
  - other server software via `third party plugins <https://certbot.eff.org/docs/using.html#third-party-plugins>`_

* The private key is generated locally on your system.
* Can talk to the Let's Encrypt CA or optionally to other ACME
  compliant services.
* Can get domain-validated (DV) certificates.
* Can revoke certificates.
* Adjustable RSA key bit-length (2048 (default), 4096, ...).
* Can optionally install a http -> https redirect, so your site effectively
  runs https only (Apache only)
* Fully automated.
* Configuration changes are logged and can be reverted.
* Supports an interactive text UI, or can be driven entirely from the
  command line.
* Free and Open Source Software, made with Python.

.. Do not modify this comment unless you know what you're doing. tag:features-end

For extensive documentation on using and contributing to Certbot, go to https://certbot.eff.org/docs. If you would like to contribute to the project or run the latest code from git, you should read our `developer guide <https://certbot.eff.org/docs/contributing.html>`_.
