# Gitserver

> Starting  your own Git server is now made simple and easy.

This project is to demonstrate the setup of simple git server along with two client machine. 
This follows the steps as described in the official git docs: https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server.
The virtual machines are brought up using vagrant and provisioned using ansible. Happy learning!

## Prerequisite:
- Vagrant https://developer.hashicorp.com/vagrant
- Ansible https://docs.ansible.com/
- VirtualBox https://www.virtualbox.org/
- MacOS? :computer: Because I used the same. Ideally, it should work on Windows and Linux as well. All the above three prerequisites can be installed on Windows/Linux/MacOS. In case you face issues running the commands, feel free to raise an issue on this repo.  

## Steps 
1. Bring up the VMs: gitserver, john and lara
```shell
vagrant up
```

2. Login into the John Wick's vm to create initial commit.
```shell
vagrant ssh john
$ vagrant@john: cd myproject
$ vagrant@john: git add README.md
$ vagrant@john: git commit -m "Initial commit"
$ vagrant@john: git remote add origin git@gitserver:/srv/git/project.git
$ vagrant@john: git push origin master
```

3. Login into Lara Croft's vm to clone and push changes.
```shell
vagrant ssh lara
$ vagrant@lara: git clone git@gitserver:/srv/git/project.git
$ vagrant@lara: cd project
$ vagrant@lara: vi README.md
$ vagrant@lara: git commit -am "fix for README file"
$ vagrant@lara: git push origin master
```

## Cleanup
Once you are done with your experimentation, you would wish to bring down the VMs(as they are eating your machine's resources). On your host machine run:
```shell
vagrant destroy -f
```

## Feedbacks
Feedbacks and optimisation are welcomed. Feel free to raise an issue on this repo. Also, if you want to suggest changes, you can fork the repository and suggest changes in the form of Pull request. If you found this project helpful, please drop a star.