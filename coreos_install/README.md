Install CoreOS using CentOS Gnome Live in VMWare ESXI 5.1
	1. Download latest Gnome Live iso
http://buildlogs.centos.org/centos/7/isos/x86_64/

	2. Prepare coreos-install.sh file.
Download from https://raw.githubusercontent.com/coreos/init/master/bin/coreos-install
(www.coreos.com -> Install to Disk -> Code on github)

	3. Prepare cloud-config.yaml as here.
	Use password tool to encrypt password
	sudo openssl passwd -1
	
	Generate ssh key from client machine (that will be used to connect to coreos)
	ssh-keygen -t rsa -b 2048

	4. Create VM for CoreOS via vSphere Client.
	Set Memory to 2GB+
	Start -> Console -> Connect to ISO image on localdisk -> Gnome Live iso.

	5. Copy the files coreos-install.sh, cloud-config.yaml to the vm. 
	Update as necessary (hostname, password etc).
	Set execute permissions on .sh using chmod +x coreos-install.sh

	6. Install coreos using command
	sudo ./coreos-install.sh -d /dev/sda -C stable -c ./cloud-config.yaml
