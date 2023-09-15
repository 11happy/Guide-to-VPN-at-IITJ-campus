# Guide-to-VPN-at-IITJ-campus

This a simple guide for using VPN on campus. Technically making your own VPN access server.

## Prerequisites

1. Github Student Developer Pack https://education.github.com/pack

2. Azure Account {with student pack you will get free 100$ credits}


## Steps

1. Go to Microsoft Azure and click on create a virtual machine & select azure virtual machine.
![Screenshot 2023-09-15 170159](https://github.com/11happy/Guide-to-VPN-at-IITJ-campus/assets/76656712/f5e3918b-caf6-4ebe-a655-b24e0b93a23a)
2. Fill in the required details with carefully selecting image,size,region.Here's a sample choice.

![Screenshot 2023-09-15 170405](https://github.com/11happy/Guide-to-VPN-at-IITJ-campus/assets/76656712/9d803ee4-d6f7-43d8-ab66-f746f9140ab1)
![Screenshot 2023-09-15 170415](https://github.com/11happy/Guide-to-VPN-at-IITJ-campus/assets/76656712/19f27df3-2479-49e8-a961-cb3b5df76349)
3. Select SSH public key as authentication method and add inbound port 80 or 443.

![Screenshot 2023-09-15 170330](https://github.com/11happy/Guide-to-VPN-at-IITJ-campus/assets/76656712/f699de1a-d00d-481e-a89f-7a454ab80ad0)
![Screenshot 2023-09-15 170343](https://github.com/11happy/Guide-to-VPN-at-IITJ-campus/assets/76656712/3c64551f-c71f-4bdd-9065-e7b17c96d5f9)

4. Click create machine and make sure to download private key.
5. Now head over to the connect section and ssh into your VM using native ssh.
6. Skip to Step 8 if you are able to successfully ssh into your VM.
7. If you encounter problem unprotected private key watch this video : https://www.youtube.com/watch?v=mrUqITjUhL8
8. After successfully ssh into your VM run this script as root user.<br>
```bash
curl -O https://raw.githubusercontent.com/angristan/openvpn-install/master/openvpn-install.sh
chmod +x openvpn-install.sh
```

Then run it:

```sh
./openvpn-install.sh
```
10. Open VPN setup
```bash
1. Ip address : Public Ip of your VM
2. Ipv6: no
3. port: custom (80/443,port which is open for your VM)
4. DNS: Your choice (Google one is good)
5. Now leave rest settings to default keep pressing enter until script starts.
6. After script finished create a passwordless client and download its ovpn files.
7. To download  - scp -i <private key destination> <user>@<host>:<destination file>
```
11. Now download OPEN VPN client and upload the .ovpn file downloaded in previous step and Boom!.
