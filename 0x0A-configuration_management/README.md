## Puppet Configuration Management Tasks

This repository contains Puppet manifests for the following configuration management tasks:

### Task 0: Create a File

- **Description**: Using Puppet, this task involves creating a file in `/tmp` directory with specific permissions and content.
  
  - **File Path**: `/tmp/school`
  - **File Permission**: 0744
  - **File Owner**: www-data
  - **File Group**: www-data
  - **File Content**: "I love Puppet"

  Example:
  ```
  root@6712bef7a528:~# puppet apply 0-create_a_file.pp
  Notice: Compiled catalog for 6712bef7a528.ec2.internal in environment production in 0.04 seconds
  Notice: /Stage[main]/Main/File[school]/ensure: defined content as '{md5}f1b70c2a42a98d82224986a612400db9'
  Notice: Finished catalog run in 0.03 seconds
  root@6712bef7a528:~#
  ```

### Task 1: Install a Package

- **Description**: Using Puppet, install the Flask package from `pip3` with a specific version.

  - **Package Name**: Flask
  - **Version**: 2.1.0

  Example:
  ```
  root@9665f0a47391:/# puppet apply 1-install_a_package.pp
  Notice: Compiled catalog for 9665f0a47391 in environment production in 0.14 seconds
  Notice: /Stage[main]/Main/Package[Flask]/ensure: created
  Notice: Applied catalog in 0.20 seconds
  root@9665f0a47391:/# flask --version
  Python 3.8.10
  Flask 2.1.0
  Werkzeug 2.1.1
  ```

### Task 2: Execute a Command

- **Description**: Using Puppet, create a manifest to terminate a process named `killmenow` using `pkill`.

  Example:
  ```
  Terminal #0 - starting my process

  root@d391259bf577:/# cat killmenow
  #!/bin/bash
  while [[ true ]]
  do
      sleep 2
  done

  root@d391259bf577:/# ./killmenow

  Terminal #1 - executing my manifest

  root@d391259bf577:/# puppet apply 2-execute_a_command.pp
  Notice: Compiled catalog for d391259bf577.hsd1.ca.comcast.net in environment production in 0.01 seconds
  Notice: /Stage[main]/Main/Exec[killmenow]/returns: executed successfully
  Notice: Finished catalog run in 0.10 seconds
  root@d391259bf577:/# 

  Terminal #0 - process has been terminated

  root@d391259bf577:/# ./killmenow
  Terminated
  ```

### Repository Information

- **GitHub Repository**: [alx-system_engineering-devops](https://github.com/alx-system_engineering-devops)
- **Directory**: 0x0A-configuration_managemen
