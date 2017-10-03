---
title: "一般檔案訊息內文 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 097e49a1-75d2-44a4-9372-d78de7b7597c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2de8748d9a36c817f7db8fed96a59c8d2bd7dda2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-message-bodies"></a>一般檔案訊息內文
一般檔案執行個體訊息內文為必要項目，一般檔案解譯器會將其處理為一或多個 XML 執行個體訊息。 若要知道在內送一般檔案執行個體訊息內文中有哪些資料，您必須使用與內文對應的一般檔案結構描述來設定一般檔案解譯器。 您可以使用指定的結構描述**文件結構描述**的一般檔案解譯器的設計階段屬性或**XMLNORM。DocumentSpecName**訊息內容屬性。 因為一般檔案執行個體訊息必須要有內文部分，所以，您必須使用這兩個方法其中一個來設定適當的結構描述。  
  
 如為輸出一般檔案執行個體訊息，一般檔案組合器可以為執行個體訊息的內文動態決定適當的一般檔案結構描述。 一般檔案組合器會從訊息類型決定適當的結構描述，它是目標命名空間與根項目名稱兩者的組合，而這兩者都必須存在於輸出訊息的 XML 版本中。 或者，您可以明確地設定可供設定的一般檔案結構描述**文件結構描述**的一般檔案組合器的設計階段屬性或**XMLNORM。DocumentSpecName**訊息內容屬性。  
  
 透過指定一般檔案解譯器所使用之一般檔案結構描述中的屬性升級，來處理輸入執行個體訊息，就可以將在輸入一般檔案執行個體訊息內文中找到的資料複製到對應的訊息內容。 同樣地，透過指定一般檔案組合器所使用之一般檔案結構描述中的屬性降級，來處理輸出訊息，就可以將訊息內容中的資料複製回輸出一般檔案執行個體訊息中。  
  
## <a name="see-also"></a>另請參閱  
 [一般檔案訊息標頭](../core/flat-file-message-headers.md)   
 [一般檔案訊息結尾](../core/flat-file-message-trailers.md)   
 [一般檔案訊息的結構](../core/structure-of-a-flat-file-message.md)   
 [如何建立一般檔案訊息的結構描述](../core/how-to-create-schemas-for-flat-file-messages.md)