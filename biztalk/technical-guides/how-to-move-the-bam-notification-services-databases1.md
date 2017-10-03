---
title: "如何移動 BAM Notification Services Databases1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89b4938e-ea4a-48d3-80c3-eb9401e28323
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a5f643d764790b37deaab445290f1230c9ed8ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-notification-services-databases"></a>如何移動 BAM Notification Services 資料庫
您可以使用此程序將 BAM Notification Services 資料庫移動到另一部伺服器。  端對端案例的觀點而言，移動 BAM Notification Services 資料庫包含兩個主要步驟：  
  
-   [移動 BAM Notification Services 資料庫](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiMoveDB)  
  
-   [更新參考新的 BAM notification Services 資料庫](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdate)  
  
> [!NOTE]  
>  您必須移動 BAM Notification Services 應用程式 (BAMAlertsApplication) 資料庫和 BAM Notification Services 執行個體 (BAMAlertsNSMain) 資料庫在一起。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。  
  
##  <a name="BKMK_NotiMoveDB"></a>移動 BAM Notification Services 資料庫  
 執行下列程序移動 BAM Notification Services 資料庫中的步驟。  
  
#### <a name="to-move-the-bam-notification-services-database"></a>若要移動 BAM Notification Services 資料庫  
  
1.  停止任何 BAM cube 更新及資料維護 SSIS 封裝，或防止它們執行，直到您完成 BAM Notification Services 資料庫的還原。  
  
2.  停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。 如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](http://go.microsoft.com/fwlink/?LinkId=154394)(http://go.microsoft.com/fwlink/?LinkId=154394) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
3.  停止 IIS 服務。  
  
4.  停止 BAM 警示 Notification service:  
  
    1.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
    2.  在命令提示字元中，輸入：  
  
         **Net stop NS$ BamAlerts**  
  
5.  在舊伺服器上備份 BAM Notification Services 資料庫。 如需有關備份資料庫的指示，請遵循指示[如何： 備份資料庫 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何備份資料庫。  
  
    > [!NOTE]  
    >  BAMAlertsApplication 和 BAMAlertsNSMain 資料庫執行此步驟。  
  
6.  將 BAM Notification Services 資料庫複製到新[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
7.  BAM Notification Services 資料庫，新的伺服器上還原。 如需在還原資料庫的指示，請遵循的指示[如何： 還原資料庫備份 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何還原資料庫。  
  
    > [!NOTE]  
    >  BAMAlertsApplication 和 BAMAlertsNSMain 資料庫執行此步驟。  
  
##  <a name="BKMK_NotiUpdate"></a>更新參考新的 BAM notification Services 資料庫  
 移動資料庫之後，您必須更新 BAM Notification Services 資料庫的所有參考。 必須更新下列參考：  
  
-   以新的資料庫和伺服器名稱更新 BAM 組態。 請參閱[更新 BAM 組態](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdateBAMConfig)。  
  
-   重新註冊 Notification Service 中的所有電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 請參閱[註冊 Notification Services](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiRegister)。  
  
###  <a name="BKMK_NotiUpdateBAMConfig"></a>若要更新 BAM 組態  
  
1.  取得用來還原 BAM 的 .xml 檔案複本：  
  
    1.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
    2.  在執行 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 的電腦中，瀏覽至下列資料夾：  
  
        -   如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:  
  
             **%Programfiles (x86) %\Microsoft BizTalk Server 2010 \tracking**  
  
        -   如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:  
  
             **%ProgramFiles%\Microsoft BizTalk Server 2010 \tracking**  
  
    3.  在命令提示字元中，輸入：  
  
         **Bm.exe get-config –filename:BAMConfiguration.xml-server:\<伺服器名稱 >-資料庫：\<資料庫 >**  
  
        > [!NOTE]  
        >  當執行此命令，以取代要取得組態資訊的來源伺服器的實際名稱<servername>，並以要從中取得組態資訊的資料庫的實際名稱取代<database>。 如需有關如何使用 BAM 管理 (BM) 公用程式的詳細資訊，請參閱[基礎結構管理命令](http://go.microsoft.com/fwlink/?LinkId=156516)(http://go.microsoft.com/fwlink/?LinkId=156516) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
2.  編輯 BAMConfiguration.xml 檔案，並變更**DBServer**中的屬性`<DeploymentUnit Name="Alert">`區段，以新的伺服器名稱。  
  
3.  儲存並關閉 BAMConfiguration.xml 檔案。  
  
4.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
5.  在執行 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 的電腦中，瀏覽至下列資料夾：  
  
    -   如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:  
  
         **%Programfiles (x86) %\Microsoft BizTalk Server 2010 \tracking**  
  
    -   如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:  
  
         **%ProgramFiles%\Microsoft BizTalk Server 2010 \tracking**  
  
6.  在命令提示字元中，輸入：  
  
     **bm.exe 更新-config-FileName:BAMConfiguration.xml**  
  
###  <a name="BKMK_NotiRegister"></a>註冊 Notification Services  
 移動 BAM Notification Services 資料庫之後，您必須重新註冊 Notification Service，BizTalk Server 群組中執行 Notification Services (NSservice.exe) 的所有電腦上。 這樣可以讓 Notification Services 連線至其位於新位置的資料庫。 如需有關如何註冊 Notification Services 的指示，請依照下列步驟 5 至 11[如何更新 BAM Notification Services 資料庫參考](http://go.microsoft.com/fwlink/?LinkId=156684)(http://go.microsoft.com/fwlink/?LinkId=156684) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
 下列執行上述的連結中所述的步驟時的注意事項：  
  
-   步驟 5 和 6 先前連結中的必須對下列屬性的 BAM 組態 XML 中列出的伺服器：  
  
    ```  
    <DeploymentUnit Name="Alert">  
      <Property Name="GeneratorServerName">Server_Name</Property>  
      <Property Name="ProviderServerName">Server_Name</Property>  
      <Property Name="DistributorServerName">Server_Name</Property>  
    </DeploymentUnit>  
  
    ```  
  
-   必須在裝載 BAM 入口網站的電腦上執行步驟 7 到 11。  
  
## <a name="see-also"></a>另請參閱  
 [移動資料庫](../technical-guides/moving-databases.md)