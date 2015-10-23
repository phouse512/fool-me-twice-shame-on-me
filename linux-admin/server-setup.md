when creating new linux servers (written for ubuntu), don't forget to do this stuff:

*delineating big sections for now - details will come later*

# setting up ssh keys
passwords are fickle - use keys for authentication

 - run `ssh-keygen` to generate a key on your local machine (not the server)
    - this will ask you in which file you'd like to create it (default is in /*you*/.ssh/id_rsa) - if you don't know what's going on here, keep it like this.
    - it will ask for a passphrase - type a good one (and don't forget it!)
 - now move the public key (id_rsa.pub) to the machine you're setting up however you'd like (brute force cp/pst, cat, etc)
    - I like `cat id_rsa.pub | root@machineip 'cat >> .ssh/authorized_keys'` but its up to you (scp is good too)
    - you'll have to use a pwd one last time
