Runs a git server along with two client machine. https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server


# Prerequisite:
- Vagrant https://developer.hashicorp.com/vagrant
- Ansible https://docs.ansible.com/
- VirtualBox https://www.virtualbox.org/
- MacOS? :computer: Because I used the same. 

# Steps 
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
