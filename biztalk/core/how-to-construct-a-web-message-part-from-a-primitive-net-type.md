---
title: 如何建構 Web 訊息部分，從基本.NET 類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, Web messages
- Web messages, Message Assignment shape [Orchestration Designer]
- Web messages, creating
- Message Assignment shape [Orchestration Designer], Web messages
- Web messages, parts
- Web messages, .NET types
ms.assetid: 1fe52412-d2bc-484c-8925-c7ff3ca7704b
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 991970d5b0d40da1ec00b54919d2742cfd48353c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248022"
---
# <a name="how-to-construct-a-web-message-part-from-a-primitive-net-type"></a>如何建構 Web 訊息部分，從基本.NET 類型
從基本.NET 類型建立 Web 訊息部分使用**訊息指派**圖形。 或者，您也可以使用 .NET Helper 類別來設定部分，以便從基本 .NET 類型建立 Web 訊息部分。 如需有關使用.NET 類別建立訊息類型的詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。  
  
### <a name="to-construct-a-web-message-part-from-a-primitive-net-type"></a>若要從基本 .NET 類型建構 Web 訊息部分  
  
1.  開啟協調流程，開啟**工具箱**按一下**BizTalk 協調流程** 索引標籤。  
  
2.  拖曳**建構訊息**圖形至協調流程。  
  
3.  編輯**建構訊息**屬性，以包括您建立 Web 訊息類型的訊息執行個體。  
  
4.  拖曳**訊息指派**圖形拖曳到**建構訊息**圖形。  
  
5.  按兩下**訊息指派**圖形以開啟 BizTalk 運算式編輯器。  
  
6.  在 [BizTalk 運算式編輯器] 方塊中，將 Web 訊息類型的部分設定為需要的值。  
  
     例如，下列程式碼會將運算式設定為字串：  
  
    ```  
    ItemAvailRequestInstance.Item_ID = "This is Item_ID.";  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [建構 Web 訊息](../core/constructing-web-messages.md)