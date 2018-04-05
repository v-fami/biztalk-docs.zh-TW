---
title: 如何移除另一個應用程式的參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, references
ms.assetid: cc867706-7c56-4386-b7ec-9fd7cf6c83a4
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de51adb1a9c42874025527ad458ecb6e3c311b3f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-reference-to-another-application"></a>如何移除另一個應用程式的參考
本主題描述如何使用 BizTalk Server 管理主控台，從某個應用程式中移除其他應用程式的參考。 當您不再需要使用目前應用程式中的成品，而該成品位於相同 BizTalk 群組的其他應用程式中時，請移除參考。 如需新增參考的詳細資訊，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。  
  
 如果目前應用程式中的成品仍在使用參考應用程式中的成品，移除參考的作業將會失敗。  
  
> [!CAUTION]
>  BizTalk Server 中的每個應用程式都會自動包含 BizTalk.系統應用程式的參考。 這是因為每一個 BizTalk 應用程式都會使用 BizTalk 系統包含的成品。 您絕對不能移除 BizTalk.系統應用程式的參考， 否則您的應用程式可能無法正常運作。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-remove-a-reference-to-another-application"></a>若要移除另一個應用程式的參考  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下您要從中移除參考 （參考到另一個應用程式），應用的程式，然後按一下**屬性**.  
  
3.  在 [屬性] 頁面的左窗格中，按一下**參考**。  
  
4.  在右窗格中，按一下 應用程式，您不想再參考這個應用程式，請按一下 **移除**，然後按一下 **確定**。  
  
## <a name="see-also"></a>另請參閱  
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)