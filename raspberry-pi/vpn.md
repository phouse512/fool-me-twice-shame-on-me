# basic openvpn setup
- if you are installing this using the readwrite tutorial, it references debian
  wheezy, not jessie. For a certain portion of copying rsa templates, check out
  this
  [link][http://raspberrypi.stackexchange.com/questions/37372/error-installing-openvpn-files-missing]
- make sure that the pi's iptables routing is set up correctly, here is the
  iptable command that usually works:
    - `sudo iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j
        MASQUERADE`
    - you can then run `sudo iptables -L -t nat` to make sure that it worked
        correctly
    - you should see see something like this referencing the ip `10.8.0.0/24`:
`Chain POSTROUTING (policy ACCEPT)`

`target     prot opt source               destination `

`MASQUERADE  all  --  anywhere             anywhere`

`MASQUERADE  all  --  anywhere             anywhere`

`MASQUERADE  all  --  10.8.0.0/24          anywhere`


- from `/etc/openvpn/server.conf`, you should be able to comment out the line
  that looks like: `local 192.168.someip` so that the server correctly restarts
