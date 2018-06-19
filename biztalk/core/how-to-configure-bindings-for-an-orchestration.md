---
title: 設定協調流程的繫結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9724a3a0-c217-4f98-b6d9-21f788ce50ba
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adb695f9636327107887397372d5fc2dda74e4eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248918"
---
# <a name="how-to-configure-bindings-for-an-orchestration"></a>如何設定協調流程的繫結

## <a name="overview"></a>概觀
本主題描述如何使用 BizTalk Server 管理主控台來設定協調流程的繫結。 此項作業包括將協調流程所定義的邏輯連接埠繫結至臨時或生產環境中的實體連接埠，以及將協調流程繫結至主控件。 如果已經繫結協調流程，您可以使用此程序來變更繫結。  
  
 在設定繫結之後，您可以登錄協調流程，然後加以啟動，這樣協調流程即可開始處理訊息。 如需執行這些工作的指示，請參閱[如何登錄協調流程](../core/how-to-enlist-an-orchestration.md)和[如何啟動協調流程](../core/how-to-start-an-orchestration.md)。  
  
> [!NOTE]
>  應用程式開發人員可以使用此主題中的程序，在開發程序中為協調流程設定繫結以測試其功能。 您也可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="configure-bindings-for-an-orchestration"></a>設定協調流程的繫結  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您想要在協調的流程的應用程式設定繫結  
  
3.  按一下**協調流程**，以滑鼠右鍵按一下您要設定繫結，然後按一下 協調的流程**屬性**。  
  
4.  按一下**繫結** 索引標籤，並從**主機**清單中，選取要登錄協調流程的主控件。  
  
5.  從下拉式清單中**接收埠**每個輸入邏輯連接埠旁邊的資料行，選取您要繫結的邏輯連接埠的接收埠。  
  
6.  從下拉式清單中**傳送埠/傳送埠群組**每個輸入邏輯連接埠旁邊的資料行，選取您想要繫結的邏輯連接埠，然後按一下傳送埠**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [管理協調流程](../core/managing-orchestrations.md)   
 [如何解除繫結協調流程](../core/how-to-unbind-an-orchestration.md)   
 [部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)