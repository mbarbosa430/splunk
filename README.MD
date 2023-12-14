# Splunk set up on RHEL 8.9

dnf install -y nano wget net-tools

wget -O splunk-9.1.2-b6b9c8185839.x86_64.rpm "https://download.splunk.com/products/splunk/releases/9.1.2/linux/splunk-9.1.2-b6b9c8185839.x86_64.rpm"

rpm -i splunk-9.1.2-b6b9c8185839.x86_64.rpm
rpm -i --replacepkgs splunk-9.1.2-b6b9c8185839.x86_64.rpm

cd /opt/splunk/bin
export SPLUNK_HOME=/opt/splunk
export PATH=$PATH:$SPLUNK_HOME/bin

./splunk start

splunk_admin:subduedlemure

firewall-cmd --permanent --zone=public --add-port={8000/tcp,8089/tcp,9997/tcp}
systemctl restart firewalld


----Backup here--------

splunk enable boot-start 

nmcli connection modify ens18 IPv4.address --internal IP address--

nmcli connection down ens18 && nmcli connection up ens18
