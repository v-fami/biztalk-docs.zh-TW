---
title: "如何設定的輸入的對應接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- configuring, maps
- configuring, inbound maps
- maps, configuring
- receive ports, configuring
- receive ports, inbound maps
- configuring, receive ports
- maps, inbound
- managing [receive ports], inbound maps
ms.assetid: b7448b39-f024-4353-818b-f753c2d60751
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5275b2701d42240df06810ef43563ca4a200151f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-inbound-maps-for-a-receive-port"></a>如何設定接收埠的輸入對應
本主題描述如何使用 BizTalk Server 管理主控台來設定接收埠的輸入對應。 您會使用輸入對應，將輸入訊息從一個結構描述轉換至其他結構描述；例如，將接收自夥伴的訊息轉換成可供公司使用的結構描述。  
  
 您可以使用對應，將 XSL 轉換套用至接收埠傳送的訊息，而無需透過協調流程處理訊息。 您可以新增輸入對應、移除對應，或將現有對應變更為不同的對應。 您可以新增一個以上的對應到接收埠，但每一個對應都必須有唯一的來源結構描述。 如需對應的背景資訊，請參閱[對應](../core/maps.md)。  
  
> [!NOTE]
>  應用程式開發人員可以使用此主題中的程序，在開發程序中設定接收埠的對應。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-inbound-maps-for-a-receive-port"></a>設定接收埠的輸入對應  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要為其設定接收埠輸入對應的 BizTalk 群組和 BizTalk 應用程式。  
  
3.  按一下**接收埠**，以滑鼠右鍵按一下接收埠，按一下**屬性**，然後按一下 **輸入對應**。  
  
4.  下表中所述設定輸入的對應，然後按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**移除**|按一下以移除選取的對應。|  
    |**來源文件**|從下拉式清單選取要與此連接埠一起使用的來源結構描述。|  
    |**對應**|從下拉式清單選取您要與此連接埠產生關聯的對應。|  
    |**目標文件**|從下拉式清單選取要與此連接埠一起使用的目的結構描述。|  
  
## <a name="see-also"></a>另請參閱  
 [管理接收埠](../core/managing-receive-ports.md)   
 [管理對應](../core/managing-maps.md)