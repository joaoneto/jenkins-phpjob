# Jenkins PHP Job
Jenkins PHP Job, based on http://jenkins-php.org, is a light version of job schema for jenkins for automatize PHPUnit tests.

## Features
    1. Code coverage
    2. Perform syntax check of sourcecode files
    3. Run unit tests with PHPUnit
    4. Find duplicate code using PHPCPD
    5. Calculate software metrics using PHP_Depend
    6. Perform project mess detection using PHPMD creating a log file for the continuous integration server

## Dependences
Steps to setup Jenkins PHP Job enviroment:

### 1. PHPUnit
```bash
    % sudo pear channel-discover pear.phpunit.de
    % sudo pear channel-discover pear.symfony.com
    % sudo pear update-channels
    % sudo pear install --alldeps phpunit/PHPUnit
    % sudo pear install phpunit/DbUnit
    % sudo pear install phpunit/PHPUnit_Story
```

### 2. Jenkins
Install jenkins (Ubuntu 12.04):
```bash
    % wget -q -O - http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -
    % sudo sh -c 'echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list'
    % sudo apt-get update
    % sudo apt-get install jenkins
    % sudo su jenkins
```
Install plugins:
```bash
    % cd ~
    % wget http://localhost:8080/jnlpJars/jenkins-cli.jar
    % java -jar jenkins-cli.jar -s http://localhost:8080 install-plugin checkstyle cloverphp dry htmlpublisher jdepend plot pmd violations xunit
    % java -jar jenkins-cli.jar -s http://localhost:8080 safe-restart
```

### 3. Clone Jenkins PHP Job
```bash
    % cd ~/jobs/
    % git clone git://github.com/joaoneto/jenkins-phpjob.git
```

### 4. Configure
    1. Access http://localhost:8080
    2. Click on "New Job"
    3. Enter a "Job name"
    4. Select "Copy existing job" and enter "jenkins-phpjob" into the "Copy from" field
    5. Click "OK"
    6. Disable the "Disable Build" option
    7. Click "Save"

