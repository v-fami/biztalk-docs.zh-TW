---
title: "如何刪除接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive locations], deleting
- receive locations, deleting
- deleting, receive locations
ms.assetid: aa859355-af4c-48d9-b224-78fd3ef618fc
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19828b7b456e872af78c2bae3c89ed75828a32ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-receive-location"></a>如何刪除接收位置
本主題描述如何使用 BizTalk Server 管理主控台來刪除接收位置。 當您刪除接收位置時，它會從 BizTalk 管理資料庫中移除，而且不再顯示於 BizTalk Server 管理主控台中。  
  
 當您刪除接收位置時，請牢記下列要點：  
  
-   您可以刪除接收位置之前，它必須先停用，如中所述[如何停用接收位置](../core/how-to-disable-a-receive-location.md)。  
  
-   您不能刪除接收埠的主要接收位置。 若嘗試這麼做，將收到一個錯誤訊息。 若要刪除此接收位置，您可以刪除接收埠 (這同時會刪除它所包含的所有接收位置)，或者您也可以指定其他接收位置做為主要接收位置，然後再刪除原始接收位置。 如需有關將接收位置建立主要接收位置的指示，請參閱[如何編輯接收位置的內容](../core/how-to-edit-the-properties-of-a-receive-location.md)。  
  
-   在您刪除接收位置之後，請重新啟動與所刪除接收位置對應的外掛式主控件工作者處理序。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-delete-a-receive-location"></a>若要刪除接收位置  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開您要刪除其接收位置的 BizTalk 群組和 BizTalk 應用程式。  
  
3.  按一下**接收位置**，以滑鼠右鍵按一下要刪除，然後按一下 接收位置**刪除**。  
  
## <a name="see-also"></a>另請參閱  
 [管理接收位置](../core/managing-receive-locations.md)