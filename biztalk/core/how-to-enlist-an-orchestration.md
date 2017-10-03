---
title: "如何登錄協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], enlisting
- orchestrations, enlisting
- enlisting, orchestrations
ms.assetid: b21a398b-8c9a-42ae-aac0-de35dbfd8176
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f58cb697e270052f8f42229997b1125e808816b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enlist-an-orchestration"></a>如何登錄協調流程。
這個主題說明如何使用 BizTalk Server 管理主控台，將協調流程登錄到主控件中。 您必須登錄協調流程，才能將它啟動。  
  
 登錄協調流程時，請記住下列要點：  
  
-   **協調流程必須繫結，然後您可以將它登錄。** 如需設定的協調流程繫結的指示，請參閱[如何設定協調流程繫結](../core/how-to-configure-bindings-for-an-orchestration.md)。  
  
-   **訂用帳戶會自動建立。** 協調流程登錄程序會在 MessageBox 資料庫中建立必要的訂閱。  
  
-   **您必須安裝應用程式。** 您必須在所有要執行協調流程的電腦上安裝包含協調流程的應用程式。 如需詳細資訊，請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。  
  
-   **呼叫的協調流程必須繫結呼叫的協調流程相同的主控件。** 任何由其他協調流程所呼叫的協調流程必須繫結至與發出呼叫的協調流程相同的主控件。  
  
-   **您也應該登錄依存的協調流程。** 如果您登錄協調流程，但沒有登錄任何依存的協調流程，則依存的協調流程將不會有任何訂閱。 沒有訂閱的依存協調流程可能會因為沒有符合訊息的訂閱而捨棄或擱置訊息。  
  
> [!NOTE]
>  應用程式開發人員可以使用此主題中的程序，在開發程序中登錄協調流程以測試其功能。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-enlist-an-orchestration"></a>登錄協調流程  
  
1.  按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您想要登錄的協調流程的應用程式。  
  
3.  按一下**協調流程**，以滑鼠右鍵按一下協調流程登錄，然後按一下 **登錄**。  
  
    > [!NOTE]
    >  若要一次登錄多個協調流程、 按住 shift 鍵並選取要登錄的每個協調流程，以滑鼠右鍵按一下協調流程，然後**登錄**。  
  
     如此便會登錄協調流程，並建立適當的訂閱。 協調流程目前是處於停止狀態。 若要開始處理內送訊息，您必須明確地啟動協調流程上按一下滑鼠右鍵按一下**啟動**。 如需詳細資訊，請參閱[如何啟動協調流程](../core/how-to-start-an-orchestration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理協調流程](../core/managing-orchestrations.md)   
 [如何取消登錄協調流程](../core/how-to-unenlist-an-orchestration.md)