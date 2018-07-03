---
title: 如何刪除 MessageBox 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, MessageBox database
- managing [MessageBox database], deleting
- MessageBox database, deleting
ms.assetid: 51f91fcb-8b97-4b00-9056-6d216c8ccb58
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a025ea29e13ef938a39f9555785177f2c64e922
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023596"
---
# <a name="how-to-delete-a-messagebox-database"></a>如何刪除 MessageBox 資料庫
您可使用 BizTalk 管理主控台或 Windows Management Instrumentation (WMI) 從 BizTalk 群組移除 MessageBox 資料庫。 您可從 BizTalk 群組移除 MessageBox 資料庫，也可從 BizTalk Server 部署中整個移除此資料庫。  
  
 例如，您可以刪除不再使用的 MessageBox 資料庫，像是測試用途的資料庫。  
  
 有 8 個步驟可以從 BizTalk Server 部署永久且完全地移除 MessageBox 資料庫：  
  
1.  停用新訊息發佈。  
  
     刪除 MessageBox 資料庫前，必須先停用新訊息發佈。 停用新訊息發佈的相關資訊，請參閱[如何停用新訊息發佈](../core/how-to-disable-new-message-publication.md)。  
  
2.  等待快取重新整理間隔過期。  
  
     停用新訊息發佈後，必須先等待才能刪除資料庫。 定義的等待時間長度是 CacheRefreshInterval 的兩倍。 CacheRefreshInterval 的預設值為 60 秒。 您使用**群組內容**對話方塊來變更快取重新整理。  
  
3.  從 BizTalk 群組中移除 MessageBox 資料庫。  
  
     若從 BizTalk 群組移除 MessageBox 資料庫，會從 BizTalk 管理資料庫中移除 MessageBox 參考。  
  
4.  重新啟動包含到 MessageBox 資料庫的快取連線的主控件執行個體。  
  
     若執行階段引擎的快取資料庫連線是現用的，則從 SQL Server 實際刪除資料庫之前，必須重新啟動主控件執行個體。 如需啟動主控件執行個體的相關資訊，請參閱 <<c0> [ 如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md)。  
  
5.  停止正在存取資料庫的所有主控件執行個體。 如需停止進行中主控件執行個體的詳細資訊，請參閱 <<c0> [ 如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)。  
  
     若您要移除非主要 MessageBox 資料庫，那麼在停止進行中的主控件執行個體前，必須先停用該 MessageBox 的新訊息發佈，並確認：  
  
    -   該 MessageBox 中沒有其他正在執行的服務執行個體。  
  
    -   MessageBox 中沒有擱置的 (或任何其他剩餘的) 執行個體留下。  
  
    -   已將 BAM 追蹤的資料移動到 BizTalk 追蹤資料庫 (BizTalkDTADb) (TrackingData 資料表應該是空的)。  
  
    -   已將追蹤的訊息內文移動到 BizTalk 追蹤資料庫 (BizTalkDTADb)。  
  
6.  確定背景 SQL Server Agent 作業已經完成。  
  
     從 BizTalk Server 部署永久刪除 MessageBox 資料庫前，必須先確定背景 SQL Server Agent 作業已將所有追蹤的訊息內文傳輸到 TrackingSpool 資料表，然後再備份該資料表。 如需有關檢查背景 SQL Server Agent 作業狀態的詳細資訊，請參閱《SQL Server 線上叢書》。  
  
7.  備份將 TrackingSpool 資料表。  
  
     追蹤的訊息內文會保留在 MessageBox 資料庫中，直到您將 TrackingSpool 資料表手動備份到外部儲存裝置為止。 備份開始前，背景 SQL Server Agent 作業會將訊息內文從 Spool 資料表傳輸到 TrackingSpool 資料表。 如需有關手動備份 SQL Server 資料表的詳細資訊，請參閱《SQL Server 線上叢書》。  
  
8.  從 SQL Server 移除資料庫。  
  
     從 BizTalk 群組移除 MessageBox 資料庫，並不會從 Microsoft SQL Server 實際移除資料庫。 若要永久刪除 MessageBox 資料庫，必須在從 BizTalk 群組移除此資料庫後，再使用 SQL Server Enterprise Manager 或 SQL Server Management Studio 將它移除。  
  
## <a name="prerequisites"></a>必要條件  
 管理 MessageBox 資料庫的系統管理員必須具備必要的使用者權限。 您必須具備下列使用者權限，才能管理 MessageBox 資料庫和停用新訊息發佈：  
  
-   您必須以「BizTalk Server 系統管理員」群組的成員身分登入。  
  
-   您必須是資料庫所在電腦的 SQL Server 系統管理員。  
  
### <a name="to-delete-a-messagebox-database-from-a-biztalk-group"></a>從 BizTalk 群組刪除 MessageBox 資料庫  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 BizTalk 群組，按一下**平台設定**，然後按一下**訊息方塊**。  
  
3. 在 詳細資料 窗格中，以滑鼠右鍵按一下您想要移除此項目，然後按一下 訊息方塊資料庫**屬性**。  
  
4. 在 **訊息方塊內容**對話方塊中，選取**停用新訊息發佈**核取方塊。  
  
5. 使用 BizTalk Server 管理主控台中的 [群組中樞] 頁面，確認您正要刪除的 MessageBox 資料庫上沒有凍結的或擱置的訊息執行個體。  
  
6. 等待兩倍於 CacheRefreshInterval 的時間。 CacheRefreshInterval 的預設值為 60 秒。  
  
7. 在詳細資料窗格中，以滑鼠右鍵按一下您想要刪除，然後按一下的 MessageBox 資料庫**刪除**。  
  
8. 閱讀警告訊息之後, 請按**確定**。  
  
9. 在主控台樹狀目錄中，展開 BizTalk 群組中，按一下**平台設定**，然後按一下**主控件執行個體**。  
  
10. 在詳細資料窗格中，使用滑鼠右鍵按一下所有執行中的主控件執行個體，然後停止並重新啟動每一個。  
  
11. 在 MessageBox 資料庫所在的伺服器上，視您正在使用的 SQL Server 版本，開啟 SQL Server Enterprise Manager 或 SQL Server Management Studio，然後刪除資料庫。  
  
     如需有關如何刪除 SQL Server 中的資料庫的資訊，請參閱《SQL Server 線上叢書》。  
  
## <a name="see-also"></a>另請參閱  
 [管理 MessageBox 資料庫](../core/managing-messagebox-databases.md)   
 [如何加入新的 MessageBox 資料庫](../core/how-to-add-a-new-messagebox-database.md)   
 [如何停用新訊息發佈](../core/how-to-disable-new-message-publication.md)   
 [MessageBox 資料庫](../core/the-messagebox-database.md)