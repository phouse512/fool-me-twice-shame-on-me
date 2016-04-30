# basic openvpn setup

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
