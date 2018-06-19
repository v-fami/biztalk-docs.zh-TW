---
title: 停用新訊息發佈 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9099ecaa-31ed-4880-a0f6-8dbfaf783f7a
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 478cf89ac4677d60e9a5b5a855998e0b0e5120c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254558"
---
# <a name="disable-new-message-publication"></a>停用新訊息發佈

## <a name="overview"></a>概觀
您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台或 Windows Management Instrumentation (WMI)，來停用新訊息發佈。 您可停用 MessageBox 資料庫中的新訊息發佈，以停止 MessageBox 資料庫接收新訊息。 在某些 BizTalk Server 環境中，若您停用主要 MessageBox 資料庫的新訊息發佈，即能改善效能。 停用新訊息發佈並不會影響 MessageBox 資料庫中的現有訊息或是進行中的服務執行個體。  
  
 如需使用 WMI 停用新訊息發佈的詳細資訊，請參閱**MSBTS_MsgBoxSetting.DisableNewMessagePublication 屬性 (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
> [!IMPORTANT]
>  刪除 MessageBox 資料庫前，必須先停用新訊息發佈。 如需刪除 MessageBox 資料庫的詳細資訊，請參閱[如何刪除 MessageBox 資料庫](../core/how-to-delete-a-messagebox-database.md)。  
  
## <a name="prerequisites"></a>必要條件  
 管理 MessageBox 資料庫的系統管理員必須具備必要的使用者權限。 您必須具備下列使用者權限，才能管理 MessageBox 資料庫和停用新訊息發佈：  
  
-   您必須以「BizTalk Server 系統管理員」群組的成員身分登入。  
  
-   您必須是資料庫所在電腦的 SQL Server 系統管理員。  
  
## <a name="disable-steps"></a>停用步驟
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **訊息方塊**。  
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下您想要停用，然後按一下 MessageBox 資料庫**屬性**。  
  
4.  在**Messagebox 屬性**對話方塊中，選取**停用新訊息發佈**核取方塊，然後**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [管理 MessageBox 資料庫](../core/managing-messagebox-databases.md)   
 [加入新的 MessageBox 資料庫](../core/how-to-add-a-new-messagebox-database.md)   
 [刪除 MessageBox 資料庫](../core/how-to-delete-a-messagebox-database.md)   
 [MessageBox 資料庫](../core/the-messagebox-database.md)