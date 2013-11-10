## hubot

![AUTOMATE](http://wilmsmann.fullmontymedia.com/wp-content/uploads/2013/03/35059284.jpg)

We use hubot to do the following with Jenkins:

### Build status

The Jenkins Notifier plugin talks to hubot and he tells us when a build fails or is restored. 

### Release

Thanks to a combination of Jenkins and [yolo](https://github.com/alexfish/yolo), a gem created by yours truly. We can send a release via hubot by simply typing:

	hubot release BRANCH EMAIL@EMAIL.com, EMAIL@EMAIL.com
