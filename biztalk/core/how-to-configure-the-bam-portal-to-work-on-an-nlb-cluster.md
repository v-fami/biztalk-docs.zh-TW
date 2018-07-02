---
title: 如何在 NLB 叢集上設定 BAM 入口網站 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96c04fde-dc12-42fb-9193-aa74819fe880
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adc423fc74cd504f79a1106d196868df20faf974
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994463"
---
# <a name="how-to-configure-the-bam-portal-to-work-on-an-nlb-cluster"></a>如何設定 BAM 入口網站在 NLB 叢集上執行
BAM 入口網站可設定為在網路負載平衡 (NLB) 叢集中使用。  
  
> [!IMPORTANT]
>  BAM 入口網站*只*在 32 位元模式下執行。 如果在 64 位元電腦上安裝 IIS，請確定在 32 位元模式下啟用 ASP.NET 2.0。 若要這樣做，請開啟 IIS 管理員 中，開啟**應用程式集區**，選取 應用程式集區 (BAMAppPool)，然後按一下 **進階設定**。 在 [啟用 32 位元應用程式] 中，選取 [True]。  
>   
>  如需其他 BAM 入口網站的需求，請參閱[規劃 BAM 入口網站](../core/planning-for-the-bam-portal.md)。  
  
### <a name="to-prepare-to-configure-bam-portal-on-an-nlb-cluster"></a>準備在 NLB 叢集上設定 BAM 入口網站  
  
1.  在第一台電腦上安裝並設定入口網站。  
  
    > [!NOTE]
    >  您只可在第一台電腦上設定入口網站。 您可選擇在叢集中的其他電腦上啟用 BAM 入口網站，但只能在第一台電腦上進行設定。  
  
2.  將入口網站元件安裝在要包含在 NLB 叢集中的所有電腦上，然後將叢集中的其他電腦加入要設定入口網站之電腦的 BizTalk 群組。 您必須啟用 BizTalk 群組，並加入適當的群組。  
  
3.  選取為安裝入口網站之電腦所設定的 BizTalk 管理資料庫。  
  
