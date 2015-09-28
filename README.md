centminmod Ansible wrapper
=========

This is an Ansible helper role that wraps the [Centminmod](http://centminmod.com/)
bash script. It syncs the script with github, then manages common configuration
settings like memcached cache size, Zend OPcache size, CSF alerts, etc.

If you're using Centminmod, the following roles play well together:
  - **[centminmod wrapper](https://github.com/jeffwidman/ansible-centminmod)** (handles basic install + tuning common configuration settings)
  - **[mariadb](https://github.com/jeffwidman/ansible-mariadb)** (configures common my.cnf settings)
  - **[centminmod-domain-verification](https://github.com/jeffwidman/ansible-centminmod-domain-verification)** (tests that individual domains are configured properly)
  - **[php-fpm-pool](https://github.com/jeffwidman/ansible-php-fpm-pool)** (for creating/managing individual php-fpm pools for each PHP app)

Role Variables
--------------

Set your preferred `text_editor` and `email_address` somewhere in your playbook.

You'll likely also want to tweak the cache sizes--see what's possible in
`defaults/main.yml`.

Example Playbook
----------------

    - hosts: servers
      roles:
      - { role: centminmod,
            zend_opcache_size: 250,
            memcached_cache_size: 20,
            lf_permblock_alert: 0,
            tags: ['centminmod'] }

License
-------

MIT

Author Information
------------------

Jeff Widman jeff@jeffwidman.com
