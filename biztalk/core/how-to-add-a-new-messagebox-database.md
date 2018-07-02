---
title: 如何加入新的 MessageBox 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding, MessageBox database
- MessageBox database, adding
- managing [MessageBox database], adding
ms.assetid: 98d850dc-fe3e-43dd-8b5d-9b8c23c006ae
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db394722afcdf9e5972a925963b5200b4eba157e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974519"
---
# <a name="how-to-add-a-new-messagebox-database"></a>如何加入新的 MessageBox 資料庫
您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，將新的 MessageBox 資料庫新增到 BizTalk Server 部署。 MessageBox 資料庫是在執行協同處裡的伺服器之間進行負載平衡工作項目的基礎。 若要增加您的系統可以處理的訊息數目，您可能需要新增其他的 MessageBox 資料庫。  
  
 您無法同時建立新的 MessageBox 資料庫並完成協調流程、傳送埠或傳送埠群組的登錄。 已登錄的協調流程、傳送埠或傳送埠群組會存取 BizTalk Server 必須複製到新 MessageBox 資料庫的資料。 存取這個資料時，BizTalk Server 無法將其複製到新的 MessageBox 資料庫。  
  
 您可以指定本機與遠端資料庫做為 MessageBox 資料庫。 如需 BizTalk Server 資料庫的資訊，請參閱[BizTalk Server 中的資料庫](../core/databases-in-biztalk-server.md)。  
  
> [!IMPORTANT]
>  SQL Server 代理程式必須在您要新增 MessageBox 資料庫的所有 SQL 伺服器上執行。  
  
## <a name="prerequisites"></a>必要條件  
 管理 MessageBox 資料庫的系統管理員必須具備必要的使用者權限。 您必須具備下列使用者權限，才能管理 MessageBox 資料庫和停用新訊息發佈：  
  
-   您必須以「BizTalk Server 系統管理員」群組的成員身分登入。  
  
-   您必須是資料庫所在電腦的 SQL Server 系統管理員。  
  
### <a name="to-add-a-new-messagebox-database"></a>加入新的 MessageBox 資料庫  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開 [BizTalk 群組]，然後按一下**平台設定**。  
  
3. 以滑鼠右鍵按一下**訊息方塊**，按一下**新增**，然後按一下**Messagebox**。  
  
4. 在 [**訊息方塊內容**] 對話方塊中，執行下列命令，，然後按一下**確定**:  
  
   |使用|以進行此動作|  
   |--------------|----------------|  
   |**[SQL Server]**|顯示裝載 MessageBox 資料庫的 SQL Server 名稱。|  
   |**[資料庫備份]**|顯示 MessageBox 資料庫的名稱。|  
   |**主要訂閱訊息方塊**|指示選取的 MessageBox 資料庫是否為主要。 若目前的 MessageBox 資料庫為主要，此核取方塊將為已選取和無法使用的狀態。 當您執行「組態精靈」所建立的第一個 MessageBox 資料庫預設為主要。|  
   |**停用新訊息發佈**|選取此核取方塊以指定您不想讓此 MessageBox 資料庫接收啟動訊息。|  
  
## <a name="see-also"></a>另請參閱  
 [管理 MessageBox 資料庫](../core/managing-messagebox-databases.md)   
 [如何停用新訊息發佈](../core/how-to-disable-new-message-publication.md)   
 [如何刪除 MessageBox 資料庫](../core/how-to-delete-a-messagebox-database.md)   
 [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)   
 [MessageBox 資料庫](../core/the-messagebox-database.md)