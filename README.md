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

<p>
  <br> Ensure Connectivity between the client and Domain Controller </b>
  <br> - Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping) </b>
</p>
    
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/c49a8d73-04f9-44bd-83e4-7d07fcde7a5a)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/a83fdb9e-446b-4c17-8581-cd13a222a014)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/8706cb59-e194-4320-832a-b677c1f5cb84)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/dc01486d-2ccb-4c84-a674-07f31fcc5aa9)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/efb43163-85f8-4d71-b16a-79886ecfa303)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/ca81bd78-3086-4643-bde9-d1268876e6c4)

<p>
  <br> - Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/b0ba4a16-28f1-4254-b3af-8a94c859a0b7)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/ef15cb1c-d132-42b4-9ef1-fb5a1460ceb7)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/4fc02e2a-4211-480d-9efd-2632122fc29d)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/fe56de0d-b61c-4607-9092-d5b27154517d)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/2aa774c0-a4c5-4391-a6f3-fb828e2b20ef)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/bb7b1305-d86d-4b7a-bfd7-da50601508d2)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/77ff09c8-5f3f-4373-a4ec-7be25507f776)

<p>
  <br> Install Active Directory </b>
  <br> - Login to DC-1 and install Active Directory Domain Services </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/30ca5757-4f24-45f5-b548-93081f16e9d1)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/45daa853-a6e5-4c15-bd18-d07548374618)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/729d4f0e-bffd-4ae1-86f4-ef89c77872a6)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/9976ff1d-7f30-4809-8baf-198c3c800d74)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/5d443c61-064a-437e-9e4d-a2316d5a57b7)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/1e73dc5f-0e22-438d-8f22-89a5019da8c2)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/08ca3df0-80e8-4873-b6c3-93528b764175)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/75e00786-aa4a-40da-a1f7-3a999fe037c2)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/68890dae-dc26-4260-9ea1-0b407b9357b9)

<p>
  <br> - Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is) </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/48e40113-aa19-4620-8317-97a67d5a29ca)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/b08b694b-3b36-4023-ab35-022af057fd49)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/8ca89f1e-349e-41bd-b6f6-de632c9c6722)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/bb0ac2a7-1629-414b-9f53-236e84d7f6c1)

<p>
  <br> - Restart and then log back into DC-1 as user: mydomain.com\labuser </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/dafdef70-cff2-430f-a118-57ea5c62d866)

<p>
  <br> Create an Admin and Normal User Account in AD </b>
  <br> - In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES” </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/e50f6da2-7954-41ca-a65b-93684222206c)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/576867cc-dc64-43e3-90ea-b7b986570616)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/9e42c919-66dd-4a4e-99a3-d8f97852a2eb)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/6ea9fba3-8907-407f-840c-537f1e17e736)

<p>
  <br> - Create a new OU named “_ADMINS” </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/226797ae-bd52-4415-b239-17d6a20438d6)

<p>
  <br> - Create a new employee named “Jane Doe” (same password) with the username of “jane_admin” </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/bbc3a023-1502-4088-b942-e363c58fb6a8)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/4447f1a2-d467-4424-8c2c-0806c891e2a6)

<p>
  <br> - Add jane_admin to the “Domain Admins” Security Group </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/401ca224-dc6d-44d7-b44d-655b126bc40c)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/6edf5bba-69f8-483a-a45e-5cd8b21af4e4)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/f868fde0-080a-4c20-84ca-eac5b3f7f999)

<p>
  <br> - Log out/close the Remote Desktop connection to DC-1 and log back in as “mydomain.com\jane_admin” </b>
</p>

![image](https://github.com/IZEK4K/configure-ad/assets/90485066/09befa09-1d6c-4186-9803-0409c8caed85)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/afe4c072-626f-4962-a37d-269cb1b25421)
![image](https://github.com/IZEK4K/configure-ad/assets/90485066/495f6a92-7f41-4ebd-bdd8-2222d6fd0c15)

<p>
  <br> Join Client-1 to your domain (mydomain.com) </b>
</p>


















