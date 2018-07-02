---
title: 匯入或匯出 BizTalk 設定使用設定儀表板 |Microsoft Docs
description: 使用 BizTalk Server 管理匯入或匯出 BizTalk Server 環境之間的設定
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc2f0b44-d79b-4f95-811a-0843e3d6d1c8
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3713ee7906d735b6328b50d3b97a214422893d21
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970215"
---
# <a name="use-settings-dashboard-to-import-or-export-biztalk-settings"></a>使用設定儀表板匯入或匯出 BizTalk 設定 

## <a name="overview"></a>概觀
您可以使用 BizTalk 設定儀表板，匯出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中的設定，再將設定匯入到其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境，進而縮短完成解決方案所需的整體時間。 當系統管理員會試著在臨時環境中調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 效能，並會在達成想要的結果時將設定匯入實際執行環境的情況下，這種方式就特別有用。 本主題將提供使用 [設定儀表板] 匯入 BizTalk 群組、主控件和主控件執行個體設定的逐步程序。  

> [!TIP]
> BTSTask 命令列公用程式也可以使用匯入或匯出工作群組、 主控件和主控件執行個體設定。 請參閱[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。

  
## <a name="prerequisites"></a>必要條件  
 若要執行這項作業，您必須為 BizTalk Server 系統管理員群組的成員登入。  
  
## <a name="import-the-biztalk-group-host-and-host-instance-settings"></a>匯入 BizTalk 群組、 主機和主機執行個體設定  

> [!IMPORTANT]
>  若要從某個環境匯入 BizTalk Server 設定，您應該已經將這些設定儲存並匯出成 XML 檔案。 **匯出 BizTalk 設定**（在本主題中） 或[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)可以幫助。
  
 透過匯入 XML 檔案，您可以將必要的 BizTalk Server 設定複製到目標電腦上。 您可以使用 [設定] 儀表板，匯入群組、主控件和主控件執行個體設定，並且將屬性相互對應。 以下是匯入設定的必要假設：  
  
-   來源環境與目的環境的 BizTalk Server 拓撲是一致的。  
  
-   來源環境和目的環境的主控件定義可相互對應。 您應該要能夠將來源環境中的所有主控件與目的環境中的主控件相互對應。  
  
-   目的環境與來源環境有相似的硬體 (如果不完全相同)。 這很重要，因為部分設定的運作要仰賴基礎硬體。  

### <a name="import-steps"></a>匯入步驟
  
1. 在  **BizTalk Server 管理主控台**，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**設定**。  
  
2. 在 [ **BizTalk 設定儀表板**] 對話方塊中，按一下**匯入**。 **匯入設定精靈** 對話方塊隨即出現。  
  
   > [!NOTE]
   >  **目的地群組**會顯示您要匯入設定的目標電腦的群組資訊。  
  
    ![指定匯入設定檔的位置](../core/media/importsettings-filelocation.jpg "ImportSettings_FileLocation")  
  
3. 按一下 **指定檔案位置**頁面，然後再按一下![瀏覽設定檔案](../core/media/importsettings-filelocationbrowse.gif "ImportSettings_FileLocationBrowse")。 檔案總管隨即出現。  
  
4. 選取包含來源環境設定的 XML 檔案，然後按一下**開啟**。 **檔案位置**顯示 XML 檔案的路徑並**來源群組**會填入來源電腦的群組資訊。 按 [下一步] 。  
  
5. 在 **主控件對應**頁面上，執行下列動作：  
  
   1.  從**目的地主機**清單中，選取您要指定來源主控件，然後再按一下目的地主機**新增**。  
  
        ![裝載對應](../core/media/importsettings-hostmapping.gif "ImportSettings_HostMapping")  
  
   2.  在 [**選取來源實體**] 對話方塊中，選取來源主控件，然後按一下**確定**。  
  
       > [!NOTE]
       >  若要對應至單一來源主控件的多個目的地主控件，重複步驟**5a**並**5b**。  
  
   3.  在 [**主控件對應**頁面上，按一下**下一步]**。  
  
6. 在 **主控件執行個體對應**頁面上，執行下列動作：  
  
   1.  從目的地主控件執行個體的清單中，選取 目的地主控件的執行個體，您要指定來源主控件執行個體，然後再按一下**新增**。  
  
       > [!NOTE]
       >  主控件執行個體只能對應至已在「主控件對應」中建立的相對應主控件。 例如，如果您指定的對應所在**SourceHost1**對應至**DestinationHost1**，然後的執行個體**DestinationHost1**只能對應至執行個體**SourceHost1**。  
       >   
       >  匯入精靈會管理上述條件約束，您需要遵守此條件約束，否則 BizTalk 工作會擲回錯誤。  
       >   
       >  您需要使用慣例**hostname: Machinename**對應檔中指定主控件執行個體。 比方說， **Host1:Server1**對應中的檔案表示的執行個體**Host1**是執行中或位於**Server1**。  
  
        ![主機執行個體對應](../core/media/importsettings-hostinstancemapping.gif "ImportSettings_HostInstanceMapping")  
  
   2.  在 [**選取來源實體**] 對話方塊中，選取來源主控件執行個體，然後按一下**確定**。  
  
       > [!NOTE]
       >  若要將多個目的地主控件執行個體對應至單一來源主控件執行個體中，重複步驟**6a**要**6b**。  
  
   3.  在 [**主控件執行個體對應**索引標籤上，按一下**下一步]**。  
  
7. 在 [**匯入摘要**] 對話方塊中，確認您所建立的目的地和來源環境的所有匯入設定是否為有需要，，然後按一下**匯入**。 **進度**頁面會顯示匯入設定的進度。  
  
   > [!WARNING]
   >  您無法復原匯入 BizTalk Server 設定的動作。 如果您按一下**匯入**，在起始從來源環境匯入設定到目的地環境的程序並**取消**已停用。 確認您要繼續執行匯入後，再按一下**匯入**。  
  
8. 在 **匯入結果**索引標籤上，檢查的群組、 主控件和主控件執行個體的設定，匯入狀態，然後按一下**完成**完成匯入作業。 所有匯入的來源環境設定都會套用到目的環境。  
  
    ![匯入結果](../core/media/importsettings-importresults.gif "ImportSettings_ImportResults")  

## <a name="export-the-biztalk-group-host-and-host-instance-settings"></a>匯出 BizTalk 群組、 主機和主機執行個體設定  

1. 在  **BizTalk Server 管理主控台**，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**設定**。  
  
2. 在 [ **BizTalk 設定儀表板**] 對話方塊中，按一下**匯出**。 [另存新檔] 對話方塊隨即出現。  
  
3. 瀏覽至您要儲存目前的 BizTalk 設定的位置。 輸入檔案名稱，選取 XML 格式的類型，然後按一下**儲存**。  

> [!IMPORTANT]
>  我們不建議手動更新 匯出的 XML 檔案。 當您匯入生產環境中更新的 XML 檔案時，匯入程序可能會失敗，因為某種資料類型不符或因手動編輯其他錯誤。  

## <a name="see-also"></a>另請參閱  
 [針對 BizTalk Server 效能調整使用設定儀表板](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)