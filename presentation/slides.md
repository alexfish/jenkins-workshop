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

We have a horrible PHP script which parses the payload and sends the `ref` to Jenkins as a Build Paramater. This is because our Jenkins is hidden from the outside world.

!SLIDE

### 4. Jenkins

	Jenkins Build Paramaters == Environment Variables
