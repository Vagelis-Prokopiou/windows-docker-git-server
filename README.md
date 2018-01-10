Virtualbox Network configuration:
	Adapter 1:
		Attached to: NAT
		Port forward
			Host IP: "Windows physical host IP"
			Host Port: 2222
			Guest IP: "Linux virtual host [$(docker machine ip default)]" (Usually 192.168.99.100)
			Guest Port: 2222 (Same as the (Windows host)
	Adapter 2:
		Attached to: Host-only Adapter
		Name: VisrualBox Host-Only Ethernet Adapter #2
		Promiscuous Mode: Allow All
		Cable connected: Checked

SSH Keys:
	Copy all the clients keys in the ./keys folder.

Repos:
	Create all your reposr in ./repos folder:
		mkdir <name>.git && cd <name>.git && git init --bare;
	Cloning a repo:
		From the Windows host:
			git clone ssh://git@$(docker machine ip default):2222/git-server/repos/<repo.git>
		From the different host in the LAN:
			git clone ssh://git@<Windows host IP>:2222/git-server/repos/<repo.git>