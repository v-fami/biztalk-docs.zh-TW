---
title: 如何設定傳送埠的輸出對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, outbound maps
- configuring, send ports
- managing [send ports], configuring
- send ports, outbound maps
- send ports, configuring
- managing [send ports], outbound maps
ms.assetid: 9f5f5504-5a7f-4b21-9a65-91dce9d35890
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51d3feaba929d1a7585a8e7c3b29f6868dcc9dc7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248086"
---
# <a name="how-to-configure-outbound-maps-for-a-send-port"></a>如何設定傳送埠的輸出對應
本主題描述如何使用 BizTalk Server 管理主控台來設定傳送埠的輸出對應。 您將會使用對應將 XSL 轉換套用至傳送埠傳所傳送的訊息，而無需協調流程處理訊息。 您可以新增輸出對應、移除對應，或將現有對應變更為不同的對應。 您可以新增一個以上的對應到傳送埠，但是每一個對應都必須有唯一的來源結構描述。 如需對應的背景資訊，請參閱[對應](../core/maps.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-outbound-maps-for-a-send-port"></a>設定傳送埠的輸出對應  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要為其設定傳送埠輸出對應的 BizTalk 群組與 BizTalk 應用程式。  
  
3.  展開**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下 **輸出對應**。  
  
4.  下表中所述，設定輸出對應，然後按一下**確定**。 視需要重複新增或移除多個對應。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**移除**|按一下以移除選取的對應。|  
    |**輸出對應-來源文件**|從下拉式清單選取輸出對應的來源文件。|  
    |**輸出對應-對應**|從下拉式清單選取與來源及目標文件關聯的對應。|  
    |**輸出對應-目標文件**|從下拉式清單選取輸出對應的目標文件。|  
  
## <a name="see-also"></a>另請參閱  
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)   
 [管理對應](../core/managing-maps.md)