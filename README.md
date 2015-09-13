# github_multi_user_repo_tool_script
**Not yet Working!**
Allows you to quickly change the git configuration settings for a cloned repository on your computer using a shell script.

Multiple SSH Keys settings for different github accounts
=================================================================


create different public key(s)
---------------------------------

create different ssh key according the article [SSH Keygen Guide](https://help.github.com/articles/generating-ssh-keys/)

	$ ssh-keygen -t rsa -C "your_email@youremail.com"

Please refer to [github ssh issues](http://help.github.com/ssh-issues/) for common problems.

for example, 2 keys created at:

	~/.ssh/id_rsa_user1
	~/.ssh/id_rsa_user2

then, add these two keys as following

	$ ssh-add ~/.ssh/id_rsa_user1
	$ ssh-add ~/.ssh/id_rsa_user2

you can delete all cached keys before

	$ ssh-add -D

finally, you can check your saved keys

	$ ssh-add -l


Modify the ssh config
---------------------------------

	$ cd ~/.ssh/
	$ touch config
	$ subl -a config

Then add

	#user1 account
	Host github.com-user1
		HostName github.com
		User git
		IdentityFile ~/.ssh/id_rsa_user1

	#user2 account
	Host github.com-user2
		HostName github.com
		User git
		IdentityFile ~/.ssh/id_rsa_user2


Modify your Git config using script
---------------------------------------------
Put github_user.sh in your github folder

  	$ mv github_user.sh ~/YOUR-DIRECTORY-HERE/
  
then make the script executable

  	$ cd YOUR-DIRECTORY-HERE/
	$ chmod +x github_user.sh

then edit the script to add your users



then use normal flow to push your code

	$ git add .
	$ git commit -m "your comments"
	$ git push

