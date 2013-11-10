##  Building with Github

How this works:
	
### Commit

Github receives a commit and sends a build hook to our script. 

### Github Hook

Github recieves the commit and sends a payload to our script via a Post-Receive Hook. 

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

### Horrible PHP

We have a horrible PHP script which parses the payload and sends the Branch to Jenkins as a Build 

### Jenkins

	Jenkins Build Paramaters == Environment Variables

The build paramter is used to checkout the branch and build it + run other magic. 
