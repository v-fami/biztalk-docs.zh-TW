---
title: "如何啟動協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], starting
- starting, orchestrations
- orchestrations, starting
ms.assetid: 83411279-ee6f-4d68-aa3b-b5cd5e106088
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e277c078a36129a125937114ee9287a1e97999b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-start-an-orchestration"></a>如何啟動協調流程
本主題描述如何使用 BizTalk Server 管理主控台來啟動協調流程。 當您啟動協調流程時，會開始處理內送訊息。  
  
 啟動協調流程時，請牢記下列要點：  
  
-   在您啟動協調流程之前，必須先登錄協調流程以及與它相關的所有傳送埠和傳送埠群組。 如需指示，請參閱[如何登錄協調流程](../core/how-to-enlist-an-orchestration.md)和[如何登錄傳送埠或傳送埠群組](../core/how-to-enlist-a-send-port-or-send-port-group.md)。  
  
-   啟動協調流程不會自動啟動任何相關的傳送埠。 您必須個別啟動它們，如中所述[如何啟動傳送埠或傳送埠群組](../core/how-to-start-a-send-port-or-send-port-group.md)。  
  
-   如果您登錄與該協調流程相關的傳送埠和/或傳送埠群組，但是不啟動它們，BizTalk Server 會將傳送給該傳送埠或傳送埠群組的任何訊息放置在主控件的擱置佇列中，此主控件便是您登錄傳送埠或傳送埠群組的地方。  
  
> [!NOTE]
>  應用程式開發人員可以啟動協調流程以測試其功能在開發過程中，使用本主題中的程序。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須以「BizTalk Server 操作員」群組或「BizTalk Server 系統管理員」群組的成員身分登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-start-an-orchestration"></a>啟動協調流程  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您想要啟動的協調流程的應用程式。  
  
3.  按一下**協調流程**，協調流程中，以滑鼠右鍵按一下，然後按一下**啟動**。  
  
    > [!IMPORTANT]
    >  如果沒有在啟動協調流程前先登錄相關的傳送埠和傳送埠群組，您將會看到錯誤訊息。  
  
    > [!NOTE]
    >  若要同時啟動多個協調流程，按住 shift 鍵並選取每個協調流程、 協調流程，以滑鼠右鍵按一下，然後按一下**啟動**。  
  
## <a name="see-also"></a>另請參閱  
 [管理協調流程](../core/managing-orchestrations.md)   
 [如何停止協調流程](../core/how-to-stop-an-orchestration.md)   
 [如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)