# DC-and-AD

<topic id ="project-readme">
IT Home Lab — Domain Controller and Active Directory 


<p>Description</p>
<shortdesc>
A hands-on home lab project simulating a real-world IT environment. Built to demonstrate practical skills in Windows Server administration and Active Directory management.
</shortdesc>
<ul>
<li>Overview</li>
<li>Environment Setup</li>
<li>Domain Controller Configuration</li>
<li>Active Directory Management</li>
<li>Project Scenarios</li>
<li>Screenshots</li>
<ul>

---


<p>This lab simulates the core responsibilities of an entry-level IT Support Technician, including:</p>

<ul>
<li>Setting up and managing a Windows Server environment in AWS</li>
<li>Promoting a server to a Domain Controller using PowerShell</li>
<li>Managing users and groups in Active Directory</li>
</ul>

<h5>Tools & Technologies Used:<h5>
<ul>
<li>AWS EC2 (Windows Server 2022)</li>
<li>Active Directory Domain Services (AD DS))</li>
<li>PowerShell</li>
</ul>

---
 <h3>Environment Setup</h3>
<h4>AWS EC2 Instance</h4>

<h5>Steps taken:</h5>
<ol>
<li>Created AWS Free Tier account</li>
<li>Launched EC2 instance with Windows Server 2022</li>
<li>Configured Security Group to allow RDP only from my IP address</li>
<li>Retrieved administrator password using EC2 key pair</li>
<li> Connected via Remote Desktop (RDP)</li>
</ol>
<img width="1920" height="1040" alt="AWS EC2 set up Screenshot" src="https://github.com/user-attachments/assets/d47e1538-f2ea-4b91-957b-7ed10efb9373" />


---

<h2>Domain Controller Configuration</h2>

### Step 1 Install Active Directory Role

Opened PowerShell as Administrator and ran:

```powershell
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
```

### Step 2 Promote Server to Domain Controller

```powershell
Install-ADDSForest -DomainName "homelab.local"
```

Entered a Directory Services Restore Mode (DSRM) password when prompted. Server restarted automatically to complete promotion.

<img width="1471" height="934" alt="Promoting to Domain Server Screenshot" src="https://github.com/user-attachments/assets/7101a2c2-a02a-46c4-9e94-ef57240c9064" />


---

## Active Directory Management

All tasks performed via PowerShell and verified in the Active Directory Users and Computers (ADUC) GUI.

### Creating a User

```powershell
New-ADUser `
  -Name "Jon Snow" `
  -GivenName "Jon" `
  -Surname "Snow" `
  -SamAccountName "jsnow" `
  -UserPrincipalName "jSnow@yourdomain.local" `
  -AccountPassword (ConvertTo-SecureString "Password123!" -AsPlainText -Force) `
  -Enabled $true
```

<img width="1796" height="1054" alt="Adding user screen shot" src="https://github.com/user-attachments/assets/1da2bc87-4cca-43f3-bafe-e2ab33a4ad58" />

---

### Modifying a User

```powershell
Set-ADUser -Identity "jSnow" -Title "King of the North" -Department "House Stark"
```
<img width="1860" height="1040" alt="Modifying User " src="https://github.com/user-attachments/assets/57fe09b4-1d78-42bd-adbd-29f568288e44" />

---

### Deleting a User

```powershell
Remove-ADUser -Identity "jdoe"
```
<img width="1860" height="1032" alt="Removig User SS" src="https://github.com/user-attachments/assets/2f24a27f-b037-4292-9a0a-2fab616be84e" />

---

### Creating a Security Group

```powershell
New-ADGroup -Name "Targaryen" -GroupScope Global -GroupCategory Security
```

---

### Adding a User to a Group

```powershell
Add-ADGroupMember -Identity "Targaryen" -Members "jSnow"
```

<img width="1860" height="1040" alt="Adding and creatinf a groups ss" src="https://github.com/user-attachments/assets/94a3afc3-5165-479b-9619-04c3008b9668" />


## Skills Demonstrated

| Skill | Details |
|---|---|
| Cloud Infrastructure | Deployed and configured Windows Server on AWS EC2 |
| Windows Server Administration | Installed roles, managed services, navigated Server Manager |
| PowerShell | Automated AD tasks including user/group creation and modification |
| Active Directory | User lifecycle management, group policy, OU structure |
| Documentation | Step-by-step runbooks with screenshots for all procedures |

---

## About This Project

This home lab was built to develop and demonstrate practical IT support skills as part of my preparation for entry-level admin responsibilities.

