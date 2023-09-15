# Guide-to-VPN-at-IITJ-campus

This a simple guide for using VPN on campus. Technically making your own VPN access server.

## Prerequisites

1. Github Student Developer Pack https://education.github.com/pack

2. Azure Account {with student pack you will get free 100$ credits}


## Steps

1. Go to Microsoft Azure and click on create a virtual machine & select azure virtual machine.
![Screenshot 2023-09-15 170159](https://github.com/11happy/Guide-to-VPN-at-IITJ-campus/assets/76656712/7a507160-e138-4696-8a76-9da3b0941eac)


3. Fill in the required details with carefully selecting image,size,region.Here's a sample choice.
![Screenshot 2023-09-15 170405](https://github.com/11happy/Guide-to-VPN-at-IITJ-campus/assets/76656712/84c65bf2-f799-4fa2-bcd9-5e0f8a205f6e)
![Screenshot 2023-09-15 170415](https://github.com/11happy/Guide-to-VPN-at-IITJ-campus/assets/76656712/bdca32a1-e27a-4b97-a29e-6da96f407ade)


3. Select SSH public key as authentication method and add inbound port 80 or 443.

![Screenshot 2023-09-15 170330](https://github.com/11happy/Guide-to-VPN-at-IITJ-campus/assets/76656712/fbe4395a-da08-4712-89e7-7839d726210d)
![Screenshot 2023-09-15 170343](https://github.com/11happy/Guide-to-VPN-at-IITJ-campus/assets/76656712/3c9dec0b-179a-4ab6-a45a-89ccf9f94bb1)


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
