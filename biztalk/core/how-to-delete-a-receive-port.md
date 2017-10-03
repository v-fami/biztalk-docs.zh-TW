---
title: "如何刪除接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], deleting
- deleting, receive ports
- receive ports, deleting
ms.assetid: 69cd86f7-e3cc-4a50-8d15-5f978c94a6be
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c5ad0b1d69747f3a890fbc20c63b8aa76c30639
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-receive-port"></a>如何刪除接收埠
本主題描述如何使用 BizTalk Server 管理主控台從 BizTalk 應用程式刪除接收埠。 在執行此工作時，也會從群組的 BizTalk 管理資料庫刪除接收埠，以及該接收埠上的所有接收位置。  
  
 若要順利完成此作業，接收埠不可繫結至協調流程。 如需移除接收埠的繫結的指示，請參閱[如何解除繫結協調流程](../core/how-to-unbind-an-orchestration.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-delete-a-receive-port"></a>刪除接收埠  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您想要刪除接收埠的應用程式。  
  
3.  按一下**接收埠**，接收埠，以滑鼠右鍵按一下，然後按一下**刪除**。  
  
## <a name="see-also"></a>另請參閱  
 [管理接收埠](../core/managing-receive-ports.md)