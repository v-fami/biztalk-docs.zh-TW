---
title: "如何使用訊息內容控制訊息處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1e3792e-9cd4-42b6-8b9d-3c2a022a16d6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73d356496d07bb2227aa514ee68f2a2a51e2291b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ways-to-use-message-content-to-control-message-processing"></a>使用訊息內容控制訊息處理的方式
有兩種類型的屬性升級：**辨別欄位**和**屬性欄位**，後者使用屬性結構描述。 在 [BizTalk 編輯器] 中，您管理這兩種類型的屬性升級使用**升級屬性**對話方塊中，以存取使用**升級屬性**屬性**結構描述**節點。  
  
> [!NOTE]
>  您可升級的值有部分限制。 如需詳細資訊，請參閱中的資料表[升級屬性](../core/promoting-properties.md)。  
  
 您必須根據實例的詳細資料來決定要使用的屬性升級類型。 請考慮下列差異**辨別欄位**屬性升級和**屬性欄位**屬性升級：  
  
-   **辨別欄位**不能參與訊息路由，因此它們沒有出現在篩選運算式中。 它們只有在協調流程的內容中可以使用，不過，它們在傳送和接收訊息時的負擔較小。  
  
-   **辨別欄位**並沒有任何大小限制。 **屬性欄位**限制為 255 個字元。  
  
-   **辨別欄位**不需要任何獨立的成品可以建立，但是**屬性欄位**需要建立和維護屬性結構描述。  
  
 根據這些考量，您應該將節點升級為**屬性欄位**只有當您想要使用的升級的屬性輸入路由或追蹤的訊息。 否則，如果您只存取協調流程中的升級的屬性，您應該利用事實的**辨別欄位**是成本更低、 較輕量級，但更容易使用比**屬性欄位**。  
  
 使用升級屬性**辨別欄位**機制只是從協調流程中存取，而且不能從管線、 連接埠，以及其他存取。 相反地，使用升級屬性**屬性欄位**，屬性結構描述機制可從所有這些元件。 另一個重要的差異是屬性欄位值的限制為 255 個字元，但是辨別欄位值則沒有這類限制。  
  
 本節提供兩種類型的屬性升級相關資訊，包括如何使用 BizTalk 編輯器為訊息結構描述建立這類升級屬性的解說資訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [關於 BizTalk 訊息內容屬性](../core/about-biztalk-message-context-properties.md)  
  
-   [執行個體訊息使用辨別欄位處理](../core/instance-message-processing-using-distinguished-fields.md)  
  
-   [使用屬性升級處理執行個體訊息](../core/instance-message-processing-using-property-promotion.md)