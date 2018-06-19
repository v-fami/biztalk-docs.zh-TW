---
title: 一般檔案訊息標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1981daaf-149a-426d-9a2f-5fcf64bce185
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 271e9fe74d0a55f4b3ff5271861d24474fffaf37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246350"
---
# <a name="flat-file-message-headers"></a>一般檔案訊息標頭
選擇性的一般檔案執行個體訊息標頭，一般檔案解譯器剖析由您在設定一般檔案結構描述**標頭結構描述**的一般檔案解譯器的設計階段屬性或**XMLNORM。HeaderSpecName**訊息內容屬性。 若您並未使用這兩種方法的其中一種來指定結構描述，則一般檔案解譯器就會假設一般檔案執行個體訊息沒有包含標頭。  

## <a name="outbound-messages"></a>輸出訊息  
 對於輸出一般檔案執行個體訊息，您可以設定要產生標頭指定適當的結構描述中的一般檔案組合器其**標頭規格名稱**設計階段屬性或**XMLNORM。HeaderSpecName**訊息內容屬性。 如需有關如何設定訊息內容屬性的詳細資訊，請參閱**訊息內容屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  

## <a name="inbound-messages"></a>輸入的訊息  
 輸入一般檔案執行個體訊息標頭中所找到的資料，可以透過兩種不同的方式加以保存和利用。 第一個方法是，一般檔案執行個體訊息標頭可以完整地儲存於內文的訊息內容裡，以便日後還原時，做為對應輸出一般檔案執行個體訊息的標頭。 您可以使用**保留標頭**屬性來指定，應該保留標頭的接收管線。 此外，若一般檔案組合器中指定了標頭，則輸出訊息上便會使用保留的標頭。  
  
 第二個方法是，一般檔案執行個體訊息中的個別資料項目，可以藉由指定對應結構描述中一或多個欄位的屬性升級，複製到與一般檔案訊息內文相關聯的訊息內容中。 如需有關如何升級屬性的詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [一般檔案訊息內文](../core/flat-file-message-bodies.md)   
 [一般檔案訊息結尾](../core/flat-file-message-trailers.md)   
 [一般檔案訊息的結構](../core/structure-of-a-flat-file-message.md)   
 [如何建立一般檔案訊息的結構描述](../core/how-to-create-schemas-for-flat-file-messages.md)