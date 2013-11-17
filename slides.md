#Jenkins Workshop

!SLIDE

## Jenkins Workshop

!SLIDE

## Easy mode

![lol](http://i1.kym-cdn.com/photos/images/newsfeed/000/413/041/81e.jpg)

!SLIDE

### Get Easy Jenkins

	http://goo.gl/Cf34T
    
!SLIDE

### Install the Git Plugin

Manage Jenkins > Manage Plugins > Available > Git Plugin

!SLIDE

### Add A Job

    Build a free-style software project

!SLIDE

### Configure it

!SLIDE

### Git URL

    https://github.com/alexfish/yolo-xcode-sample.git

!SLIDE

### Build step

@@@ ruby
	bundle install
	bundle exec rake yolo:build
	bundle exec rake yolo:ocunit:test
@@@

!SLIDE

### Post Build Action

Generate test reports

    test-reports/*.xml
    
!SLIDE

### Build It

![build it fool](https://issues.jenkins-ci.org/secure/attachment/23210/context-menu-build-now.PNG)

!SLIDE

### Success

![win](http://weknowmemes.com/wp-content/uploads/2012/02/full-of-win.jpg)

!SLIDE

##  Building with Github

How this works..

!SLIDE

### 1. Commit

Github recieves the commit and sends a payload via a Post-Receive Hook. 

!SLIDE code

@@@ ruby
	{
	  :before     => before,
	  :after      => after,
	  :ref        => ref,
	  :commits    => [{
	    :id        => commit.id,
	    :message   => commit.message,
	    :timestamp => commit.committed_date.xmlschema,
	    :url       => commit_url,
	    :added     => array_of_added_paths,
	    :removed   => array_of_removed_paths,
	    :modified  => array_of_modified_paths,
	    :author    => {
	      :name  => commit.author.name,
	      :email => commit.author.email
	    }
	  }],
	  :repository => {
	    :name        => repository.name,
	    :url         => repo_url,
	    :pledgie     => repository.pledgie.id,
	    :description => repository.description,
	    :homepage    => repository.homepage,
	    :watchers    => repository.watchers.size,
	    :forks       => repository.forks.size,
	    :private     => repository.private?,
	    :owner => {
	      :name  => repository.owner.login,
	      :email => repository.owner.email
	    }
	  }
	}
@@@

!SLIDE

### 3. Horrible PHP

We have a horrible PHP script which parses the payload and sends the `ref` to Jenkins as a Build Paramater.

!SLIDE

### 4. Jenkins

	Jenkins Build Paramaters == Environment Variables

!SLIDE code

@@@ruby
		${BRANCH}
@@@

!SLIDE

##  Building Pull Requests

How this works:

!SLIDE

### 1. Github pull request builder plugin

!SLIDE

This plugin does all of the magic, just set it up in Jenkins with a user who has access to your repo. 

!SLIDE

### 2. Create a pull request builder job

!SLIDE

This prevents your main job being clogged up and spamming everybody.

!SLIDE

### 3. Pull request!

![sweeet](http://i.imgur.com/vy7PRub.png)

!SLIDE

## Recommended Plugins

!SLIDE

### Conditional build step

!SLIDE

Do fun stuff with the build paramaters on a per branch basis.

!SLIDE

### Build Name Setter

!SLIDE

Set better names for your builds, we use:

@@@ruby
		BUILD NUMBER: BRANCH
@@@

!SLIDE

### PMD Plugin

!SLIDE

![PMD](http://i.imgur.com/yp48zFL.png)

oclint powered code smell reports.

!SLIDE

### Warnings Plugin

!SLIDE

![WARNING](http://i.imgur.com/KDQFy1C.png)

!SLIDE

### Build Failure Analyzer

![FAIL](http://i.imgur.com/jkE4ETt.png)

!SLIDE

### Jenkins Email Extension Plugin

Nicer looking notification emails

!SLIDE

## hubot

!SLIDE

We use hubot to do the following with Jenkins:

!SLIDE

### Build status

campfire notifications when a build fails or is restored. 

!SLIDE

### Release

Release builds via campfire with [yolo](https://github.com/alexfish/yolo)

		hubot release BRANCH to EMAIL@EMAIL.com, EMAIL@EMAIL.com

!SLIDE

fun shit:

		https://github.com/ustwo/hubot

!SLIDE

##Thanks



