---
title: 如何刪除傳送埠群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send port groups, deleting
- managing [send port groups], deleting
- deleting, send port groups
ms.assetid: 90c01e58-d35c-4cb2-ac6d-92199199fb42
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bf0e1a75799671ecd2e52515481c3d3be32ee67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013687"
---
# <a name="how-to-delete-a-send-port-group"></a>如何刪除傳送埠群組
本主題描述如何使用 BizTalk Server 管理主控台，從 BizTalk 應用程式中刪除傳送埠群組。 這樣做也會從群組的 BizTalk 管理資料庫中刪除傳送埠群組。 刪除傳送埠群組並不會刪除其包含的任何傳送埠。  
  
 如果符合下列條件，您就可以只刪除傳送埠群組：  
  
-   沒有協調流程繫結至此傳送埠群組。 如果發生這種情況，您可以依照下列中的指示移除繫結[如何解除繫結協調流程](../core/how-to-unbind-an-orchestration.md)。  
  
-   已停止並取消登錄此傳送埠群組。 如需停止及取消登錄傳送埠的指示，請參閱 <<c0> [ 如何取消登錄傳送埠或傳送埠群組](../core/how-to-unenlist-a-send-port-or-send-port-group.md)並[如何停止傳送埠或傳送埠群組](../core/how-to-stop-a-send-port-or-send-port-group.md)。  
  
-   沒有合作對象參考此傳送埠群組。 如需移除合作對象傳送埠群組的參考的指示，請參閱[如何檢視或編輯合作對象](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-delete-a-send-port-group"></a>刪除傳送埠群組  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 BizTalk 群組、 展開**應用程式**，然後展開包含您想要刪除的傳送埠群組的應用程式。  
  
3. 按一下 **傳送埠群組**，以滑鼠右鍵按一下傳送埠群組，然後按一下 **刪除**。  
  
## <a name="see-also"></a>另請參閱  
 [建立和設定傳送埠群組](../core/creating-and-configuring-send-port-groups.md)