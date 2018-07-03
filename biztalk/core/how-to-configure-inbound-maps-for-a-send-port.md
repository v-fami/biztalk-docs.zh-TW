---
title: 如何設定傳送埠的輸入的對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [send ports], inbound maps
- configuring, send ports
- send ports, inbound maps
- configuring, inbound maps
- managing [send ports], configuring
- send ports, configuring
ms.assetid: 213c66ba-928f-4c00-9a87-f45eaa9f7dca
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5afe1edd63f10f39619948fb69d657bbaf85b81
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996103"
---
# <a name="how-to-configure-inbound-maps-for-a-send-port"></a>如何設定傳送埠的輸入對應
本主題描述如何使用 BizTalk Server 管理主控台來設定傳送埠的輸入對應。 輸入對應只能搭配動態或靜態請求-回應傳送埠使用。 您可以使用對應將 XSL 轉換套用到連接埠接收的回應訊息，無需透過協調流程處理訊息。 您可以新增輸入對應、移除對應，或將現有對應變更為不同的對應。 您可以新增一個以上的對應到傳送埠，但是每一個對應都必須有唯一的來源結構描述。 如需地圖的背景資訊，請參閱 <<c0> [ 對應](../core/maps.md)。  
  
> [!NOTE]
>  應用程式開發人員可以使用此主題中的程序，在開發程序中設定對應。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-inbound-maps-for-a-send-port"></a>設定傳送埠的輸入對應  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，展開您要為傳送埠設定輸入對應的 BizTalk 群組與 BizTalk 應用程式。  
  
3. 依序展開**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下**輸入對應**。  
  
4. 下表中所述，設定輸入的對應，然後按一下**確定**。 視需要重複新增或移除多個對應。  
  
   |使用|以進行此動作|  
   |--------------|----------------|  
   |**移除**|按一下以移除選取的對應。|  
   |**來源文件**|從下拉式清單選取輸入對應的來源文件。|  
   |**對應**|從下拉式清單選取與來源及目標文件關聯的對應。|  
   |**目標文件**|從下拉式清單選取輸入對應的目標文件。|  
  
## <a name="see-also"></a>另請參閱  
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)   
 [管理對應](../core/managing-maps.md)