---
title: 如何從應用程式移除結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, schemas
- applications, schemas
- schemas, deleting
- managing [schemas], deleting
- managing [schemas], applications
- schemas, applications
ms.assetid: 17dd5869-b56c-4166-9f02-03e04e691eda
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6535764af00156325c006388a88803207329e5fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254646"
---
# <a name="how-to-remove-a-schema-from-an-application"></a>如何從應用程式移除結構描述
本主題說明如何使用 BizTalk Server 管理主控台，從應用程式移除結構描述。 這個程序也會從群組的 BizTalk 管理資料庫中移除結構描述。 您可能會想要在部署新版的結構描述之後，移除結構描述。 如需詳細資訊和更新應用程式成品的重要考量，請參閱[更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)。  
  
 當您移除結構描述時，如果某個先前版本的結構描述具有存在於應用程式中的相同根命名空間，這個版本便會成為作用中的版本。  
  
 當您移除結構描述時，會發生下列情況：  
  
-   從 BizTalk 管理資料庫中刪除結構描述。  
  
-   包含結構描述的 BizTalk 組件會從 BizTalk 管理資料庫中刪除，但是不會從本機檔案系統或全域組件快取 (GAC) 中移除 (如果存在於這些位置)。  
  
-   由於會刪除 BizTalk 組件，所以包含在組件中的所有成品也會從 BizTalk 管理資料庫中移除。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-remove-a-schema"></a>若要移除結構描述  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組包含結構描述移除與包含結構描述的應用程式。  
  
3.  按一下**結構描述**，結構描述中，以滑鼠右鍵按一下，然後按一下**移除**。  
  
## <a name="see-also"></a>另請參閱  
 [管理結構描述](../core/managing-schemas.md)