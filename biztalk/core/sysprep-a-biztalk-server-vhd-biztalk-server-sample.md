---
title: "Sysprep BizTalk Server VHD （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35f0146d-60ed-4265-983a-0e3665ef2ae4
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3da0d65917598dbbce4e203a97a9e843b5ba70c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sysprep-a-biztalk-server-vhd-biztalk-server-sample"></a>Sysprep BizTalk Server VHD （BizTalk Server 範例）
Sysprep 會從已安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的虛擬機器建立快照集，以便快速部署到其他虛擬機器上。  
  
## <a name="prerequisites"></a>必要條件  
 之前使用 Sysprep，您應該先使用虛擬機器與 HYPER-V 的一些知識。 您也應該擁有乾淨、 一般安裝中的 BizTalk Server 及所有其必要條件的虛擬機器。  
  
 Windows Server 2008 和 Windows Vista SP1 上執行 Sysprep。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 Sysprep 會建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝的 VHD (含作業系統和所有必要元件)，以便快速安裝到其他虛擬機器上。 建立使用 Sysprep 映像會選擇新的電腦名稱，才能加入網域的第一次啟動。 若要取得正確執行的 BizTalk Server，就必須更新儲存在登錄和資料庫中的電腦名稱的不同執行個體。  
  
 本文件假設 BizTalk Server 設定為在單一電腦上執行，並示範如何使用新名稱更新的電腦名稱的其他執行個體。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這個範例位於下列 SDK 位置：  
  
 \<*範例路徑*> \Admin\Sysprep\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
> [!NOTE]
>  下表中的.vbs 和.cmd 檔案自動化 Sysprep 回應檔案 （Sysprep.xml、 SetupCompletecmd.txt） 中，此處僅供參照。 如果您需要手動執行這些指令碼，它們的順序執行它們出現在資料表中。  
  
|檔案|Description|  
|----------|-----------------|  
|Sysprep.xml|回應檔案|  
|SetupCompletecmd.txt|回應檔案|  
|ReplaceMachineName.vbs|用途： 開啟檔案，並給定字串的所有執行個體，取代目前的電腦名稱。 準備其他指令碼和 xml 檔案，並更新 bm.exe.config 很有用。<br /><br /> 使用方式： ReplaceMachineName.vbs\<檔案以開啟 >\<来取代的字串 >|  
|UpdateRegistry.vbs|用途： 更新 BizTalk 登錄設定中儲存的電腦名稱。<br /><br /> 使用方式： UpdateRegistry.vbs \<UpdateInfo.xml >。 請務必取代 $(OLDCOMPUTERNAME) 和 $(NEWCOMPUTERNAME) 這個 xml 檔案中的所有執行個體。|  
|UpdateDatabase.vbs|用途： 更新儲存在 BizTalk 管理資料庫中的電腦名稱。<br /><br /> 使用方式： UpdateDatabase.vbs \<UpdateInfo.xml >|  
|UpdateBAMDb.vbs|用途： 更新儲存在 BAM 資料庫的電腦名稱。<br /><br /> 使用方式： UpdateBamDb.vbs \<UpdateInfo.xml >|  
|UpdateSSO.cmd|用途： 重新設定 「 企業單一登入 (SSO) 密碼伺服器。<br /><br /> 使用方式： sso.cmd \<UpdateInfo.xml >|  
|UpdateSqlServerAndInstanceName.cmd|用途： 重新設定 SQL，SQL Express、 重新啟動一系列相依的服務，並 reregisters BAMAlerts。<br /><br /> 使用方式： 編輯指令碼的 $(NEWCOMPUTERNAME)，所有執行個體並更新 serviceusername 和 servicepassword BAM 警示。 然後，執行 UpdateSqlServerAndInstanceName.cmd 傳遞做為第一個引數舊的電腦名稱。|  
  
## <a name="creating-the-answer-files-and-running-sysprep"></a>建立回應檔案和執行 Sysprep  
  
#### <a name="to-create-the-answer-files"></a>若要建立回應檔案  
  
1.  在新的虛擬機器上安裝並設定 [!INCLUDE[prague](../includes/prague-md.md)]。 請務必使用預設安裝和設定選項，因為 Sysprep 不支援自訂的安裝。  
  
2.  包含 「 指令碼 」 資料夾的內容複製到 C:\Scripts，虛擬機器上。  
  
