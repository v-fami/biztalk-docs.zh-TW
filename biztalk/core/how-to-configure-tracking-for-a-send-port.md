---
title: "如何設定傳送埠的追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, send ports
- configuring, tracking
- tracking, send ports
- configuring [HAT tracking], send ports
- send ports, tracking
- managing [send ports], configuring
- tracking, configuring
- send ports, configuring
- managing [send ports], tracking
- HAT, send ports
ms.assetid: f32e97b0-244c-4acc-8f3f-b18cdb9ec0da
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60ba83b7d3451599a0422ec370fed41eeba94407
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-send-port"></a>如何設定傳送埠的追蹤
本主題描述如何使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定追蹤傳送埠，例如選項，以檢視訊息內文和升級屬性。 這可以協助您監控 BizTalk 實作的狀況並找出任何瓶頸。 您設定的追蹤設定適用於傳送埠的所有執行個體。  
  
 如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶登入。 如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-tracking-for-a-send-port"></a>設定傳送埠的追蹤  
  
1.  按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要為傳送埠設定追蹤的 BizTalk 群組與 BizTalk 應用程式。  
  
3.  按一下**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下 **追蹤**。  
  
    > [!NOTE]
    >  一個傳送埠只能與一個傳送管線相關聯。 如果停用傳送管線上的訊息內文追蹤，則也不會對傳送埠進行任何追蹤。 在這類情況下，您可以停用該傳送埠上的「追蹤」選項。  
  
4.  下表中所述，設定您要的追蹤選項，然後按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**追蹤訊息內文-連接埠處理前要求訊息**|選取此核取方塊，可讓您在收到訊息之前儲存和追蹤訊息內容。 **注意：**您必須啟用訊息內文管線追蹤，才能成功追蹤連接埠處理前的回應訊息。|  
    |**追蹤訊息內文-連接埠處理後要求訊息**|選取此核取方塊，可讓您在收到訊息之後儲存和追蹤訊息內容。|  
    |||  
    |||  
    |**追蹤訊息屬性-連接埠處理前要求訊息**|選取此核取方塊，可追蹤輸入訊息的升級屬性。|  
    |**追蹤訊息屬性-連接埠處理後要求訊息**|若您想要追蹤輸出訊息的升級屬性，請選取此核取方塊。|  
    |||  
    |||  
  
## <a name="see-also"></a>另請參閱  
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)