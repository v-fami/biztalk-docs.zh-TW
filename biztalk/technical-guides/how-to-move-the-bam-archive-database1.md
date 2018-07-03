---
title: 如何移動 BAM 封存 Database1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e371321c-6b8d-4be6-a6d2-926f6218db01
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84dda0937fc0c7b060e483b2ca1585a3d5160ad1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023404"
---
# <a name="how-to-move-the-bam-archive-database"></a>如何移動 BAM 封存資料庫
您可以使用這個程序，將 BAM 封存資料庫移動到其他伺服器。  端對端案例的觀點而言，移動 BAM 封存資料庫，將牽涉到兩個主要步驟：  
  
-   [移動 BAM 封存資料庫](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_MovingArch)  
  
-   [更新至新的 BAM 封存資料庫的參考](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArch)  
  
## <a name="prerequisites"></a>必要條件  
 您必須以成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。  
  
##  <a name="BKMK_MovingArch"></a> 移動 BAM 封存資料庫  
 執行下列程序移動 BAM 封存資料庫中的步驟。  
  
#### <a name="to-move-the-bam-archive-database"></a>移動 BAM 封存資料庫  
  
1. 停止任何 BAM cube 更新和資料維護 SSIS 封裝，或防止它們執行，直到您還原 BAM 封存資料庫。  
  
2. 停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。 如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
3. 停止 IIS 服務。  
  
4. 停止 BAM 警示 Notification service:  
  
   1.  按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
   2.  在命令提示字元中，輸入：  
  
        **net stop NS$ BamAlerts**  
  
