##  Building with Github

How this works:
	
### 1. Commit

Github recieves the commit and sends a payload via a Post-Receive Hook. 

### 2. Github Hook

The payload looks something like this:

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

### 3. Horrible PHP

We have a horrible PHP script which parses the payload and sends the `ref` to Jenkins as a Build Paramater. This is because our Jenkins is behind the great firewall of China. 

### 4. Jenkins

	Jenkins Build Paramaters == Environment Variables

The build paramater is used to checkout the branch and build it.

![github](http://cdn.memegenerator.net/instances/400x/37900954.jpg)