4.  建立 NLB 叢集。 如何建立和管理網路負載平衡叢集的詳細資訊，請參閱 「 建立和管理網路負載平衡叢集 >，網址[ http://go.microsoft.com/fwlink/?LinkId=56206 ](http://go.microsoft.com/fwlink/?LinkId=56206)。  
  
    > [!NOTE]
    >  在繼續進行之前，您應確定 NLB 叢集在 BizTalk Server 環境之外運作良好。  
  
    > [!NOTE]
    >  若要設定硬體式 NLB，請參閱硬體供應商的文件。  
  
### <a name="to-update-the-bam-configuration-to-reflect-the-location-of-the-cluster"></a>更新 BAM 組態以反映叢集位置  
  
1. 如何使用 BAM 管理公用程式取得目前的 BAM 組態 若要這樣做，請按一下 **開始**，按一下**執行**，然後輸入[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm get-config-filename: Myconfig.xml。  
  
2. 使用 NLB 叢集的名稱取代本機主機名稱。 若要這樣做，請按一下**開始**，按一下**執行**，然後輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\MyConfig.xml。  
  
3. (僅限硬體式 NLB) 確認組態檔含有下列項目：  
  
   ```  
   <GlobalProperty Name="BAMVRoot">  
   http://<NLB IP Address>:portname/BAM</GlobalProperty>  
   ```  
  
   > [!NOTE]
   >  在硬體式 NLB 上更新 BAM 組態時，不需要執行步驟 4 和 5。  
  
4. 使用叢集名稱取代電腦名稱 (machinename)，藉以修改下列行以指向 NLB 叢集：  
  
   ```  
   <GlobalProperty Name=" BAMVRoot">  http://machinename:portname/BAM  
   </GlobalProperty>   
   ```  
  
5. 儲存新組態。 若要這樣做，請按一下 **開始**，按一下**執行**，然後輸入[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm 更新-config-filename: Myconfig.xml。  
  
### <a name="to-edit-the-bam-portal-webconfig-file-to-change-the-bammanagementservice-and-queryservice-urls-to-point-to-the-nlb-server-name-note-this-procedure-is-not-necessary-for-hardware-based-nlb"></a>編輯 BAM 入口網站的 web.config 檔案，將 BAMmanagementService 和 QueryService 的 URL 變更為指向 NLB 伺服器名稱。 注意： 此程序不需要硬體式 nlb。  
  
1. 開啟 web.config 檔案，使用 [記事本]，依序按一下**開始**，再按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config，，然後按一下**確定**。  
  
2. 修改下列兩行中的電腦名稱 (machinename) 和連接埠名稱，使其指向叢集的名稱：  
  
   ```  
   <add key="BamQueryWSUrl" value="http://machinename:portname /BAM/BAMQueryService/BamQueryService.asmx" />  
   <add key="BamManagementWSUrl" value=" http://machinename:portname/BAM/BAMManagementService/BamManagementService.asmx" />   
   ```  
  
3. 儲存檔案。 若要這樣做，請按一下**檔案**，然後按一下**儲存**[記事本] 功能表列上。  
  
### <a name="to-configure-each-additional-computer-in-the-cluster"></a>設定叢集中的其他電腦  
  
1. 將 web.config 檔案複製到叢集中其他每台電腦上的 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal 資料夾。  
  
   > [!NOTE]
   >  在下列步驟中的所有參考**Program Files**資料夾將會是**Program Files (x86)** 64 位元電腦。  
   > 
   > [!IMPORTANT]
   >  在下列步驟中，當您建立虛擬目錄時，請檢查並確定其設定與第一台電腦上 BizTalk Server 組態所建立的三個 BAM 虛擬目錄完全相同。 請確認您的檔案路徑、ASP.NET 版本、目錄權限以及應用程式集區。  請使用與您設定第一台電腦時所使用的相同網域服務帳戶，在您正在設定的電腦上執行 BAMAppPool。 請確定 BAMAppPool 在所有的電腦上執行。 有兩個 web.config 檔案您必須複製。  
   > 
   >  除了 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal 中的 web.config 檔案以外，您還必須將 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService 與 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMQueryService 中的 web.config 檔案複製到這部電腦上的相同資料夾。  
  
2. (僅限硬體式 NLB) 修改下列兩行中的電腦名稱 (machinename) 和連接埠名稱，使其指向叢集的名稱：  
  
   ```  
   <add key="BamQueryWSUrl" value="http://machinename:portname /BAM/BAMQueryService/BamQueryService.asmx" />  
   <add key="BamManagementWSUrl" value=" http://machinename:portname/BAM/BAMManagementService/BamManagementService.asmx" />  
   ```  
  
3. 建立名為 BAMAppPool 的應用程式集區。  
  
   > [!NOTE]
   >  虛擬目錄的目錄路徑應為 %InstallationFolder%/BamPortal、%InstallationFolder%/BamPortal/BAMManagementService 及 %InstallationFolder%/BamPortal/BAMQueryService。  
  
4. 在名為 BAM 的預設網站下建立虛擬目錄。  
  
5. 將 BAM 虛擬目錄的應用程式集區變更為 BAMAppPool。  
  
   > [!NOTE]
   >  虛擬目錄的目錄路徑應為 %InstallationFolder%/BamPortal、%InstallationFolder%/BamPortal/BAMManagementService 及 %InstallationFolder%/BamPortal/BAMQueryService。  
  
6. 在 BAM 下建立名為 BAMManagementService 的虛擬目錄。  
  
7. 將 BAMManagementService 的應用程式集區變更為 BAMAppPool。  
  
   > [!NOTE]
   >  虛擬目錄的目錄路徑應為 %InstallationFolder%/BamPortal、%InstallationFolder%/BamPortal/BAMManagementService 及 %InstallationFolder%/BamPortal/BAMQueryService。  
  
8. 在 BAM 下建立名為 BAMQueryService 的虛擬目錄。  
  
9. 將 BAMQueryService 的應用程式集區變更為 BAMAppPool。  
  
10. 使用位於虛擬目錄屬性 ASP NET 索引標籤的 INETMGR 變更 BAM、BAMMANAGEMENTSERVICE 和 BAMQUERYSERVICE 的版本，以設定應用程式版本為 .NET Framework 4。  
  
11. Run aspnet_setreg.exe -k:"SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\identity" -u:BAMWebServiceAccount  -p:Password。  這裡所指定的帳戶為 BAM 管理 Web 服務使用者帳戶。  
  
    > [!CAUTION]
    >  BAM 入口網站*只*在 32 位元模式下執行。 如果在 64 位元電腦上安裝 IIS，必須在 32 位元模式下啟用 ASP.NET 2.0。 若要這樣做，請開啟 IIS 管理員 中，開啟**應用程式集區**，選取 應用程式集區 (BAMAppPool)，然後按一下 **進階設定**。 在 [啟用 32 位元應用程式] 中，選取 [True]。  
    >   
    >  [規劃 BAM 入口網站](../core/planning-for-the-bam-portal.md)列出其他需求。  
  
12. 執行 SubInACL，此命令列工具可以讓系統管理員取得檔案、登錄機碼和服務的安全性資訊，並且在使用者間、本機或全域群組間以及網域間傳輸此資訊，以便在 WebServices 上設定 AppPool 的讀取 ACL。  
  
13. 下載的 SubInAcl [ http://go.microsoft.com/fwlink/?LinkId=61990 ](http://go.microsoft.com/fwlink/?LinkId=61990)。  
  
14. 開啟命令提示字元。 若要這樣做，請按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
15. 在命令提示字元輸入下列命令： subinacl.exe /subkeyreg"HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices 」"/ 授與 = Network Service = R"  
  
    > [!NOTE]
    >  此命令的目的是要授與 BAM 應用程式集區使用者讀取 SOFTWAREMicrosoftBizTalk Server3.0BAMWebServicesidentity 登錄機碼。 此範例使用網路服務，因為這是 IIS 使用的應用程式集區預設值。 如果您未使用預設的 IIS 設定，則應該取代部署使用的應用程式集區使用者。  
  
16. 在命令提示字元輸入下列命令： subinacl.exe /keyreg"[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk server\3.0] 」"/ 授與 =\<BAM web 服務帳戶\>"  
  
    > [!NOTE]
    >  這個命令的目的，是要授與 BAM 管理 Web 服務使用者帳戶讀取 SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\Identity 登錄機碼的權限。  
  
17. 確認用來執行 BAMManagement Web 服務的識別身分具有 ASPNET_SETREG 機碼的存取權。  
  
18. 請使用電腦管理系統管理員工具，將 BAM 管理 Web 服務使用者及 BAM 應用程式集區使用者帳戶新增至 IIS 工作者處理序群組 (IIS_WPG) 及 SharePoint 服務群組 (STS_WPG)。  
  
19. 設定應用程式集區和 Web 服務使用者的暫存 ASP.NET 資料夾的權限： c:\windows\system32\cacls"%windir%\Microsoft.NET\Framework\ v2.0。\<最小版本號碼\>\Temporary ASP.NET Files"/T /E /G \<BAM web 服務帳戶\>: F  
  
    > [!NOTE]
    >  您會同時授與 BAM 管理 Web 服務使用者帳戶及 BAM 應用程式集區使用者帳戶的存取權。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 入口網站](../core/managing-the-bam-portal.md)