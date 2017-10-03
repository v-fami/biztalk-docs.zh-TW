---
title: "如何將資料複製到訊息內容，做為辨別欄位 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 004a13ca-a162-4a5e-9f72-8a5c55bbb7a6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ea68bc0b83c5a8f886416107e1dc98ea8ad8d30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-data-to-the-message-context-as-distinguished-fields"></a>如何將資料複製到訊息內容做為辨別欄位
本主題提供逐步指示將屬性升級為**辨別欄位**。  
  
 您可能會選擇**辨別欄位**升級，而不**屬性欄位**升級，原因如下：  
  
-   **屬性欄位**值的限制為 255 個字元的長度。  
  
-   **屬性欄位**值會儲存在資料庫中，，因此需要更多成本負擔比**辨別欄位**。 **辨別欄位**不需要任何額外的存放裝置; 它們是基本上別名**XPath**，因此能讓協調流程可以更輕鬆地從訊息中直接存取相關的值。  
  
### <a name="to-promote-a-property-as-a-distinguished-field"></a>升級做為辨別欄位的屬性  
  
1.  在 [BizTalk 編輯器] 中，開啟您要升級一或多個屬性的結構描述，然後選取 （第一個）**欄位項目**，**欄位屬性**，或**記錄**節點您想要升級作為**辨別欄位**。  
  
    > [!NOTE]
    >  記錄節點永遠不會升級為**辨別欄位**，不論它們包含的內容類型。  
  
2.  以滑鼠右鍵按一下選取的節點中，按一下**升階**，然後按一下 **顯示升級**。  
  
     **升級屬性**對話方塊隨即開啟與選取的節點顯示為已選取對話方塊左側的結構描述樹狀目錄中的工作。  
  
3.  在**升級屬性**對話方塊中，選取**辨別欄位** 索引標籤。  
  
4.  與要升級仍左邊的結構描述樹狀目錄中選取節點**升級屬性**對話方塊中，按一下 **新增**。  
  
     如果允許，選取的節點加入至清單上**辨別欄位** 索引標籤。若不允許，則訊息方塊會提供解釋。  
  
5.  您可以在對話方塊中按一下左邊的結構描述樹狀目錄中選取用於升級的其他節點**新增**之後每個選取項目。  
  
6.  完成後，按**確定**。  
  
     您已選取要升級的節點現在都會**辨別欄位**。  
  
## <a name="see-also"></a>另請參閱  
 [升級屬性](../core/promoting-properties.md)   
 [如何建立屬性結構描述](../core/how-to-create-property-schemas.md)   
 [使用訊息內容控制訊息處理方式](../core/ways-to-use-message-content-to-control-message-processing.md)