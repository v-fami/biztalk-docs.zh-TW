---
title: 如何變更應用程式的名稱 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- naming conventions, renaming
- naming conventions, applications
- applications, renaming
ms.assetid: ae59c792-44bd-43e0-a4ae-e67bcad2e128
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4826688935bf18cd5288924d4544f484b3dcf0cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248190"
---
# <a name="how-to-change-the-name-of-an-application"></a>如何變更應用程式的名稱
本主題將描述如何使用 BizTalk Server 管理主控台來變更應用程式的名稱。 您所使用的應用程式名稱不能已存在於群組中。  
  
> [!NOTE]
>  如果您匯出的應用程式 .msi 檔案會參考此重新命名的應用程式，則當您匯入此 .msi 檔案時，該參考將無法再運作。 您將需要使用新的應用程式名稱來更新此參考。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-change-the-name-of-an-application"></a>若要變更應用程式的名稱  
  
1.  按一下**啟動**，指向 **程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下您想要變更，然後按一下其名稱的應用程式**屬性**。  
  
3.  在**名稱**方塊中，輸入新名稱，則應用程式，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)