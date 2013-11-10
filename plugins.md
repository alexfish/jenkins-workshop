## Recommended Plugins

### Conditional build step

Critical if you want to do fun stuff with the build paramaters on a per branch basis, we for example only run the BDD suite on develop using this plugin.

### Build Name Setter

Set better names for your builds, we use:

	BUILD NUMBER: BRANCH

### PMD Plugin

We scan our source code with OCLint on every pull request, code smell reports can now be part of the code review.

![PMD](http://i.imgur.com/yp48zFL.png)

### Warnings Plugin

This plugin scans your build output for compiler warnings and generates a report, keep track of naughty developers who leave warnings all over the place or introduce compiler warnings with dangerous code.

![WARNING](http://i.imgur.com/KDQFy1C.png)

### Build Failure Analyzer

Add regex rules that apply to the build output to give your team human friendly build failure output, Jenkins console output can be LOOOOONG.

![FAIL](http://i.imgur.com/jkE4ETt.png)

### Jenkins Email Extension Plugin

Nicer looking notification emails, these are still ugly but not as ugly as the default. 
