# FreeIPA Cheatsheet 
 ###Pssh – Execute Commands on Multiple Remote Linux Servers Using Single Terminal
 `# yum install python-pip -y`
 `# pip install pssh`
*To read hosts file, include the -h host_file-name or –hosts host_file_name option.
*To include a default username on all hosts that do not define a specific user, use the -l username or –user username option.
*You can also display standard output and standard error as each host completes. By using the -i or –inline option.

`# pssh -h pssh-hosts -l root -A -i "uptime"`

`yum install -y ipa-server bind bind-dyndb-ldap bind-utils vim ipa-server-dns bindipa-server  rng-tools`

`systemctl start rngd && systemctl enable rngd && systemctl status rngd`

`# yum install ipa-server ipa-server-dns -y`
#### Add node to freeipa

`yum install ipa-client -y`

#### Update the resolv conf file with nameservice as freeipa ip address

`ipa-client-install --uninstall`

`ipa-client-install --domain=squadron-labs.com --server=c274-node4.squadron-labs.com  --realm=SQUADRON-LABS.COM --principal=admin@SQUADRON-LABS.COM --enable-dns-updates`
