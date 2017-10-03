---
title: "如何將追蹤的訊息複製到 BizTalk 追蹤資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, copying between servers
- MessageBox database, Tracking database
- Tracking database, linking servers
- MessageBox database, copying messages
- linking, servers
- Tracking database, archiving
- archiving [Tracking database], linking servers
- Tracking database, MessageBox database
- Tracking database, copying messages
- archiving [Tracking database], MessageBox database
- MessageBox database, linking servers
- MessageBox database, archiving
ms.assetid: 369e972a-efbe-4ad5-a68f-aa3bbfb9ad54
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23aaa8e3bea3405d51a18da1778d420550ad4584
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-tracked-messages-into-the-biztalk-tracking-database"></a>如何將追蹤的訊息複製到 BizTalk 追蹤資料庫
因為封存與清除程序可能會存取並 (或) 更新不同 SQL Server 中的資料庫，所以您必須在相關 SQL Server 執行個體之間設定連結的伺服器。 您可以使用連結的伺服器，將追蹤的訊息從 [BizTalk MessageBox] (BizTalkMsgBoxDb) 資料庫伺服器直接複製到 [BizTalk 追蹤] (BizTalkDTADb) 資料庫。 您必須設定下列各項之間的連結伺服器：  
  
-   每一個 [BizTalk MessageBox] (BizTalkMsgBoxDb) 資料庫與 [BizTalk 追蹤] (BizTalkDTADb) 資料庫。  
  
-   [BizTalk 追蹤] (BizTalkDTADb) 資料庫與封存驗證的驗證伺服器。  
  
-   在裝載 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫的電腦上，SQL Server 代理程式的服務帳戶必須對連結伺服器上的 BizTalk 追蹤 (BizTalkDTADb) 資料庫擁有 db_datareader 和 db_datawriter 權限。  
  
> [!NOTE]
>  在 SQL Server Agent 中，確認複製作業執行無誤。 否則，錯誤可能使資料無法移至追蹤資料庫。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。  
  
### <a name="to-copy-tracked-messages-into-the-biztalk-tracking-database-sql-server-2008"></a>將追蹤的訊息複製到「BizTalk 追蹤」資料庫 (SQL Server 2008)  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到伺服器**對話方塊中，指定 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在的 SQL server 和適當的驗證類型的名稱，然後按一下**連接**至連接到適當的 SQL server。  
  
3.  在**Microsoft SQL Server Management Studio**，連按兩下**SQL Server Agent**，然後按一下 **作業**。  
  
4.  在詳細資料窗格中，以滑鼠右鍵按一下**TrackedMessages_Copy_BizTalkMsgBoxDb**，然後按一下 **屬性**。  
  
5.  在**作業屬性-TrackedMessages_Copy_BizTalkMsgBoxDb**對話方塊的 **選取頁面**，按一下 **步驟**。  
  
6.  在下**作業步驟清單**，按一下 **清除**，然後按一下 **編輯**。  
  
7.  在**命令**方塊、 編輯追蹤伺服器與視需要的資料庫名稱參數，然後按一下**確定**。  
  
8.  在**作業屬性-TrackedMessages_Copy_BizTalkMsgBoxDb**對話方塊的 **選取頁面**，按一下 **一般**，選取**已啟用**核取方塊，然後**確定**。  
  
     訊息將會從 BizTalk MessageBox (BizTalkMsgBoxDb) 複製到 BizTalk 追蹤 (BizTalkDTADb) 資料庫。  
  
> [!IMPORTANT]
>  若您加入新 MessageBox 資料庫，則必須為此新 MessageBox 資料庫再次執行此程序。  
  
## <a name="see-also"></a>另請參閱  
 [封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)