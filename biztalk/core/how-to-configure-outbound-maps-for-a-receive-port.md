---
title: 如何設定輸出對應接收埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- maps, outbound
- configuring, maps
- managing [receive ports], outbound maps
- maps, configuring
- receive ports, configuring
- configuring, receive ports
- receive ports, outbound maps
ms.assetid: 01a864a1-9e8c-4b82-9d03-91be09d556da
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c74fcc259b833a64a480bbe88f4cc0273d2a83c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023604"
---
# <a name="how-to-configure-outbound-maps-for-a-receive-port"></a>如何設定接收埠的輸出對應
本主題描述如何使用 BizTalk Server 管理主控台來設定接收埠的輸出對應。 您可以與要求-回應接收埠一起使用輸出對應，將輸出訊息從一個結構描述轉換為另一個結構描述；例如，將您公司使用的訊息轉換為夥伴公司使用的結構描述。  
  
 您可以使用對應將 XSL 轉換套用到接收埠所傳送的回應訊息，無需透過協調流程處理訊息。 您可以新增輸出對應、移除對應，或將現有對應變更為不同的對應。 您可以新增一個以上的對應到接收埠，但每一個對應都必須有唯一的來源結構描述。 如需地圖的背景資訊，請參閱 <<c0> [ 對應](../core/maps.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-outbound-maps-for-a-receive-port"></a>設定接收埠的輸出對應  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，展開 BizTalk 群組，並展開您要為其設定接收埠輸出對應的 BizTalk 應用程式。  
  
3. 依序展開**接收連接埠**，以滑鼠右鍵按一下接收埠，按一下**屬性**，然後按一下**輸出對應**。  
  
4. 下表中所述，設定輸出對應，然後按一下**確定**。  
  
   |使用|以進行此動作|  
   |--------------|----------------|  
   |**移除**|按一下以移除選取的對應。|  
   |**來源文件**|從下拉式清單選取要與此連接埠一起使用的來源結構描述。|  
   |**對應**|從下拉式清單選取您要與此連接埠產生關聯的對應。|  
   |**目標文件**|從下拉式清單選取要與此連接埠一起使用的目的結構描述。|  
  
## <a name="see-also"></a>另請參閱  
 [管理接收埠](../core/managing-receive-ports.md)   
 [管理對應](../core/managing-maps.md)