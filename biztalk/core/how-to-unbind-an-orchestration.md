---
title: 解除繫結協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a7c421d-e0cb-4b23-b472-e501056d6329
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5673101934c4ba35deb4d63839c23e3d9cda7e4b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992623"
---
# <a name="unbind-an-orchestration"></a>解除繫結協調流程

## <a name="overview"></a>概觀
本主題描述如何使用 BizTalk Server 管理主控台從協調流程移除接收埠、傳送埠或主控件繫結。  
  
> [!NOTE]
>  應用程式開發人員可以使用本主題中的程序，移除協調流程的繫結。 您也可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="remove-bindings-from-an-orchestration"></a>從協調流程移除繫結  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，展開**應用程式**，然後展開包含您要移除的協調流程的應用程式繫結  
  
3. 按一下 **協調流程**，以滑鼠右鍵按一下協調流程後，按**屬性**，然後按一下**繫結**的左窗格中。  
  
4. 若要移除主控件繫結**主機**清單中，選取 **\<None\>**。  
  
5. 若要移除接收埠繫結，下方的下拉式清單**接收連接埠**，按一下 **\<None\>**。  
  
6. 若要移除傳送埠繫結，下方的下拉式清單**傳送埠/傳送埠群組**，按一下 **\<None\>**。  
  
7. 完成移除繫結，請按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [管理協調流程](../core/managing-orchestrations.md)   
 [如何設定協調流程的繫結](../core/how-to-configure-bindings-for-an-orchestration.md)   
 [部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)