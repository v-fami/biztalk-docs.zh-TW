---
title: "刪除主控件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3df8719-27cb-4010-82e3-68226ab74b17
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fd5f54fa84ddb521444cfb3f2351a8062c4de00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="delete-a-host"></a>刪除主控件
只有在下列情況才可以刪除主控件：  
  
-   不是預設主控件。  
  
-   不是執行主控件追蹤的唯一主控件。  
  
-   沒有裝載任何配接器處理常式。  
  
-   沒有已登錄的協調流程。  
  
-   沒有已開始的主控件執行個體。  
  
-   如果主控件未叢集化。  
  
 如需主控件的詳細資訊，請參閱[主機](../core/hosts.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須具有以下的使用者權限才能建立主控件、修改主控件屬性和刪除主控件：  
  
-   您必須是「BizTalk Server 系統管理員」群組的成員。  
  
-   在 SQL Server 中您必須具有以下權限：  
  
    -   您必須是 SQL Server 系統管理員，或是 BizTalk 追蹤資料庫 (BizTalk DTADb)、MessageBox 資料庫 (BizTalkMsgBoxDb)，以及 BAM 主要匯入資料庫 (BAMPrimaryImport) 中 db_owner 或 db_securityadmin SQL Server 資料庫角色的成員。  
  
    -   您必須是具有 MessageBox 資料庫之所有電腦上 sysadmin SQL Server 角色的成員，或是所有 MessageBox 資料庫中 db_owner 或 db_ddladmin SQL Server 角色的成員。  
  
## <a name="steps"></a>步驟 
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **主機**。  
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下您想要刪除，然後按一下 的主機**刪除**。  
  
4.  在**確認主機刪除**對話方塊中，按一下 **是**。  
  
## <a name="see-also"></a>另請參閱  
-  [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
-  [如何建立新的主機](../core/how-to-create-a-new-host.md)   
-  [如何修改主控件屬性](../core/how-to-modify-host-properties.md)   
-  **MSBTS_Host (WMI)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]