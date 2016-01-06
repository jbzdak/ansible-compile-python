Role Name
=========

Compiles a python interpreter from source, Python is the only thing it
downloads, rest is downloaded from debian repositories.

Tested for python 2.7.11, 3.5 and debian Jessies.
Should work for another combinations.

We also (optionally) run make test before finishing, to check any unforseen issues.
Tests are optionall since 25.12.2015 when ``test_ssl`` failed because
botched sertificate on ``svn.python.org``.

Requirements
------------

All requirements are installed using apt.

Role Variables
--------------

Following object: 
    
    python:
      # Will be installed here
      do_tests: true
      location: /usr/local/python/3.5.0
      version: 3.5.0
      compilation:
        # Build dependencies
        build_dep:
         - python3.4
        dependencies: []
      download:
        # Path to python interpreter with sha validation
        url: "https://www.python.org/ftp/python/3.5.0/Python-3.5.0.tar.xz"
        sha256sum: "d6d7aa1634a5eeeca6ed4fca266982a04f84bd8f3945a9179e20b24ad2e2be91"
    
Role regisers a single variable: 
    
    python_compiled_flag 
    
Which points to a flag file, that signifies that compilation was done.

Example
-------


If you need to install couple of python versions:

variables:

    python35:
      # Will be installed here
      do_tests: true
      location: /usr/local/python/3.5.0
      version: 3.5.0
      compilation:
        # Build dependencies
        build_dep:
         - python3.4
        dependencies: []
      download:
        # Path to python interpreter with sha validation
        url: "https://www.python.org/ftp/python/3.5.0/Python-3.5.0.tar.xz"
        sha256sum: "d6d7aa1634a5eeeca6ed4fca266982a04f84bd8f3945a9179e20b24ad2e2be91"

Playbook:

 - role: compile-python
    python: "{{python35}}"

    
License
-------

BSD
