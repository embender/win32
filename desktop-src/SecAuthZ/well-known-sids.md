---
Description: Well-known security identifiers (SIDs) identify generic groups and generic users.
ms.assetid: eb2f95c4-9465-409b-b76c-9ccae1d05eda
title: Well-known SIDs
ms.topic: article
ms.date: 04/19/2019
ms.custom: 19H1
---

# Well-known SIDs

Well-known [*security identifiers*](https://docs.microsoft.com/windows/desktop/SecGloss/s-gly) (SIDs) identify generic groups and generic users. For example, there are well-known SIDs to identify the following groups and users:

-   Everyone or World, which is a group that includes all users.
-   CREATOR\_OWNER, which is used as a placeholder in an inheritable ACE. When the ACE is inherited, the system replaces the CREATOR\_OWNER SID with the SID of the object's creator.
-   The Administrators group for the built-in domain on the local computer.

There are [*universal well-known SIDs*](https://docs.microsoft.com/windows/desktop/SecGloss/u-gly), which are meaningful on all secure systems using this security model, including operating systems other than Windows. In addition, there are well-known SIDs that are meaningful only on Windows systems.

The Windows API defines a set of constants for well-known identifier authority and [*relative identifier*](https://docs.microsoft.com/windows/desktop/SecGloss/r-gly) (RID) values. You can use these constants to create well-known SIDs. The following example combines the SECURITY\_WORLD\_SID\_AUTHORITY and SECURITY\_WORLD\_RID constants to show the universal well-known SID for the special group representing all users (Everyone or World):

S-1-1-0

This example uses the string notation for SIDs in which S identifies the string as a SID, the first 1 is the revision level of the SID, and the remaining two digits are the SECURITY\_WORLD\_SID\_AUTHORITY and SECURITY\_WORLD\_RID constants.

You can use the [**AllocateAndInitializeSid**](https://msdn.microsoft.com/library/Aa375213(v=VS.85).aspx) function to build a SID by combining an identifier authority value with up to eight subauthority values. For example, to determine whether the logged-on user is a member of a particular well-known group, call **AllocateAndInitializeSid** to build a SID for the well-known group and use the [**EqualSid**](https://msdn.microsoft.com/library/Aa446622(v=VS.85).aspx) function to compare that SID to the group SIDs in the user's [*access token*](https://docs.microsoft.com/windows/desktop/SecGloss/a-gly). For an example, see [Searching for a SID in an Access Token in C++](searching-for-a-sid-in-an-access-token-in-c--.md). You must call the [**FreeSid**](https://msdn.microsoft.com/library/Aa446631(v=VS.85).aspx) function to free a SID allocated by **AllocateAndInitializeSid**.

The remainder of this section contains tables of well-known SIDs and tables of identifier authority and subauthority constants that you can use to build well-known SIDs.

The following are some [*universal well-known SIDs*](https://docs.microsoft.com/windows/desktop/SecGloss/u-gly).



| Universal well-known SID    | String value       | Identifies                                                                                                                                               |
|-----------------------------|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Null SID<br/>         | S-1-0-0<br/> | A group with no members. This is often used when a SID value is not known.<br/>                                                                    |
| World<br/>            | S-1-1-0<br/> | A group that includes all users.<br/>                                                                                                              |
| Local<br/>            | S-1-2-0<br/> | Users who log on to [*terminals*](https://docs.microsoft.com/windows/desktop/SecGloss/t-gly) locally (physically) connected to the system.<br/> |
| Creator Owner ID<br/> | S-1-3-0<br/> | A security identifier to be replaced by the security identifier of the user who created a new object. This SID is used in inheritable ACEs.<br/>   |
| Creator Group ID<br/> | S-1-3-1<br/> | A security identifier to be replaced by the primary-group SID of the user who created a new object. Use this SID in inheritable ACEs.<br/>         |



 

The following table lists the predefined identifier authority constants. The first four values are used with universal well-known SIDs; the last value is used with Windows well-known SIDs.



| Identifier authority                         | Value        | SID string prefix |
|----------------------------------------------|--------------|-------------------|
| SECURITY\_NULL\_SID\_AUTHORITY<br/>    | 0<br/> | S-1-0<br/>  |
| SECURITY\_WORLD\_SID\_AUTHORITY<br/>   | 1<br/> | S-1-1<br/>  |
| SECURITY\_LOCAL\_SID\_AUTHORITY<br/>   | 2<br/> | S-1-2<br/>  |
| SECURITY\_CREATOR\_SID\_AUTHORITY<br/> | 3<br/> | S-1-3<br/>  |
| SECURITY\_NT\_AUTHORITY<br/>           | 5<br/> | S-1-5<br/>  |



 

The following [*RID*](https://docs.microsoft.com/windows/desktop/SecGloss/r-gly) values are used with [*universal well-known SIDs*](https://docs.microsoft.com/windows/desktop/SecGloss/u-gly). The Identifier authority column shows the prefix of the identifier authority with which you can combine the RID to create a universal well-known SID.



| Relative identifier authority            | Value        | Identifier authority |
|------------------------------------------|--------------|----------------------|
| SECURITY\_NULL\_RID<br/>           | 0<br/> | S-1-0<br/>     |
| SECURITY\_WORLD\_RID<br/>          | 0<br/> | S-1-1<br/>     |
| SECURITY\_LOCAL\_RID<br/>          | 0<br/> | S-1-2<br/>     |
| SECURITY\_LOCAL\_LOGON\_RID<br/>   | 1<br/> | S-1-2<br/>     |
| SECURITY\_CREATOR\_OWNER\_RID<br/> | 0<br/> | S-1-3<br/>     |
| SECURITY\_CREATOR\_GROUP\_RID<br/> | 1<br/> | S-1-3<br/>     |



 

The SECURITY\_NT\_AUTHORITY (S-1-5) predefined identifier authority produces SIDs that are not universal but are meaningful only on Windows installations. You can use the following RID values with SECURITY\_NT\_AUTHORITY to create well-known SIDs.



| Constant                                          | String value               | Identifies                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|---------------------------------------------------|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SECURITY\_DIALUP\_RID<br/>                  | S-1-5-1<br/>         | Users who log on to [*terminals*](https://docs.microsoft.com/windows/desktop/SecGloss/t-gly) using a dial-up modem. This is a group identifier.<br/>                                                                                                                                                                                                                                                                                                                                                                  |
| SECURITY\_NETWORK\_RID<br/>                 | S-1-5-2<br/>         | Users who log on across a network. This is a group identifier added to the token of a process when it was logged on across a network. The corresponding logon type is LOGON32\_LOGON\_NETWORK.<br/>                                                                                                                                                                                                                                                                                                                      |
| SECURITY\_BATCH\_RID<br/>                   | S-1-5-3<br/>         | Users who log on using a batch queue facility. This is a group identifier added to the token of a process when it was logged as a batch job. The corresponding logon type is LOGON32\_LOGON\_BATCH.<br/>                                                                                                                                                                                                                                                                                                                 |
| SECURITY\_INTERACTIVE\_RID<br/>             | S-1-5-4<br/>         | Users who log on for interactive operation. This is a group identifier added to the token of a process when it was logged on interactively. The corresponding logon type is LOGON32\_LOGON\_INTERACTIVE.<br/>                                                                                                                                                                                                                                                                                                            |
| SECURITY\_LOGON\_IDS\_RID<br/>              | S-1-5-5-*X*-*Y*<br/> | A logon session. This is used to ensure that only [*processes*](https://docs.microsoft.com/windows/desktop/SecGloss/p-gly) in a given logon session can gain access to the window-station objects for that session. The *X* and *Y* values for these SIDs are different for each logon session. The value SECURITY\_LOGON\_IDS\_RID\_COUNT is the number of RIDs in this identifier (5-*X*-*Y*).<br/>                                                                                                                   |
| SECURITY\_SERVICE\_RID<br/>                 | S-1-5-6<br/>         | Accounts authorized to log on as a service. This is a group identifier added to the token of a process when it was logged as a service. The corresponding logon type is LOGON32\_LOGON\_SERVICE.<br/>                                                                                                                                                                                                                                                                                                                    |
| SECURITY\_ANONYMOUS\_LOGON\_RID<br/>        | S-1-5-7<br/>         | Anonymous logon, or null session logon.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| SECURITY\_PROXY\_RID<br/>                   | S-1-5-8<br/>         | Proxy.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| SECURITY\_ENTERPRISE\_CONTROLLERS\_RID<br/> | S-1-5-9<br/>         | Enterprise controllers.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| SECURITY\_PRINCIPAL\_SELF\_RID<br/>         | S-1-5-10<br/>        | The PRINCIPAL\_SELF security identifier can be used in the ACL of a user or group object. During an access check, the system replaces the SID with the SID of the object. The PRINCIPAL\_SELF SID is useful for specifying an inheritable ACE that applies to the user or group object that inherits the ACE. It the only way of representing the SID of a created object in the default [*security descriptor*](https://docs.microsoft.com/windows/desktop/SecGloss/s-gly) of the schema.<br/> |
| SECURITY\_AUTHENTICATED\_USER\_RID<br/>     | S-1-5-11<br/>        | The authenticated users.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| SECURITY\_RESTRICTED\_CODE\_RID<br/>        | S-1-5-12<br/>        | Restricted code.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| SECURITY\_TERMINAL\_SERVER\_RID<br/>        | S-1-5-13<br/>        | Terminal Services. Automatically added to the security token of a user who logs on to a terminal server.<br/>                                                                                                                                                                                                                                                                                                                                                                                                            |
| SECURITY\_LOCAL\_SYSTEM\_RID<br/>           | S-1-5-18<br/>        | A special account used by the operating system.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| SECURITY\_NT\_NON\_UNIQUE<br/>              | S-1-5-21<br/>        | SIDS are not unique.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| SECURITY\_BUILTIN\_DOMAIN\_RID<br/>         | S-1-5-32<br/>        | The built-in system domain.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| SECURITY\_WRITE\_RESTRICTED\_CODE\_RID<br/> | S-1-5-33<br/>        | Write restricted code.<br/> |


 

The following RIDs are relative to each domain.



| RID                                                                | Value       | Identifies                                                                                                                                                                                                                                           |
|--------------------------------------------------------------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DOMAIN\_ALIAS\_RID\_CERTSVC\_DCOM\_ACCESS\_GROUP<br/>              | 0x0000023EL | The group of users who can connect to certification authorities using Distributed Component Object Model (DCOM).<br/>                                                                                                                          |
| DOMAIN\_USER\_RID\_ADMIN<br/>                                      | 0x000001F4L | The administrative user account in a domain.<br/>                                                                                                                                                                                              |
| DOMAIN\_USER\_RID\_GUEST<br/>                                      | 0x000001F5L | The guest-user account in a domain. Users who do not have an account can automatically log on to this account.<br/>                                                                                                                            |
| DOMAIN\_GROUP\_RID\_ADMINS<br/>                                    | 0x00000200L | The domain administrators' group. This account exists only on systems running server operating systems.<br/>                                                                                                                                   |
| DOMAIN\_GROUP\_RID\_USERS<br/>                                     | 0x00000201L | A group that contains all user accounts in a domain. All users are automatically added to this group.<br/>                                                                                                                                     |
| DOMAIN\_GROUP\_RID\_GUESTS<br/>                                    | 0x00000202L | The guest-group account in a domain.<br/>                                                                                                                                                                                                      |
| DOMAIN\_GROUP\_RID\_COMPUTERS<br/>                                 | 0x00000203L | The domain computers' group. All computers in the domain are members of this group.<br/>                                                                                                                                                       |
| DOMAIN\_GROUP\_RID\_CONTROLLERS<br/>                               | 0x00000204L | The domain controllers' group. All DCs in the domain are members of this group.<br/>                                                                                                                                                           |
| DOMAIN\_GROUP\_RID\_CERT\_ADMINS<br/>                              | 0x00000205L | The certificate publishers' group. Computers running Certificate Services are members of this group.<br/>                                                                                                                                      |
| DOMAIN\_GROUP\_RID\_ENTERPRISE\_READONLY\_DOMAIN\_CONTROLLERS<br/> | 0x000001F2L | The group of enterprise read-only domain controllers.<br/>                                                                                                                                                                                     |
| DOMAIN\_GROUP\_RID\_SCHEMA\_ADMINS<br/>                            | 0x00000206L | The schema administrators' group. Members of this group can modify the Active Directory schema.<br/>                                                                                                                                           |
| DOMAIN\_GROUP\_RID\_ENTERPRISE\_ADMINS<br/>                        | 0x00000207L | The enterprise administrators' group. Members of this group have full access to all domains in the Active Directory forest. Enterprise administrators are responsible for forest-level operations such as adding or removing new domains.<br/> |
| DOMAIN\_GROUP\_RID\_POLICY\_ADMINS<br/>                            | 0x00000208L | The policy administrators' group.<br/>                                                                                                                                                                                                         |
| DOMAIN\_GROUP\_RID\_READONLY\_CONTROLLERS<br/>                     | 0x00000209L | The group of read-only domain controllers.<br/>                                                                                                                                                                                                |                                             
| DOMAIN\_GROUP\_RID\_CLONEABLE\_CONTROLLERS<br />                   | 0x0000020AL | The group of cloneable domain controllers.<br/>                                                                                                                                                                                                |
| DOMAIN\_GROUP\_RID\_CDC\_RESERVED<br />                            | 0x0000020CL | The reserved CDC group.<br/>                                                                                                                                                                                                                   |
| DOMAIN\_GROUP\_RID\_PROTECTED\_USERS<br />                         | 0x0000020DL | The protected users group.</br>                                                                                                                                                                                                                |
| DOMAIN\_GROUP\_RID\_KEY\_ADMINS<br />                              | 0x0000020EL | The key admins group.<br/>                                                                                                                                                                                                                     |
| DOMAIN\_GROUP\_RID\_ENTERPRISE\_KEY\_ADMINS<br />                  | 0x0000020FL | The enterprise key admins group</br>                                                                                                                                                                                                           |



 

The following RIDs are used to specify mandatory integrity level.



| RID                                                     | Value                                               | Identifies                        |
|---------------------------------------------------------|-----------------------------------------------------|-----------------------------------|
| SECURITY\_MANDATORY\_UNTRUSTED\_RID<br/>          | 0x00000000<br/>                               | Untrusted.<br/>             |
| SECURITY\_MANDATORY\_LOW\_RID<br/>                | 0x00001000<br/>                               | Low integrity.<br/>         |
| SECURITY\_MANDATORY\_MEDIUM\_RID<br/>             | 0x00002000<br/>                               | Medium integrity.<br/>      |
| SECURITY\_MANDATORY\_MEDIUM\_PLUS\_RID<br/>       | SECURITY\_MANDATORY\_MEDIUM\_RID + 0x100<br/> | Medium high integrity.<br/> |
| SECURITY\_MANDATORY\_HIGH\_RID<br/>               | 0X00003000<br/>                               | High integrity.<br/>        |
| SECURITY\_MANDATORY\_SYSTEM\_RID<br/>             | 0x00004000<br/>                               | System integrity.<br/>      |
| SECURITY\_MANDATORY\_PROTECTED\_PROCESS\_RID<br/> | 0x00005000<br/>                               | Protected process.<br/>     |



 

The following table has examples of domain-relative RIDs that you can use to form well-known SIDs for local groups (aliases). For more information about local and global groups, see [Local Group Functions](https://docs.microsoft.com/windows/desktop/NetMgmt/local-group-functions) and [Group Functions](https://docs.microsoft.com/windows/desktop/NetMgmt/group-functions).



| RID                                                              | Value                 | Identifies                                                                                                                                                                                                                                                                                 |
|------------------------------------------------------------------|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DOMAIN\_ALIAS\_RID\_ADMINS<br/>                            | 0x00000220<br/> | A local group used for administration of the domain.<br/>                                                                                                                                                                                                                            |
| DOMAIN\_ALIAS\_RID\_USERS<br/>                             | 0x00000221<br/> | A local group that represents all users in the domain.<br/>                                                                                                                                                                                                                          |
| DOMAIN\_ALIAS\_RID\_GUESTS<br/>                            | 0x00000222<br/> | A local group that represents guests of the domain.<br/>                                                                                                                                                                                                                             |
| DOMAIN\_ALIAS\_RID\_POWER\_USERS<br/>                      | 0x00000223<br/> | A local group used to represent a user or set of users who expect to treat a system as if it were their personal computer rather than as a workstation for multiple users.<br/>                                                                                                      |
| DOMAIN\_ALIAS\_RID\_ACCOUNT\_OPS<br/>                      | 0x00000224<br/> | A local group that exists only on systems running server operating systems. This local group permits control over nonadministrator accounts.<br/>                                                                                                                                    |
| DOMAIN\_ALIAS\_RID\_SYSTEM\_OPS<br/>                       | 0x00000225<br/> | A local group that exists only on systems running server operating systems. This local group performs system administrative functions, not including security functions. It establishes network shares, controls printers, unlocks workstations, and performs other operations.<br/> |
| DOMAIN\_ALIAS\_RID\_PRINT\_OPS<br/>                        | 0x00000226<br/> | A local group that exists only on systems running server operating systems. This local group controls printers and print queues.<br/>                                                                                                                                                |
| DOMAIN\_ALIAS\_RID\_BACKUP\_OPS<br/>                       | 0x00000227<br/> | A local group used for controlling assignment of file backup-and-restore privileges.<br/>                                                                                                                                                                                            |
| DOMAIN\_ALIAS\_RID\_REPLICATOR<br/>                        | 0x00000228<br/> | A local group responsible for copying security databases from the primary domain controller to the backup domain controllers. These accounts are used only by the system.<br/>                                                                                                       |
| DOMAIN\_ALIAS\_RID\_RAS\_SERVERS<br/>                      | 0x00000229<br/> | A local group that represents RAS and IAS servers. This group permits access to various attributes of user objects.<br/>                                                                                                                                                             |
| DOMAIN\_ALIAS\_RID\_PREW2KCOMPACCESS<br/>                  | 0x0000022A<br/> | A local group that exists only on systems running Windows 2000 Server. For more information, see [Allowing Anonymous Access](allowing-anonymous-access.md).<br/>                                                                                                                    |
| DOMAIN\_ALIAS\_RID\_REMOTE\_DESKTOP\_USERS<br/>            | 0x0000022B<br/> | A local group that represents all remote desktop users.<br/>                                                                                                                                                                                                                         |
| DOMAIN\_ALIAS\_RID\_NETWORK\_CONFIGURATION\_OPS<br/>       | 0x0000022C<br/> | A local group that represents the network configuration. <br/>                                                                                                                                                                                                                       |
| DOMAIN\_ALIAS\_RID\_INCOMING\_FOREST\_TRUST\_BUILDERS<br/> | 0x0000022D<br/> | A local group that represents any forest trust users.<br/>                                                                                                                                                                                                                           |
| DOMAIN\_ALIAS\_RID\_MONITORING\_USERS<br/>                 | 0x0000022E<br/> | A local group that represents all users being monitored.<br/>                                                                                                                                                                                                                        |
| DOMAIN\_ALIAS\_RID\_LOGGING\_USERS<br/>                    | 0x0000022F<br/> | A local group responsible for logging users.<br/>                                                                                                                                                                                                                                    |
| DOMAIN\_ALIAS\_RID\_AUTHORIZATIONACCESS<br/>               | 0x00000230<br/> | A local group that represents all authorized access.<br/>                                                                                                                                                                                                                            |
| DOMAIN\_ALIAS\_RID\_TS\_LICENSE\_SERVERS<br/>              | 0x00000231<br/> | A local group that exists only on systems running server operating systems that allow for terminal services and remote access.<br/>                                                                                                                                                  |
| DOMAIN\_ALIAS\_RID\_DCOM\_USERS<br/>                       | 0x00000232<br/> | A local group that represents users who can use Distributed Component Object Model (DCOM).<br/>                                                                                                                                                                                      |
| DOMAIN\_ALIAS\_RID\_IUSERS<br/>                            | 0X00000238<br/> | A local group that represents Internet users.<br/>                                                                                                                                                                                                                                   |
| DOMAIN\_ALIAS\_RID\_CRYPTO\_OPERATORS<br/>                 | 0x00000239<br/> | A local group that represents access to cryptography operators.<br/>                                                                                                                                                                                                                 |
| DOMAIN\_ALIAS\_RID\_CACHEABLE\_PRINCIPALS\_GROUP<br/>      | 0x0000023B<br/> | A local group that represents principals that can be cached.<br/>                                                                                                                                                                                                                    |
| DOMAIN\_ALIAS\_RID\_NON\_CACHEABLE\_PRINCIPALS\_GROUP<br/> | 0x0000023C<br/> | A local group that represents principals that cannot be cached.<br/>                                                                                                                                                                                                                 |
| DOMAIN\_ALIAS\_RID\_EVENT\_LOG\_READERS\_GROUP<br/>        | 0x0000023D<br/> | A local group that represents event log readers.<br/>                                                                                                                                                                                                                                |
| DOMAIN\_ALIAS\_RID\_CERTSVC\_DCOM\_ACCESS\_GROUP<br/>      | 0x0000023E<br/> | The local group of users who can connect to certification authorities using Distributed Component Object Model (DCOM).<br/>                                                                                                                                                          |
| DOMAIN\_ALIAS\_RID\_RDS\_REMOTE\_ACCESS\_SERVERS<br />     | 0x0000023FL<br/>| A local group that represents RDS remote access servers.<br/> |
| DOMAIN\_ALIAS\_RID\_RDS\_ENDPOINT\_SERVERS                 | 0x00000240L<br/>| A local group that represents endpoint servers.<br/> |
| DOMAIN\_ALIAS\_RID\_RDS\_MANAGEMENT\_SERVERS               | 0x00000241L<br/>| A local group that represents management servers. <br/>|
| DOMAIN\_ALIAS\_RID\_HYPER\_V\_ADMINS                       | 0x00000242L<br/>| A local group that represents hyper-v admins <br/>|
| DOMAIN\_ALIAS\_RID\_ACCESS\_CONTROL\_ASSISTANCE\_OPS       | 0x00000243L<br/>| A local group that represents access control assistance OPS.<br/> |
| DOMAIN\_ALIAS\_RID\_REMOTE\_MANAGEMENT\_USERS              | 0x00000244L<br/>| A local group that represents remote management users. <br/>|
| DOMAIN\_ALIAS\_RID\_DEFAULT\_ACCOUNT                       | 0x00000245L<br/>| A local group that represents the default account. <br/>|
| DOMAIN\_ALIAS\_RID\_STORAGE\_REPLICA\_ADMINS               | 0x00000246L<br/>| A local group that represents storage replica admins. <br/>|
| DOMAIN\_ALIAS\_RID\_DEVICE\_OWNERS	                     | 0x00000247L<br/>| A local group that represents can make settings expected for Device Owners.<br/>|


 

The [**WELL\_KNOWN\_SID\_TYPE**](/windows/desktop/api/Winnt/ne-winnt-well_known_sid_type) enumeration defines the list of commonly used SIDs. Additionally, the [Security Descriptor Definition Language](security-descriptor-definition-language.md) (SDDL) uses [SID strings](sid-strings.md) to reference well-known SIDs in a string format.

 

 




