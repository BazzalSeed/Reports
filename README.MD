## From SVN to Git

#### Why Git is better?
Although i come in with a strong bias favoring Git over SVN, the truth is git is not better. SVN definitely has its own advantage such as easy to implement locking mechanism. However, Git will benefit an agile team like us in the following two major aspects
###### Distributed system for every developer
Git is a distributed version control system. So what does “distributed” actually mean? Well it means that instead of running `svn checkout (url)` to get the latest version of your repository, with Git you run `git clone (url)`, which gives you a complete copy of the entire history of that project. This means that immediately after the clone, there is basically no information about that project that the server you cloned from has that you do not have. Interestingly, Subversion is so inefficient at this that in general it’s nearly as fast to clone an entire repository over Git as it is to checkout a single version of the same repository over Subversion.

As a result (nearly) every operation is now done off data on your local disk, meaning that it is both unbelievably fast and can be done offline. This means that you can do commits, diffs, logs, branches, merges, file annotation and more – entirely offline, off VPN and generally instantly. Most commands you run in Git take longer to type then they do to execute. Now stop for a moment and try to remember how many times you’ve gone to get a cup of coffee while Subversion has been running some command. Or jot down a quick list of occasions on which you’ve wanted to commit but didn’t have an internet connection or couldn’t connect to your corporate VPN.

A very nice [stackoverflow reponse](http://stackoverflow.com/questions/871/why-is-git-better-than-subversion) goes into more detail on this
###### Modern Deployment ecosystem
Another reason why we might prefer Git over SVN is that it is more native for a countinous delivery workflow (CI and CD), which can be extremly beneficial for an agile team like us. Two very detailed documentations from Atalassian can be found here
  * [Super-powered continuous delivery with Git](https://www.atlassian.com/continuous-delivery/why-git-and-continuous-delivery-are-super-powered)
  * [CI friendly Git Repo](https://www.atlassian.com/continuous-delivery/ci-friendly-git-repos)



#### Migration from SVN to Git

The main challenge here is how to maintain the commit history (If we eventually choose to host our own git service on AWS or Chicago datacenter, extra step exists to set up the git service). Fortunately, it is a rather common migration process and a rather [well-written documentation](https://www.atlassian.com/git/tutorials/migrating-overview/) is again provided by Atlassian
