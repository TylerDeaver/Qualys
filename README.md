# Vulnerability Management with Qualys
![Qualys Title Image](https://github.com/TylerDeaver/Qualys/assets/149614301/e2fe1b51-6a20-4787-ab69-fb4301e170ac)


## Summary and Purpose

This project is directly related to the [Vulnerability Management with OpenVAS](https://github.com/TylerDeaver/OpenVAS) project.

In this project, Oracle VirtualBox was used to create a Windows 10 virtual machine (VM) and a Qualys Virtual Scanner Appliance. 

To highlight the significance of properly configuring vulnerability scans, two types of scans were conducted. First, an unauthenticated scan was performed on the Windows 10 machine. Following the completion of the unauthenticated scan, a credentialed scan was configured and initiated. Based on the results of the credentialed scan, remediations were implemented to mitigate major vulnerabilities. 

A final credentialed scan was conducted to verify the effectiveness of the implemented remediations.


## Technologies, Azure Components, and Regulations Used

- Oracle VirtualBox
- Qualys Community Edition
- Windows 10 Pro VM
- Outdated software, known to have vulnerabilities
  - Mozilla Firefox, v104.0
  - VideoLAN VLC Media Player, v1.1.1


## Deploy Resources and Configure Virtual Machine for an Unauthenticated Scan

The first resource created in this project was the Qualys Virtual Scanner Appliance. While the appliance initialized, a Windows 10 Pro VM  was created. 

To prepare the Windows 10 machine, the firewall was disabled and outdated versions of Firefox, and VLC Media Player were installed. The goal was for the Windows 10 machine to be blatantly vulnerable. Once the firewall was disabled and the vulnerable software was installed, the machine was given a static IP address and restarted.

<br>Qualys was then configured to conduct an unauthenticated scan of the Windows 10 VM

##  Results of the Unauthenticated Scan

Due to the scan being unauthenticated, the vulnerabilities found do not accurately reflect the vulnerabilities known to be on the machine. The outdated software on the virtual machine is not reflected in this scan due to the limited capabilities inherent in unauthenticated scans.

![1 Uncredentialed](https://github.com/TylerDeaver/Qualys/assets/149614301/b4583584-24ef-451a-b065-764ab03a5ae6)
![2 detailed](https://github.com/TylerDeaver/Qualys/assets/149614301/f157bd68-23e0-46c1-8e54-1f45f0a32834)



## Configure Windows 10 for a Credentialed Scan

To configure the Windows 10 machine for a credentialed scan, the exact steps from the OpenVAS project were performed. The images provided below are from the OpenVAS project. 

The first step was to verify the Domain, Private, and Public profiles for Windows Firewall were still disabled from the initial configuration.

The following steps were then completed:

1. Disable User Account Control.


![7 disable user account control](https://github.com/TylerDeaver/OpenVAS/assets/149614301/87eb7d5f-c7e6-429d-b0e5-cb218243a04c)


2. Enable Remote Registry.


![remote registry](https://github.com/TylerDeaver/OpenVAS/assets/149614301/5197899e-c971-44e7-9cca-935b910297ec)


3. Navigate to the Windows Registry and create a new DWORD named “LocalAccountTokenFilterPolicy” and set the value to “1”.


![8 regedit](https://github.com/TylerDeaver/OpenVAS/assets/149614301/bcc9a5df-7068-45ad-bebd-03ed4cb5dbe7)


4. Restart the virtual machine.


## Configure Qualys for a Credentialed Scan

While the Windows 10 machine restarted, Qualys was provided the credentials for the Windows 10 VM. A credentialed scan was then performed to evaluate the true vulnerability status of the machine.


## Results of the Credentialed Scan

The difference in vulnerabilities discovered during the unauthenticated and credentialed scans is immediately apparent. During the unauthenticated scan, Qualys found one vulnerability. During the credentialed scan, Qualys found 82 vulnerabilities and four potential vulnerabilities. 

The credentialed scan allowed Qualys to fully evaluate the system, which included identifying vulnerabilities in the outdated software. To learn more about the vulnerabilities, Qualys allows users to expand the details of any given vulnerability. 

![3 credentialed](https://github.com/TylerDeaver/Qualys/assets/149614301/a1ca1d13-0705-4570-b271-a71739382cd6)
![4 detailed](https://github.com/TylerDeaver/Qualys/assets/149614301/62798200-a8f8-4142-bf69-f2739732d803)
![5 cve](https://github.com/TylerDeaver/Qualys/assets/149614301/e64e9dc4-d227-4e48-b150-bd26d1a997ad)


## Remediation, Verification Scan, and Conclusion

To remediate the majority of the vulnerabilities found during the credentialed scan, the outdated software was uninstalled from the Windows 10 machine. The operating system (OS) was also updated, as a large quantity of the vulnerabilities were related to the OS. Another credentialed scan was performed to verify the implemented remediations resolved the expected vulnerabilities. 

Based on the scan, the remediations were successful. During the verification scan, the vulnerability total dropped from 86 to >>>>>>>>>

![6 scan](https://github.com/TylerDeaver/Qualys/assets/149614301/054bc9cd-7954-4880-9b69-1f20dd653ef2)
![7 details](https://github.com/TylerDeaver/Qualys/assets/149614301/bfd653b0-e51c-457e-89c1-45560bc41a86)



This project successfully demonstrated the configuration of Qualys and the subsequent remediation of vulnerabilities. The project also demonstrated the importance of conducting credentialed scans when possible, as an unauthenticated scan does not accurately reflect the security of a system. Even though additional high severity vulnerabilities remained on the verification scan, remediating those vulnerabilities was not within the scope of this project.


## Reflection
This project was designed to give me hands-on experience with vulnerability management, to include configurations and remediations. This project directly relates to my other vulnerability management projects and was a great way to become more comfortable with different vulnerability management tools.


