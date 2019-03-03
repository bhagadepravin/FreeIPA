# FreeIPA Cheatsheet 

`yum install -y ipa-server bind bind-dyndb-ldap bind-utils vim ipa-server-dns bindipa-server  rng-tools`

`systemctl start rngd && systemctl enable rngd && systemctl status rngd`

`# yum install ipa-server ipa-server-dns -y`

`# ipa-server-install --setup-dns`
```
ipa-server-install --realm=BEER.MYDOMAIN.COM --domain=beer.mydomain.com \
    --ds-password=$UNBREAKABLE_PASSWORD --admin-password=$UNBREAKABLE_PASSWORD \
    --hostname=freebeer.beer.mydomain.com --ip-address=199.1.x.x \
    --idstart=1001 --idmax=10000000 \
    --setup-dns --no-forwarders \
    --reverse-zone=1.199.in-addr.arpa --allow-zone-overlap
```

###### Add node to freeipa

 ###### Pssh – Execute Commands on Multiple Remote Linux Servers Using Single Terminal
 
 `# yum install python-pip -y`
 
 `# pip install pssh`

* To read hosts file, include the -h host_file-name or –hosts host_file_name option.
* To include a default username on all hosts that do not define a specific user, use the -l username or –user username option.
* You can also display standard output and standard error as each host completes. By using the -i or –inline option.

`# pssh -h pssh-hosts -l root -A -i "uptime"`

`# pssh -h pssh-hosts -l root -A -i "yum update -y"`

`# pssh -h pssh-hosts -l root -A -i "yum install ipa-client -y"`

 ###### Configure the HDP nodes to use the FreeIPA server for DNS resolution:

`# pssh -h pssh-hosts -l root -A -i "echo "nameserver $ipaserver_ip_address" > /etc/resolv.conf"`

`# pssh -h pssh-hosts -l root -A -i "cat /etc/resolv.conf"`

`# pssh -h pssh-hosts -l root -A -i "echo "172.26.81.236 pbhagade-freeipa.openstacklocal" >> /etc/hosts"`

###### Update the resolv conf file with nameservice as freeipa ip address

`# ipa-client-install --uninstall`

`# ipa-client-install --domain=squadron-labs.com --server=c274-node4.squadron-labs.com  --realm=SQUADRON-LABS.COM --principal=admin@SQUADRON-LABS.COM --enable-dns-updates`

```
ipa-client-install -p admin -w $UNBREAKABLE_PASSWORD --ip-address 199.1.x.x
```

`# pssh -h pssh-hosts -l root -A -i "yum clean all && yum update all"`

 * Execute below cmd, if ambari server version is less than 2.6.x

`# ipa group-add ambari-managed-principals`


#### Enable Experimental FreeIPA Support
Support for FreeIPA is not enabled by default in Ambari. You must enable the experimental functionality in Ambari before you can select FreeIPA as an option in the Kerberos wizard. In a browser, navigate to:

http://ambariserver.example.domain.com:8080/#/experimental

https://community.hortonworks.com/articles/59645/ambari-24-kerberos-with-freeipa.html

### Howto/DNS classless IN-ADDR.ARPA delegation

```
ipa dnszone-add 42.25.172.in-addr.arpa.
ipa dnszone-add 43.25.172.in-addr.arpa.
```

Ref: https://www.freeipa.org/page/Howto/DNS_classless_IN-ADDR.ARPA_delegation
