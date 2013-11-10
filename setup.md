# Jenkins Workshop


## EASY MODE

![lol](http://i1.kym-cdn.com/photos/images/newsfeed/000/413/041/81e.jpg)

## Get Jenkins

    http://goo.gl/Cf34T

## Install the Git Plugin

Manage Jenkins > Manage Plugins > Available > Git Plugin

## Add A Job

Call it whatever you like, it's good practice to not include spaces. 

#### Git URL

    https://github.com/alexfish/yolo-xcode-sample.git

## Configure it

#### Build step

    bundle install
    bundle exec rake yolo:build
    bundle exec rake yolo:ocunit:test

#### Post Build Action

Generate test reports

    test-reports/*.xml

## Build It

![build it fool](https://issues.jenkins-ci.org/secure/attachment/23210/context-menu-build-now.PNG)

## Success

![win](http://weknowmemes.com/wp-content/uploads/2012/02/full-of-win.jpg)
