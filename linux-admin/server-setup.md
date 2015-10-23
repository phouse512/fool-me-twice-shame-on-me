when creating new linux servers (written for ubuntu), don't forget to do this stuff:

*delineating big sections for now - details will come later*

# setting up ssh keys
passwords are fickle - use keys for authentication

 - run `ssh-keygen` to generate a key on your local machine (not the server)
    - this will ask you in which file you'd like to create it (default is in /*you*/.ssh/id_rsa) - if you don't know what's going on here, keep it like this.
    - it will ask for a passphrase - type a good one (and don't forget it!)
 - now move the public key (id_rsa.pub) to the machine you're setting up however you'd like (brute force cp/pst, cat, etc)
    - to do so, you can brute force pbcopy/paste, cat, scp
    - I like `cat id_rsa.pub | root@machineip 'cat >> .ssh/authorized_keys'` 
    - you'll have to use a password once more
 - next, we need to change ssh config settings
    - run `sudo nano /etc/ssh/sshd_config` or vim ~~
    - change the `PasswordAuthentication` line to look like: `PasswordAuthentication no`
    - write changes, and quit
 - restart (as root) ssh by running `sudo service ssh restart
 -
 **TODO** - add more info about setting up users (namely not using root)
