<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
In this lab i outline the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>
<p> Setup Resources in Azure
<br> - Create the Domain Controller VM (Windows Server 2022) named “DC-1” </b>
<br> - Resource group: "AD-Lab" , Virtual Network (vnet): "DC-1-vnet"  </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/00cff8d9-ba54-4cef-97b8-5ae88dbcb083)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/754028f2-6fd8-4f90-acae-ea34797d36c1)

<p>
  <br> - Set Domain Controller’s NIC Private IP address to be static </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/84ae9267-bac7-481e-ac76-de40bfe71d62)

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/508dfedd-eebb-4732-a633-213d089f8e15)




<p>
  <br> - Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created for DC-1 </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/c0fff143-1c2c-422f-8653-5d0317b029b5)

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/0dba6d04-a8e3-4149-9ccc-32b252525441)

<p>
  <br> - Ensure that both VMs are in the same Vnet </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/50534d48-876b-40f2-a2fa-5310105fb460)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/ea70a1a5-9247-400e-9599-9882bca563b0)






