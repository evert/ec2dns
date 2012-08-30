# ec2dns

ec2dns is a set of command line tools that makes it easy to display public hostnames of [EC2](http://aws.amazon.com/ec2/) instances and ssh into them via their tag name.

## Usage

```
$ ec2host
i-12345678: appserver-1    ec9-99-99-99-99.compute-1.amazonaws.com
i-87654321: appserver-2    ec1-11-11-11-11.compute-1.amazonaws.com

$ ec2host appserver-1
ec9-99-99-99-99.compute-1.amazonaws.com

$ ssh ubuntu@`ec2host appserver-1`
i-12345678: appserver-1    ec9-99-99-99-99.compute-1.amazonaws.com
ubuntu@ip-9-99-99-99:~$ 

$ ec2ssh appserver-2
i-12345678: appserver-1    ec1-11-11-11-11.compute-1.amazonaws.com
ubuntu@ip-1-11-11-11:~$ 
```

## Prerequisites

* Obviously an [AWS](http://aws.amazon.com) account and at least one running EC2 instance.
* Correctly set `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variables.
* You need [Composer](http://getcomposer.org) to install the dependencies - you should install it globally, as described [here](http://getcomposer.org/doc/00-intro.md#globally).
* You should have a `~/bin` directory and it should be included in your `PATH` environment variable.

## Installation

* Create the file `~/bin/composer.json` with your favourite text editor and paste the following content (or update your existing `composer.json` accordingly, if you already use this approach for something else).

```
{
    "require" : {

        "fruux/ec2dns" : "dev-master"

    },
    "config" : {
        "bin-dir" : "."
    }
}
```

* Save the file.
* Run `composer install` in your `~/bin` directory.
* Composer will now install `ec2host` and its dependencies.

## Updating

```
cd ~/bin
composer update
```

## Roadmap

* Set a nice prompt with the tag name when sshing into a machine via `ec2ssh appserver-1`.
* A cli tool (`ec2dns`) that updates /etc/hosts with the current public hostnames of all ec2 instances.

## Credits
ec2dns is inspired by [ec2-ssh](http://github.com/Instagram/ec2-ssh) and powered by [aws-sdk-for-php](http://github.com/amazonwebservices/aws-sdk-for-php).