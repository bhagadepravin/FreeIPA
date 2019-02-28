# FreeIPA
FreeIPA Cheatsheet

yum install -y ipa-server bind bind-dyndb-ldap bind-utils vim ipa-server-dns bindipa-server  rng-tools

systemctl start rngd && systemctl enable rngd && systemctl status rngd

# Add node to freeipa

yum install ipa-client -y

# Update the resolv conf file with nameservice as freeipa ip address

ipa-client-install --uninstall

ipa-client-install --domain=squadron-labs.com --server=c274-node4.squadron-labs.com  --realm=SQUADRON-LABS.COM --principal=admin@SQUADRON-LABS.COM --enable-dns-updates