5. 在舊伺服器上備份 BAM 封存資料庫。 如需有關備份資料庫的指示，請遵循指示[如何： 備份資料庫 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (<http://go.microsoft.com/fwlink/?LinkId=156510>) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何備份資料庫。  
  
6. 將 BAM 封存資料庫複製到新[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
7. BAM 封存資料庫，新的伺服器上還原。 如需還原資料庫的指示，請遵循指示[如何： 還原資料庫備份 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (<http://go.microsoft.com/fwlink/?LinkId=156511>) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何還原資料庫。  
  
##  <a name="BKMK_UpdateArch"></a> 更新至新的 BAM 封存資料庫的參考  
 移動資料庫之後，您必須更新至新的 BAM 封存資料庫的所有參考。 必須更新下列參考：  
  
-   使用新的資料庫和伺服器名稱更新 BAM 組態。 請參閱[若要更新 BAM 組態](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArchConfig)。  
  
-   更新所有 BAM 分析 SSIS 封裝中新的伺服器和資料庫名稱。 請參閱[來更新伺服器和資料庫名稱在所有 BAM SSIS 套件](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArchSSIS)。  
  
###  <a name="BKMK_UpdateArchConfig"></a> 若要更新 BAM 組態  
  
1. 取得用來還原 BAM 的 .xml 檔案複本：  
  
   1. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
   2. 在執行 BizTalk Server 的電腦，瀏覽至下列資料夾：  
  
      - 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:  
  
         **%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**  
  
      - 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:  
  
         **%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**  
  
   3. 在命令提示字元中，輸入：  
  
       **Bm.exe 取得設定 –filename:BAMConfiguration.xml-server:\<servername\> -資料庫：\<資料庫\>**  
  
      > [!NOTE]
      >  執行此命令時，替代伺服器，以取得組態資訊的實際名稱\<servername\> ，並以要從中取得組態資訊的資料庫的實際名稱取代\<資料庫\>。 如需使用 BAM 管理 (BM) 公用程式的詳細資訊，請參閱[基礎結構管理命令](http://go.microsoft.com/fwlink/?LinkId=156516)(<http://go.microsoft.com/fwlink/?LinkId=156516>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
2. 編輯 BAMConfiguration.xml 檔案，並變更**ServerName**在`<DeploymentUnit Name="ArchivingDatabase">`一節，以新的伺服器名稱。  
  
3. 儲存並關閉 BAMConfiguration.xml 檔案。  
  
4. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
5. 在執行 BizTalk Server 的電腦，瀏覽至下列資料夾：  
  
   - 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:  
  
      **%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**  
  
   - 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:  
  
      **%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**  
  
6. 在命令提示字元中，輸入：  
  
    **bm.exe update-config -FileName:BAMConfiguration.xml**  
  
###  <a name="BKMK_UpdateArchSSIS"></a> 若要更新伺服器和資料庫名稱在所有 BAM SSIS 套件  
  
1. 更新所有 BAM 分析 SSIS 封裝中，會加上"bam_dm_"作為伺服器和資料庫名稱。 若要這樣做，請按一下**開始**，按一下**所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下**SQL Server Business Intelligence Development Studio**。  
  
2. 在 SQL Server Business Intelligence Development Studio 中建立新專案。 按一下 **檔案**，按一下**新增**，然後按一下**專案**。  
  
3. 在 **新的專案**對話方塊中，於**專案類型**方塊中，按一下**商業智慧專案**。 在右窗格中，在**範本**方塊中，按一下**Integration Services 專案**，然後按一下**確定**。  
  
4. 在**Integration Services 專案**對話方塊中，在 [方案總管] 中，以滑鼠右鍵按一下**SSIS 封裝**，然後按一下**加入現有封裝**。  
  
5. 在 **加入現有封裝的副本**對話方塊中，於**Server**下拉式清單方塊中，選取包含 BAM_DM_ * 封裝的伺服器。  
  
6. 在 **封裝路徑**，按一下省略符號按鈕。  
  
7. 在  **SSIS 封裝**對話方塊方塊中，選取您想要更新，請按一下 的套件**確定**，然後按一下  **確定**。  
  
    封裝現在會在 [方案總管] 中列出。  
  
8. 在 [方案總管] 中，按兩下您在上一個步驟中新增的套件。 在 **連接管理員**索引標籤上 （朝向螢幕的下半部提供） 中，按兩下資料來源數字 2 （BAMArchive 資料庫）。  
  
9. 在 **連接管理員**對話方塊中，於**伺服器名稱**方塊，輸入伺服器名稱，然後按一下**確定**。  
  
    > [!NOTE]  
    >  重複此步驟的資料來源數字 3 （MSDB 資料庫）。  
  
10. 按一下 **套件總管**索引標籤上，按兩下**變數**資料夾，然後更新的值**ArchivingDatabase**， **ArchivingServer**， **PrimaryImportDatabase**，以及**PrimaryImportServer**變數。 您必須更新為指向新的伺服器與資料庫的值。  
  
    > [!NOTE]  
    >  針對您想要更新的所有封裝重複步驟 4 到 10。  
  
11. 然後按一下**檔案**功能表，然後再按一下**全部儲存**。  
  
12. 啟動 SQL Server Management Studio。 按一下 **開始**，按一下**所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下**SQL Server Management Studio**。  
  
13. 在 [**連接到伺服器**] 對話方塊中，從**伺服器**類型下拉式清單中，選取**Integration Services**。  
  
14. 指定伺服器名稱和認證以連接至伺服器，然後按一下**確定**。  
  
15. 在 **物件總管 中**，展開**Integration Services**，展開**存放的封裝**，然後按一下  **MSDB**。  
  
16. 在 **物件總管詳細資料**索引標籤上，以滑鼠右鍵按一下您在稍早所更新的封裝，然後按一下**匯入封裝**。  
  
17. 在 [**匯入封裝**] 對話方塊中，從**封裝位置**下拉式清單中，選取**檔案系統**。  
  
18. 在 **封裝路徑**、 瀏覽至您儲存的專案中，選取您要匯入，然後按一下 的封裝.dtsx 檔案**開啟**。  
  
19. 按一下以自動填入  方塊中的 封裝名稱 方塊內。  
  
    > [!NOTE]  
    >  針對您想要更新的所有封裝重複步驟 16 到 19。  
  
20. 按一下  **確定**，然後按一下**是**覆寫。  
  
21. 啟動所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。 如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
22. 啟動 IIS 服務。  
  
23. 啟動 BAM 警示 Notification service:  
  
    1.  按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
    2.  在命令提示字元中，輸入：  
  
         **Net start NS$ BamAlerts**  
  
24. 啟用任何 BAM Cube 更新和資料維護 SSIS 封裝。  
  
> [!TIP]  
>  好的做法是，您也應該移動 BAM_DM_ * SSIS 封裝至裝載 BAMArchive 資料庫的伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [移動資料庫](../technical-guides/moving-databases.md)