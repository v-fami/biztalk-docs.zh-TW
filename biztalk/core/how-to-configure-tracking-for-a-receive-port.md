---
title: 如何設定追蹤接收埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- configuring [HAT tracking], receive ports
- tracking, receive ports
- receive ports, tracking
- configuring, tracking
- receive ports, configuring
- tracking, configuring
- HAT, receive ports
- configuring, receive ports
- managing [receive ports], tracking
ms.assetid: dd569e84-cb1c-4191-912a-0c2eb2781a85
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e18748a5d9ff8088d09dfe28bf23c7b729b6afc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249102"
---
# <a name="how-to-configure-tracking-for-a-receive-port"></a>如何設定追蹤接收埠
本主題描述如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定接收埠的追蹤，例如用來檢視訊息內文和升級屬性的選項。 這可以協助您監控 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 實作的狀況並找出任何瓶頸。 您設定的追蹤設定會套用到接收埠的所有執行個體。  
  
 如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢查清單： 訊息和執行個體資料追蹤](../core/checklist-message-and-instance-data-tracking.md)  
  
 您設定的追蹤設定會套用到接收埠的所有執行個體。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶登入。 如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-tracking-for-a-receive-port"></a>設定追蹤接收埠  
  
1.  按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開 BizTalk 群組，並展開您要為其設定接收埠追蹤的 BizTalk 應用程式。  
  
3.  按一下**接收埠**，以滑鼠右鍵按一下接收埠，然後按一下**追蹤**。  
  
    > [!NOTE]
    >  啟用接收埠的訊息內文追蹤之前，請確定是否要完全追蹤接收埠；它可能會是負擔。 例如，接收管線 RcvPipe 用在不同的接收埠的數個接收位置上。 如果您啟用訊息內文追蹤 rcvpipe 的選項，它會導致訊息內文追蹤所有接收位置，您可能不想要的。 因此，設定訊息內文追蹤接收埠。  
  
4.  下表中所述，設定您要的追蹤選項，然後按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**追蹤訊息內文-連接埠處理前要求訊息**|選取此核取方塊，可讓您在接收訊息之前儲存和追蹤訊息內容。|  
    |**追蹤訊息內文-連接埠處理後要求訊息**|選取此核取方塊，可讓您在接收訊息之後儲存和追蹤訊息內容。|  
    |||  
    |||  
    |**追蹤訊息屬性-連接埠處理前要求訊息**|選取此核取方塊，可追蹤輸入訊息的升級屬性。|  
    |**追蹤訊息屬性-連接埠處理後要求訊息**|若您想要追蹤輸出訊息的升級屬性，請選取此核取方塊。|  
    |||  
    |||  
  
## <a name="see-also"></a>另請參閱  
 [管理接收埠](../core/managing-receive-ports.md)