Role Name
=========

Compiles a python interpreter from source, Python is the only thing it
downloads, rest is downloaded from debian repositories.

Tested for python 3.5 and debian Jessies. Should work for another combinations. 

We also run make test before finishing, to check any unforseen issues. 

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

Following object: 
    
    python:
    # Will be installed here
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
    
License
-------

BSD
