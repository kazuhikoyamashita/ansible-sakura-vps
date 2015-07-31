# ansible-sakura-vps

## pre-preparation
### create private/public key using ssh-keygen command.
```
$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/username/.ssh/id_rsa): id_rsa_sakura
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in id_rsa_sakura.
Your public key has been saved in id_rsa_sakura.pub.
```

### edit $HOME/.ssh/config file.

```
Host sakura
  Hostname 192.168.33.10
  Port 10022
  User admin
  IdentityFile ~/.ssh/id_rsa_sakura
```

### install ansible usign pip command.

```
$ sudo easy_install pip
$ sudo pip install ansible
$ sudo pip install -U ansible
$ ansible --version
ansible 1.9.2
```

## run ansible

### initialize server settings.
```
$ ansible-playbook -i hosts sakura_init.yml -k -c paramiko
```

Notice: If you run ansible command, you need to speficy 'paramiko' option.

### install LAMP environment.

```
$ ansible-playbook sakura_lamp.yml -i hosts -vv
```

That's all. Enjoy!
