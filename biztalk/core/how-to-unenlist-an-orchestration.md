---
title: 如何取消登錄協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, unenlisting
- enlisting, unenlisting
- managing [orchestrations], unenlisting
- unenlisting, orchestrations
ms.assetid: 038ed7bb-615c-4e4e-a5bb-79de2626de77
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7504551d6cc97f108d6cdee695f241ee983994a2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993511"
---
# <a name="how-to-unenlist-an-orchestration"></a>如何取消登錄協調流程
本主題描述如何使用 BizTalk Server 管理主控台來取消登錄協調流程。 取消登錄協調流程會將其從主控件中移除。 這會移除訂閱，使協調流程不再處理訊息。 您必須先取消登錄協調流程才能夠編輯其繫結。  
  
 您可以取消登錄協調流程之前，您必須終止任何執行的執行個體中, 所述[如何暫停、 繼續和終止協調流程執行個體](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md)。  
  
> [!NOTE]
>  應用程式開發人員可以使用此主題中的程序，在開發程序中取消登錄協調流程。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-unenlist-an-orchestration"></a>取消登錄協調流程  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，展開**應用程式**，然後展開包含您想要取消登錄協調流程的應用程式。  
  
3. 按一下 **協調流程**，以滑鼠右鍵按一下以取消登錄，然後按一下 協調流程**取消登錄**。  
  
   > [!NOTE]
   >  若要次取消登錄多個協調流程，請按住 shift 鍵並選取每個要取消登錄的協調流程，協調流程，以滑鼠右鍵按一下，然後按一下**取消登錄**。  
  
## <a name="see-also"></a>另請參閱  
 [管理協調流程](../core/managing-orchestrations.md)   
 [如何登錄協調流程](../core/how-to-enlist-an-orchestration.md)   
 [部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)