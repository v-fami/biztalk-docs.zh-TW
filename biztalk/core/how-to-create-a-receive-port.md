---
title: "如何建立接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.procedure.createreceiveport
helpviewer_keywords:
- receive ports, creating
- managing [receive ports], creating
- creating, receive ports
ms.assetid: 23fae441-be80-4759-b3d6-74787a40e65b
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdecbc36962d3e4e45d35171747ff4c450959a83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-receive-port"></a>如何建立接收埠
本主題描述如何使用 BizTalk Server 管理主控台來建立接收埠。 接收埠是相似接收位置的邏輯群組，服務會透過這些位置接收資料，以與外部夥伴互動。  
  
 您可以建立下列類型的接收埠：  
  
-   單向：用在應用程式放置訊息但不同步等候回覆時  
  
-   要求-回應：用在應用程式需要訊息的回應時  
  
 除了本主題中所述的設定，您也可以指定接收埠，處理的訊息追蹤選項中所述[如何設定追蹤接收埠](../core/how-to-configure-tracking-for-a-receive-port.md)。  
  
> [!NOTE]
>  如果您要在遠端電腦上建立接收埠，而該電腦沒有啟用網路 DTC，就必須在建立接收埠之後，將遠端電腦重新開機。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-create-a-receive-port"></a>建立接收埠  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開您要建立接收埠的 BizTalk 群組和 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**或**要求回應接收埠**根據連接埠類型，您想要建立。  
  
4.  在**接收埠屬性**視窗中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|輸入連接埠的名稱。|  
    |**無驗證**|按一下此選項以停用驗證。 這是預設值。|  
    |**驗證失敗時捨棄訊息**|按一下此選項以啟用驗證，但會捨棄未驗證的訊息|  
    |**驗證失敗時保留訊息**|按一下此選項以啟用驗證，並保留未驗證的訊息。|  
    |**啟用失敗訊息的路由**|選取此核取方塊以嘗試將處理失敗的任何訊息路由至訂閱應用程式 (例如另一個接收埠或協調流程排程)。 清除核取方塊以擱置失敗的訊息，並產生負值通知 (NACK)。 預設值為清除核取方塊。 如需詳細資訊，請參閱[如何啟用接收埠的失敗訊息路由](../core/how-to-enable-routing-for-failed-messages-for-a-receive-port.md)。|  
  
5.  在左窗格中，按一下 **接收位置**，並建立新接收位置，此接收埠。 如需指示，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
6.  在左窗格中，按一下 **輸入對應**，執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**來源文件**|從下拉式清單選取要與此連接埠一起使用的來源結構描述。|  
    |**對應**|從下拉式清單選取您要與此連接埠產生關聯的對應。|  
    |**目標文件**|從下拉式清單選取要與此連接埠一起使用的目的結構描述。|  
  
7.  如果您要建立要求-回應接收埠，然後在左窗格中，按一下**輸出對應**，執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**來源文件**|從下拉式清單選取要與此連接埠一起使用的來源結構描述。|  
    |**對應**|從下拉式清單選取您要與此連接埠產生關聯的對應。|  
    |**目標文件**|從下拉式清單選取要與此連接埠一起使用的目的結構描述。|  
  
8.  完成設定接收埠，請按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [管理接收埠](../core/managing-receive-ports.md)