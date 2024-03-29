# RADIUS
The purpose of this repository is to give a step by step process on how to create and configure a RADIUS WI-FI authentication server on Active Directory

# Add AD DS
1. Click on Add new roles and features
2. Next
3. Installation type > Role-based or featured based installation > Next
4. Select the RADIUS server
5. Add Active Directory Domain Services and install
6. On the Notfications tab, in the "Post-deployment Configuration" click on "Promote this server to a domain controller"

# Deployment Configuration
1. Add a new forest
2. Add a Root domain name. i.e: mylab.local
3. Type a password. Leave all other options in their default setting.
4. DNS delegation, left unchecked
5. Additional options > Next
6. Paths > Next
7. Review Options > Next
8. Prerequisites Check > if All prerequisite passed successfuly > Install
9. Close. Restart the computer.
**Applying the settings can take some time**

# Active Directory Certificate Services (CA)
1. Manage > Add roles and features
2. Server Roles > add Active Directory Certificate Services
3. Role Services > Certification Authority check only
4. Check "Restart the destination server automatically if required"
5. Install
6. On the Notfications tab, in the "Post-deployment Configuration" click on "Configure Active Directory Certificate Services on the destination server"
7. Next
8. Role Services > check Certification Authority
9. Setup type > Enterprise CA
10. CA type > Root CA
11. Private key > New private key > RSA#Microsoft Software Key Storage Provider > SHA256 > Key lenght: 2048
12. CA name > Next
13. Validity period > Next
14. Cerificate database > Next
15. Confirmation > Configure > Close

# Installing and configuring NAP (Network Policy and Access Services)
1. Add a new role and feature
2. Server roles > add Network Policy and Access Services
3. Install
4. Click on the NPAS tab and then click on AD Users and Coputers under Tools
5. On the created domain, in this case: **mylab.local**, go to the Users folder > Right click > New > User
6. Create a new user credentials
7. Uncheck "User must change password at next logon" and check the two options below
8. Right click > Create a new Group
9. Add the user to the Group
10. On the user Properties > Dial in > Allow Access in Network Access permission

# Network policy Server configuration
1. On the Server tab > Right click > Network policy Server
2. Standard Configuration > RADIUS server for 802.1x Wireless or Wired Connections
3. Configure 802.1x
4. Select Secure Wireless connections
5. RADIUS Clients > Add
6. Add a Name, Address: 192.168.0.250 and Shared secret (password)
7. Next
8. Select Protected EAP(PEAP)
9. Specify User Groups > Add > Enter the object name to select (the group name previously created)
10. Next
11. "You have successfuly created the following policies and configured the following RADIUS clients" > Finish
12. Go to Network and Sharing Center > Ethernet > Properties > Select "Internet Protocol Version 4" > Properties
13. Preferred DNS Server: 192.168.0.252

# Configuring the Access Point
1. Open Internet Explorer and type the address used to configure your Access Point
2. Add the address to Trusted Sites
3. On LAN settings change the IP address to 192.168.0.250
4. On Wireless security settings switch to WPA2 Enterprise and add the RADIUS IP Server: 192.168.0.252 > then set a RADIUS password (has to be the same used for "Shared secret")
5. Save and reboot the device
