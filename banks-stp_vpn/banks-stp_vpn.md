
systemctl list-units --type=service		# ver servicios corriendo


# Segurity Group que hace referencia a otro SG (aunque no se pueden andar)

$ pwd
/home/kueski/monitoring

$ ls
monitor.sh  monitortest.sh


$ cat monitor.sh
#!/bin/bash

if ipsec status | grep --quiet ESTABLISHED
then
  echo "strongSwan connection is established"
else
  echo "strongSwan connection is not established, restarting..."
  ipsec restart
  #send info to datadog
  echo -n "_e{18,25}:STP VPN connection|VPN Service was Restarted|t:warning" >/dev/udp/localhost/8125
fi


$ cat monitortest.sh
#!/bin/bash

if ipsec status | grep --quiet DDDDD
#if ipsec status | grep --quiet ESTABLISHED
then
  echo "strongSwan connection is established"
else
  echo "strongSwan connection is not established, restarting..."
fi


$ ipsec status
Segmentation fault


$ ping 10.5.1.1		# ver si recibe bien
PING 10.5.1.1 (10.5.1.1) 56(84) bytes of data.
64 bytes from 10.5.1.1: icmp_seq=1 ttl=254 time=122 ms
64 bytes from 10.5.1.1: icmp_seq=2 ttl=254 time=130 ms



$ pwd
/home/kueski/repo
$ ls.  		# Vacio
