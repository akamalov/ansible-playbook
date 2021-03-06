======================
Plone Ansible playbook
======================

.. admonition:: Description

    Use Ansible to provision a full-stack Plone server


Introduction
------------

Plone's Ansible Playbook can completely provision a remote server to run the full stack of Plone, including:

* Plone in a cluster configuration;

* Automatic starting and process control of the Plone cluster with `supervisor <http://supervisord.org>`_;

* Load balancing of the cluster with `HAProxy <http://www.haproxy.org/>`_;

* Caching with `Varnish <https://www.varnish-cache.org/>`_;

* `Nginx <http://wiki.nginx.org/Main>`_ as a world-facing remote proxy and URL rewrite engine;

* An outgoing-mail-only mail server using `Postfix <http://www.postfix.org/>`_;

* Monitoring and log analysis with `munin-node <http://munin-monitoring.org/>`_ and `logwatch <http://linuxcommand.org/man_pages/logwatch8.html>`_ and `fail2ban <http://www.fail2ban.org/wiki/index.php/Main_Page>`_.

* Use of a local `VirtualBox <https://www.virtualbox.org/>`_ provisioned via `vagrant <https://www.vagrantup.com/>`_ to test and model your remote server.

An ansible playbook and roles describe the desired condition of the server. The playbook is used both for initial provisioning and for updating.

We generally support relatively current CentOS and Debian/Ubuntu environments. Versions currently supported are Ubuntu 16.0.4 (Xenial) LTS, Ubuntu 15, Ubuntu 14, Debian wheezy, Debian jessy, and CentOS 7.

See the ``docs`` subdirectory or `readthedocs <http://plone-ansible-playbook.readthedocs.org/en/latest/>`_ for complete documentation.

Detailed, tutorial-style documentation with lots of real-life examples is available at the `Plone Training <https://training.plone.org/5/deployment/index.html>`_ site.

TL;DR
^^^^^

1. Install a *current* version of Ansible (use virtualenv and pip -- not your OS package manager);

2. If you wish to test locally, install Vagrant and VirtualBox;

3. Check out or download a copy of `the STABLE branch of this package <https://github.com/plone/ansible-playbook>`_;

4. Run ``ansible-galaxy -p roles -r requirements.yml install`` to install required roles;

5. Copy one of the ``sample*.yml`` files to ``local-configure.yml`` and edit as needed.

6. To test in a local virtual machine, run ``vagrant up`` or ``vagrant provision``;

7. To deploy, create an Ansible inventory file for the remote host and run ``ansible-playbook --ask-sudo-pass -i myhost.cfg playbook.yml``;

8. Set a real password for your Plone instance on the target server;

9. Set up appropriate firewalls.

.. warning::

    This version of the playbook requires that the plone.plone_server role be 1.2.0+.

License
-------

BSD-3-Clause
