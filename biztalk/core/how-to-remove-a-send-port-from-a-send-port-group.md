---
title: "如何從傳送埠群組移除傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send port groups, deleting send ports
- managing [send port groups], deleting send ports
- managing [send ports], deleting send ports
- deleting, send ports
- send ports, deleting from send port groups
ms.assetid: a2289bfe-5bc9-4bc7-949c-5152ffb5bc62
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d109064a1286bcd622479a4075ef2d23dc8d320c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-send-port-from-a-send-port-group"></a>如何從傳送埠群組移除傳送埠
本主題描述如何使用 BizTalk Server 管理主控台，從傳送埠群組中移除傳送埠。 這樣做並不會從應用程式或 BizTalk 管理資料庫中刪除傳送埠。  
  
 傳送埠必須處於停止或取消登錄的狀態，才可以被移除。  
  
> [!NOTE]
>  若要路由訊息，傳送埠群組必須包含至少一個傳送埠。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-remove-a-send-port-from-a-send-port-group"></a>從傳送埠群組移除傳送埠  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要在其中將傳送埠自傳送埠群組移除的 BizTalk 群組和 BizTalk 應用程式。  
  
3.  按一下**傳送埠群組**，以滑鼠右鍵按一下傳送埠群組，然後按一下**屬性**。  
  
4.  在下**名稱**，按一下要移除，然後按一下 傳送埠**移除**。  
  
## <a name="see-also"></a>另請參閱  
 [建立和設定傳送埠群組](../core/creating-and-configuring-send-port-groups.md)   
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)