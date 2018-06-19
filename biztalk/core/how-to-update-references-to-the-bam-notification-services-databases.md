---
title: 如何更新參考 BAM Notification Services 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Notification Services Application database [BAM], restoring
- Notification Services Application database [BAM], updating references
- restoring, BAM
- NS$instance_name service Notification Services Application database [BAM], NS$instance_name service
- restoring [BAM], updating references
- BAM, restoring
- restoring [BAM], Notification Services Application database
- restoring [BAM], NS$instance_name service
ms.assetid: b007fdc2-2e74-4eef-b4c3-43689e9f2180
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c27f1ecaf07c3f953372a9e5733d62c8376a288f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972997"
---
# <a name="how-to-update-references-to-the-bam-notification-services-databases"></a>如何更新 BAM Notification Services 資料庫的參考
執行將「商務活動監控」(BAM) 的 Notification Services 資料庫還原至目的地系統的必要步驟之後，您必須在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組中執行 Notification Services (NSservice.exe) 的所有電腦上重新註冊 Notification Service。 這樣可以讓 Notification Services 連線至其位於新位置的資料庫。  
  
 註冊 Notification Services 的執行個體會建立 NS$instance_name 服務、在本機伺服器建立效能計數器，以及在登錄中新增資訊。 您必須在下列伺服器上註冊執行個體：  
  
-   每個執行 NS$instance_name 服務的伺服器。 執行事件提供者主控件、產生器和散發者元件的服務。 在向外擴充的組態中，在多部伺服器上執行的服務。  
  
-   每個執行訂閱管理應用程式的伺服器。 如果訂閱管理應用程式是在自己的伺服器上執行，請不要在註冊執行個體時建立 NS$instance_name 服務。  
  
-   每個執行獨立事件提供者的伺服器。 如果獨立事件提供者是在自己的伺服器或資料庫伺服器上執行，請不要在註冊執行個體時建立 NS$instance_name 服務。  
  
 如果資料庫伺服器也沒有執行 Notification Services 執行個體或用戶端元件，請不要在此伺服器註冊執行個體。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須以「系統管理員」群組成員的身分登入，才能執行此程序。  
  
-   在您要還原 BAM Notification Services 資料庫的電腦上，必須安裝 BAM Alert Provider for SQL Notification Services。  
  
### <a name="to-update-references-to-the-bam-notification-services-databases-sql-server-2008-r2sp1"></a>若要更新 BAM Notification Services 資料庫的參考 (SQL Server 2008 R2/SP1)  
  
1.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
2.  在命令提示字元中，瀏覽至下列目錄：[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3.  類型： **bm.exe get-config**  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
4.  開啟步驟 2 建立的 XML 檔案以取得您必須在其中重新註冊 Notification Services 的電腦的清單。  
  
     電腦名稱會列在**\<屬性名稱\=\>** 中的參數 **\<DeploymentUnit 名稱 = 警示\>** xml 檔案的區段：  
  
    ```  
    -<DeploymentUnit Name="Alert">  
    <Property Name="GeneratorServerName" />  
    <Property Name="ProviderServerName" />  
    <Property Name="DistributorServerName" />  
      </DeploymentUnit>  
    ```  
  
5.  在 XML 檔案所列出的每台電腦上，停止 NS 服務，然後取消註冊 Notification Services 的執行個體：  
  
    1.  按一下**啟動**，按一下 **程式**，按一下  **Microsoft SQL Server 2008 R2**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**。  
  
    2.  在命令提示字元中，輸入： **net stop NS$ BamAlerts**  
  
    3.  輸入下列命令取消註冊執行個體：  
  
         **nscontrol unregister-name BamAlerts**  
  
         取消註冊執行個體會移除登錄項目、移除 NS$instance_name 服務 (如果有)，並刪除服務的效能計數器。  
  
6.  重新註冊 Notification Services：  
  
    1.  按一下**啟動**，按一下 **程式**，按一下  **Microsoft SQL Server 2008 R2**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**。  
  
    2.  在命令提示字元中，輸入： **nscontrol register-name BamAlerts-server**  *\<ServerName\>***-服務-serviceusername"** *\<ServiceUserName\>***"-servicepassword"***\<ServicePassword\>***"**  
  
         這樣可以讓 Notification Services 登入正確的資料庫 (這項資訊是在服務電腦的登錄中由 nscontrol 執行維護)。  
  
        > [!IMPORTANT]
        >  請記得使用新的 Notification Services 資料庫伺服器中 **-伺服器**選項重新註冊服務時。 此外，您也應該將新的 Notification Services 服務的使用者名稱，保持與舊服務的使用者名稱一致。  
  
7.  在裝載 BAM 入口網站的電腦，按一下 **啟動**，按一下 **程式**，按一下**Microsoft SQL Server 2008 R2**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**。  
  
8.  在命令提示字元中，輸入：  
  
     **net stop NS$ BamAlerts**  
  
9. 在命令提示字元中，輸入：  
  
     **nscontrol unregister-name BamAlerts**  
  
10. 在命令提示字元中，輸入：  
  
     **nscontrol register-name***\<BamAlerts\>***-伺服器**  *\<NotificationServicesDatabaseServer    \>*  
  
11. 在命令提示字元中，輸入： **net start NS$ BamAlerts**。  
  
12. 按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
13. 在命令提示字元中，瀏覽至下列目錄：[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
14. 在命令提示字元中，輸入：  
  
     **bm.exe 更新-config –FileName:config.xml**  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [備份和還原 BAM](../core/backing-up-and-restoring-bam.md)