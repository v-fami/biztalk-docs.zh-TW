---
title: "執行個體訊息使用辨別欄位處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b8f3f77-5385-4294-b441-bcb28bdc51b4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4dca22ff1b09a0d1cfb261a9d5726da8b1b17b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="instance-message-processing-using-distinguished-fields"></a>使用辨別欄位處理執行個體訊息
使用升級屬性**辨別欄位**機制不需要建立屬性結構描述。 當您使用所有屬性升級，**升級屬性**對話方塊中，以存取使用**升級屬性**屬性**結構描述**中的節點訊息結構描述，或使用**升階 &#124;顯示升級**命令**BizTalk**或捷徑功能表。  
  
 在**升級屬性**對話方塊方塊中，確認**辨別欄位**選取在對話方塊右邊索引標籤。 然後展開的節點在結構描述樹狀目錄中，尋找並選取對話方塊左側**欄位項目**節點或**欄位屬性**您想要升級為辨別欄位的節點，然後按一下**新增**。 如需升級屬性的逐步指示**辨別欄位**使用**升級屬性** 對話方塊中，請參閱[複製資料至訊息內容做 Distinguished欄位](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)。  
  
> [!NOTE]
>  您也可以升級**記錄**節點至欄位項目中的節點屬性結構描述，但是只有**內容類型**屬性**記錄**節點設定為**SimpleContent**。  
  
 若要移除的一組要升級為辨別欄位屬性節點，選取 升級的屬性上**辨別欄位**索引標籤，然後按一下**移除**。  
  
 當您使用辨別欄位機制升級屬性時，會在根項目的註解子項目中新增 XML 結構描述定義 (XSD) 語言片段。 在下列範例中，片段顯示使用辨別欄位機制升級的兩個屬性。  
  
```  
<b:properties>  
    <b:property distinguished="true"  
        xpath="/*[local-name()='Record' and namespace-  
         uri()='http://BizTalk_Server_Project1.Schema11']/*[local-  
         name()='test']/*[local-name()='Field1']" />  
    <b:property distinguished="true"  
        xpath="/*[local-name()='Record' and namespace-  
         uri()='http://BizTalk_Server_Project1.Schema11']/*[local-  
         name()='test']/*[local-name()='Field5' and position()='1']" />  
</b:properties>  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用訊息內容控制訊息處理方式](../core/ways-to-use-message-content-to-control-message-processing.md)   
 [如何將資料複製到訊息內容做為辨別欄位](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)