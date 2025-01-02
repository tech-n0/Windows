# Demoting Domain Controller

Demoting a Domain Controller (DC) involves transitioning it from a DC role to a regular member server within an Active Directory forest. This guide outlines the required setups and steps to achieve this, specifically for a forest named "soc.boy." 

### **Pre-Demotion Checklist**
- Perform a full backup of the Domain Controller, including the system state, in case rollback is necessary.
- Update the server’s preferred DNS settings to point to an active DC or DNS server in the "soc.boy" forest. Update DNS records to reflect these changes.

#### **Start the Demotion Process**

- In Server Manager:
    
    1. Click **Manage** > **Remove Roles and Features**.
        
    2. Navigate to the **Server Roles** page.
        
    3. Uncheck **Active Directory Domain Services (AD DS)**.

![](Remove-Role.png)


![](1st.png)

The wizard will detect that the server is a DC and will prompt to demote it.
![](2nd.png)

Uncheck the "Active Directory Domain Services" to remove the AD functionality from the Domain Controller.

![](3rd.png)

Click Remove Features.

![](3.1.png)

It is safe to ignore the error message and click the "Demote this Domain Controller".

![](4th.png)

I only have one Domain Controller, so I'm selecting the second option "Last Domain". If you have two or more DC in a single domain then proceed with the first option.

![](5th.png)


![](6th.png)

Check both the options as we dont need DNS Zone and partitions. Also make sure you have proper backups.

![](7th.png)

Enter the Domain Admin credentials for the "soc.boy" domain password and click next.
![](8th.png)

Click **Demote this domain controller**.
![](9th.png)
#### **Restart the Server**

Once demotion is complete, the server will restart. It will no longer function as a DC but as a regular member server. Now, Try login with the local Administrator account password.

![](10th.png)


![](11th.png)


### **Post-Demotion Steps**

1. **Verify Demotion**:
    
    - Check in Active Directory Users and Computers (ADUC) to confirm the DC is no longer listed.
        
    - Use the `nltest /dsgetdc:soc.boy` command to ensure functionality of the remaining DCs.
        
2. **Metadata Cleanup** (if manual cleanup is required):
    
    - Use `ntdsutil` to remove lingering metadata of the demoted DC.
        
    - Run the following commands:
        
        ```
        ntdsutil
        metadata cleanup
        select operation target
        list domains
        select domain <domain_name>
        list sites
        select site <site_name>
        remove selected server
        ```
        
3. **Reconfigure Server**:
    
    - Remove any remnants of Active Directory configurations.
        
    - Reassign server roles if necessary (e.g., file sharing, application hosting).