3.  藉由修改下列行中 Sysprep.xml 準備 sysprep 回應檔案。 (注意： 這些線條會標記為"！" 之前。）您可以使用這些範本，或自行建立並透過複製\<FirstLogonCommands > 一節。  
  
    -   $(OLDCOMPUTERNAME) 取代目前的虛擬機器的電腦名稱。  
  
    -   使用者帳戶  
  
    -   密碼  
  
    -   UpdateSqlServerAndInstance.cmd 和您 Sysprep.xml 中也應該更新任何公司詳細資料。  
  
     或者，您可以從頭開始建立 Sysprep 回應檔案使用[自動化安裝套件 (AIK)](http://www.microsoft.com/downloads/details.aspx?FamilyID=94bb6e34-d890-4932-81a5-5b50c657de08&DisplayLang=en) Windows Server 2008 上。 請確認您\<FirstLogonCommands > 區段比對這些範例，因此 BizTalk 指令碼會執行第一次開機。  
  
#### <a name="to-run-sysprep"></a>若要執行 Sysprep  
  
1.  開啟命令提示字元，然後執行 Sysprep。 此命令看起來像這樣：  
  
    ```  
    C:\windows\system32\sysprep\sysprep.exe /oobe /generalize /shutdown /unattend:c:\scripts\unattend_Win2K8x64.xml  
    ```  
  
2.  Sysprep 執行的時間約半小時。 當完成時，它會自動關閉虛擬機器。  
  
3.  虛擬機器關機之後，會合併任何快照集，並將 VHD 檔案複製到安全的位置。  
  
4.  您的 VHD 已經準備好要部署其他的虛擬機器上完成，但作業系統、 BizTalk Server 及所有的必要條件。  
  
 **SetupCompletecmd.txt**  
  
```  
del /Q /F c:\windows\system32\sysprep\sysprep.xml  
SqlCmd -s . -d Repository -A -Q "drop login [PDC08-CSD\Administrator]"  
SqlCmd -s . -d Repository -A -Q "create login [$(COMPUTERNAME)\Administrator] from windows"  
SqlCmd -s . -d Repository -A -Q "EXEC sp_changedbowner [$(COMPUTERNAME)\Administrator]"  
  
```  
  
 **Sysprep.xml**  
  
```  
- <!--   
References:  
"Unattended Installation Settings Reference" @ http://technet.microsoft.com/library/cc749204.aspx  
"How to Sysprep in Windows 2008 " @ http://briandesmond.com/blog/how-to-sysprep-in-windows-2008  
  
Make sure to modify the values specified for the   
<Credentials> and <DomainAccounts> sections of this unattend file.  
  
SetupComplete.cmd should be copied to the C:\Windows\Setup\Scripts\ folder before running sysprep.  
Contents of SetupComplete.cmd:  
  
del /Q /F c:\windows\system32\sysprep\sysprep.xml   
SqlCmd -s . -d Repository -A -Q "drop login [PDC08-CSD\Administrator]"  
SqlCmd -s . -d Repository -A -Q "create login [$(COMPUTERNAME)\Administrator] from windows"  
SqlCmd -s . -d Repository -A -Q "EXEC sp_changedbowner [$(COMPUTERNAME)\Administrator]"  
  
Sysprep.xml (this file) should be copied to the C:\Windows\System32\sysprep\ folder.  
  
Run sysprep with the following options:  
  
sysprep /generalize /oobe /shutdown /unattend:sysprep.xml  
  -->   
  <?xml version="1.0" encoding="utf-8" ?>   
- <unattend xmlns="urn:schemas-microsoft-com:unattend">  
- <settings pass="oobeSystem">  
- <component name="Microsoft-Windows-International-Core" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <InputLocale>0409:00000409</InputLocale>   
  <SystemLocale>en-US</SystemLocale>   
  <UILanguage>en-US</UILanguage>   
  <UILanguageFallback>en-US</UILanguageFallback>   
  <UserLocale>en-US</UserLocale>   
  </component>  
- <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
- <UserAccounts>  
- <!--   
This sets the password for the Administrator account back to pass@word1   
  -->   
- <AdministratorPassword>  
  <Value>pass@word1</Value>   
  <PlainText>true</PlainText>   
  </AdministratorPassword>  
- <!--   
Enter the appropriate value for the <Name> and <Domain> elements here,   
this group/account will be added to the local Administrators and Remote Desktop Users groups.  
  -->   
- <DomainAccounts>  
- <DomainAccountList wcm:action="add">  
- <DomainAccount wcm:action="add">  
  <Name>MSMQ4TR</Name>   
  <Group>Administrators;RemoteDesktopUsers</Group>   
  </DomainAccount>  
  <Domain>Northamerica.corp.microsoft.com</Domain>   
  </DomainAccountList>  
- <!--   
Additional DomainAccountList section. Uncomment/modify this section if you need to add   
groups / users from multiple domains to the local Administrators and Remote Desktop Users groups.  
                    <DomainAccountList wcm:action="add">  
                        <DomainAccount wcm:action="add">  
                            <Name>OsloVM_NTDev</Name>  
                            <Group>Administrators;RemoteDesktopUsers</Group>  
                        </DomainAccount>  
                        <Domain>Ntdev.corp.microsoft.com</Domain>  
                    </DomainAccountList>  
  -->   
  </DomainAccounts>  
  </UserAccounts>  
- <!--   
The new computer name is generated using a combination of <RegisteredOwner>, <RegisteredOrganization>, and random alphanumeric characters. Since <RegisteredOrganization> is blank, the new computer name will be OsloVPC-*******.  
  -->   
  <RegisteredOwner>OsloVPC</RegisteredOwner>   
  <TimeZone>Pacific Standard Time</TimeZone>   
- <Display>  
  <ColorDepth>16</ColorDepth>   
  <HorizontalResolution>1024</HorizontalResolution>   
  <VerticalResolution>768</VerticalResolution>   
  </Display>  
  <RegisteredOrganization />   
  <StartPanelOff>true</StartPanelOff>   
  <ShowWindowsLive>false</ShowWindowsLive>   
  <DoNotCleanTaskBar>true</DoNotCleanTaskBar>   
  <DisableAutoDaylightTimeSet>false</DisableAutoDaylightTimeSet>   
  <BluetoothTaskbarIconEnabled>false</BluetoothTaskbarIconEnabled>   
- <VisualEffects>  
  <FontSmoothing>ClearType</FontSmoothing>   
  </VisualEffects>  
  </component>  
  </settings>  
- <settings pass="specialize">  
- <component name="Microsoft-Windows-IE-ESC" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <IEHardenAdmin>false</IEHardenAdmin>   
  <IEHardenUser>false</IEHardenUser>   
  </component>  
- <component name="Microsoft-Windows-UnattendedJoin" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
- <!--   
Enter credentials for a user account that has permissions to join a computer to the domain specified in the <JoinDomain> element. (Note: you must enter your password in plaintext here. This file will be deleted at the conclusion of Windows setup by SetupComplete.cmd in the C:\Windows\Setup\Scripts\ folder. For more information see the bottom of "How to Sysprep in Windows 2008" @ http://briandesmond.com/blog/how-to-sysprep-in-windows-2008)  
  -->   
- <Identification>  
- <Credentials>  
  <Domain>northamerica</Domain>   
  <Username>davidhamilton</Username>   
  <Password>******</Password>   
  </Credentials>  
  <JoinDomain>Redmond.corp.microsoft.com</JoinDomain>   
  </Identification>  
  </component>  
- <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
- <!--   
By specifying a value of "*" for <ComputerName>, Windows setup will generate a new computer name using a combination of <RegisteredOwner>, <RegisteredOrganization>, and random alphanumeric characters. Since <RegisteredOrganization> is blank, the new computer name will be OsloVPC-*******  
  -->   
  <ComputerName>*</ComputerName>   
  <RegisteredOrganization />   
- <!--   
The new computer name is generated using a combination of <RegisteredOwner>, <RegisteredOrganization>, and random alphanumeric characters. Since <RegisteredOrganization> is blank, the new computer name will be OsloVPC-*******.   
  -->   
  <RegisteredOwner>OsloVPC</RegisteredOwner>   
  <ShowWindowsLive>false</ShowWindowsLive>   
  <BluetoothTaskbarIconEnabled>false</BluetoothTaskbarIconEnabled>   
- <!--   
This setting will copy the profile of the original image to the renamed image when set to true   
  -->   
  <CopyProfile>true</CopyProfile>   
  <DisableAutoDaylightTimeSet>false</DisableAutoDaylightTimeSet>   
  <DoNotCleanTaskBar>true</DoNotCleanTaskBar>   
  </component>  
  </settings>  
- <settings pass="generalize">  
- <component name="Microsoft-Windows-Security-Licensing-SLC" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <SkipRearm>1</SkipRearm>   
  </component>  
- <component name="Microsoft-Windows-OutOfBoxExperience" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <DoNotOpenInitialConfigurationTasksAtLogon>true</DoNotOpenInitialConfigurationTasksAtLogon>   
  </component>  
- <component name="Microsoft-Windows-ServerManager-SvrMgrNc" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <DoNotOpenServerManagerAtLogon>true</DoNotOpenServerManagerAtLogon>   
  </component>  
  </settings>  
  <cpi:offlineImage cpi:source="catalog:e:/sources/install_windows longhorn serverenterprise.clg" xmlns:cpi="urn:schemas-microsoft-com:cpi" />   
  </unattend>  
- <!--   
When the virtual machine is started, Windows setup will:  
  
 - Assign the copy a random computer name: "OsloVPC-*****"  
 - Reset the local Administrators password to pass@word1  
 - Join the domain specified in the sysprep.xml file (under Microsoft-Windows-UnattendedJoin\Identification\JoinDomain)  
 - Add the groups/users specified under <DomainAccounts> to the local Administrators and the local Remote Desktop Users group.  
  
Known issues:  
  
 - Sysprep removes the Server Manager icon from the Quick Launch toolbar, investigating how to prevent this.  
 - To start SQL Server Management Studio, either connect to the new server name (OsloVPC-*******) or else connect to ".".  The "Server name:" drop-down box in SQL Server Management Studio is pre-populated with "PDC08-CSD" which will not work since the computer name has been changed by sysprep.  
 - There are some known issues associated with changing the computer name; renaming the computer after everything was installed was not a design, development or test requirement for this milestone.  
  -->  
```  
  
## <a name="comments"></a>註解  
 這些指令碼不會修改 Microsoft Office SharePoint Server。 如果您使用 Windows SharePoint Services 配接器，您可能必須重新設定 Microsoft Office SharePoint Server，然後更新 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\ SharePointAdapterManagementGroup 機碼TPM。