---
title: 如何設定 MQSeries 配接器傳送和接收處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive handlers, MQSeries adapters
- configuring [MQSeries adapters], receive handlers
- MQSeries adapters, send handlers
- MQSeries adapters, receive handlers
- send handlers, MQSeries adapters
- configuring [MQSeries adapters], send handlers
ms.assetid: e1cfc415-50d2-440b-9301-ad69da28ad3e
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9a1e933f62adaf4e17fae5334e65f50610fb6f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248230"
---
# <a name="how-to-configure-mqseries-adapter-send-and-receive-handlers"></a>如何設定 MQSeries 配接器傳送和接收處理常式
您可以透過 [BizTalk Server 管理] 主控台，為 MQSeries 配接器的傳送與接收處理常式設定一些屬性。 描述的程序[如何設定 MQSeries 配接器接收位置和傳送埠](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)建立大多數傳送處理常式屬性的值。  
  
## <a name="to-configure-the-send-and-receive-handlers"></a>設定傳送與接收處理常式  
 請依照下列步驟執行，設定 MSQeries 配接器的傳送和接收處理常式：  
  
1.  按一下**啟動**，指向 **程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，按一下以展開**平台設定**，然後按一下 以展開**配接器**。  
  
3.  在展開的配接器清單中，選取**MQSeries**。 繫結至 MQSeries 配接器的傳送與接收處理常式清單會顯示在右窗格中。  
  
4.  在右窗格中，按兩下傳送或接收處理常式。  
  
5.  在**配接器處理常式屬性**對話方塊中，按一下 **屬性**。  
  
6.  在**MQSeries 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**批次中的訊息上限**|設定批次中的訊息數目上限。 只適用於傳送處理常式。|  
    |**Server**|執行 MQSeries Server for Windows 的電腦名稱。|  
  
7.  按一下 **[確定]**。  
  
    > [!NOTE]
    >  [接收位置] 與 [傳送埠] 屬性會覆寫 [接收處理常式] 與 [傳送處理常式] 值。 若 [接收位置] 或 [傳送埠] 屬性沒有值，配接器會分別使用 [接收處理常式] 與 [傳送處理常式] 值。  
  
8.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 MQSeries 配接器接收位置和傳送埠](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)   
 [設定 MQSeries 配接器](../core/configuring-the-mqseries-adapter.md)