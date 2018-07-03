---
title: 如何從應用程式移除對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, maps
- deleting, maps
- managing [maps], deleting
- managing [maps], applications
ms.assetid: 27d9bb08-36f0-46ff-ae9a-2247be6e3f96
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8863e95aabed933872edbe9a93146e59ad7480d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000095"
---
# <a name="how-to-remove-a-map-from-an-application"></a>如何從應用程式移除對應
本主題描述如何使用 BizTalk Server 管理主控台，從 BizTalk 應用程式中移除對應。 您可能會想要在部署新版本的對應之後移除對應。 如需詳細資訊和更新應用程式成品的重要考量，請參閱 <<c0> [ 更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)。  
  
 移除對應時，會發生下列情況：  
  
-   對應會從 BizTalk 管理資料庫中刪除。  
  
-   包含對應的 BizTalk 組件會從 BizTalk 管理資料庫中刪除，但是不會從本機檔案系統或全域組件快取 (GAC) 中移除 (如果存在於這些位置)。  
  
-   由於會刪除 BizTalk 組件，所以包含在組件中的所有成品也會從 BizTalk 管理資料庫中移除。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-remove-a-map"></a>若要移除對應  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，依序展開 BizTalk 群組包含對應中移除，然後再展開 包含對應的應用程式。  
  
3. 按一下  **Maps**資料夾中，以滑鼠右鍵按一下地圖上，然後**移除**。  
  
> [!NOTE]
>  若要移除多個對應，請按住 shift 鍵，請按一下移除，以滑鼠右鍵按一下其中一個對應，然後按一下 每個對應**移除**。  
  
## <a name="see-also"></a>另請參閱  
 [管理對應](../core/managing-maps.md)   
 [如何從應用程式移除 BizTalk 組件](../core/how-to-remove-a-biztalk-assembly-from-an-application.md)   
 [解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md)