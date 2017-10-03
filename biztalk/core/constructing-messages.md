---
title: "建構訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, messages
- multi-part message types
- messages, modifying
- multi-part message types, about multi-part message types
- modifying, messages
- messages, creating
ms.assetid: c9fc1e97-ff53-42e2-848c-6c8fae7c9122
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 923fa87c4f3400a80ce83df132747d0004232323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="constructing-messages"></a>建構訊息
每次將訊息導入協調流程時，您都可以透過擷取訊息或指派值給訊息變數的方式來建構訊息。 您所建構的任何訊息都必須具有訊息類型，如此執行階段才會擁有其所使用之物件的完整描述。 多部分訊息類型可以是使用者定義、.NET 類別或結構描述。 您可以建構訊息以各種方式： 您可以叫用.NET 類別來建立訊息、 將某個訊息指派到另一個，或使用轉換來將訊息內特定的值對應到另一則訊息內的值。 訊息也可由接收動作建構，或是在您的協調流程接受訊息做為參數時建構。  
  
> [!NOTE]
>  多部分訊息類型不一定要包含多個部分；這種訊息可能只包含一個部分。  
  
> [!IMPORTANT]
>  訊息在 BizTalk 中是不變；也就是說，一旦您建構了訊息，便無法修改原始訊息。 如果需要進行變更，您必須建構訊息的新複本，然後為它指派適當的值。  
  
## <a name="in-this-section"></a>本節內容  
 [如何設定建構訊息圖形](../core/how-to-configure-the-construct-message-shape.md)  
  
 [如何設定訊息指派圖形](../core/how-to-configure-the-message-assignment-shape.md) 
  
 [如何設定 「 轉換 」 圖形](../core/how-to-configure-the-transform-shape.md) 
  
 [訊息指派圖形中的訊息參考](../core/message-references-in-message-assignment-shape.md)  
  
 [使用者程式碼中的訊息參考](../core/message-references-in-user-code.md)  
  
 [訊息指派中使用 Xpath](../core/using-xpaths-in-message-assignments.md)  
  
 [訊息指派中使用非標準 Xpath](../core/using-non-canonical-xpaths-in-message-assignments.md)  
  
 [使用者程式碼中建構的訊息](../core/constructing-messages-in-user-code.md)  
  
 [將節點附加至使用者程式碼中的訊息](../core/appending-nodes-to-messages-in-user-code.md)  
  
## <a name="see-also"></a>另請參閱  
 [協調流程中使用訊息](../core/using-messages-in-orchestrations.md)