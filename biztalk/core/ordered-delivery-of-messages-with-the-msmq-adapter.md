---
title: 依序傳遞訊息，與 MSMQ 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, ordered delivery
- MSMQ adapters, ordered delivery
ms.assetid: e8dafc76-e894-4120-9cea-d014d635850e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac842fcd1e9b386fa885844f3a797504ed7c4c3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263582"
---
# <a name="ordered-delivery-of-messages-with-the-msmq-adapter"></a>依序傳遞訊息，與 MSMQ 配接器
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供**排序的傳遞**選項用於靜態傳送埠。 設定**排序的傳遞**至傳送埠上的選項**True**可確保 BizTalk Server 將訊息傳遞至傳送埠，它們會發佈到 MessageBox 資料庫的順序相同。 若要提供端對端排序的傳遞，必須符合下列條件：  
  
-   必須以保留提交訊息給 BizTalk Server 的訊息順序之配接器接收訊息。  
  
-   您必須訂閱這些訊息的傳送埠**排序的傳遞**選項設定為**True**。  
  
-   如果應使用的訊息，協調流程中的單一執行個體的程序來協調流程，協調流程應該設定為使用循序群組，而**排序的傳遞**屬性協調流程的接收埠應該設定為**True**。  
  
## <a name="using-the-msmq-adapter-for-ordered-delivery-of-messages"></a>使用 MSMQ 配接器進行依序傳遞訊息  
 MSMQ 接收配接器必須支援保留提交訊息至 BizTalk Server 的訊息順序。 端對端排序的傳遞訊息透過 BizTalk Server 接收訊息與 MSMQ 配接器，如果透過已設定的傳送埠來處理訊息時可達到**排序的傳遞**選項設為**True**。  
  
## <a name="see-also"></a>另請參閱  
 [依序傳遞訊息](../core/ordered-delivery-of-messages.md)   
 [如何設定 MSMQ 接收位置](../core/how-to-configure-an-msmq-receive-location.md)