---
title: 一般檔案訊息的結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00f2adf6-a47c-498b-b5ae-c6bd55bafceb
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: badb8aacf6f2ed8ce9e38f1ea6bbe432a1d3b89e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278934"
---
# <a name="structure-of-a-flat-file-message"></a>一般檔案訊息的結構
在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的內容中，一般檔案執行個體訊息是包含三種邏輯部分的文字檔：依序為標頭、內文及結尾。 標頭和結尾為選擇性。 下列範例將顯示包含這三個部分的一般檔案執行個體訊息，其中內文是以粗體顯示。  
  
```  
Microsoft Corporation  
One Microsoft Way  
Redmond, WA 98033  
  
TRANSACTION-1111,1  
  
```  
  
 為了讓一般檔案解譯器能夠正確地辨識一般檔案執行個體訊息的標頭、內文及結尾，您必須各別為其建立和設定各自的結構描述。  
  
 在一般檔案執行個體訊息的特定部分，分組資料的不同項目記錄，到哪一個本身可以包含子記錄和最終的資料，又稱為欄位的個別項目。 這些記錄及欄位可以使用兩種不同的基本方法之一來加以識別。 第一種方法 (稱為位置) 會定義每個資料項目預先建立的長度，且若資料項目長度短於預期的長度則會使用填補字元填滿。 第二種方法 (稱為分隔) 會使用一或多個特殊字元來區分每個資料項目。 此方法能避免多餘的填補字元，但在資料本身包含用來當作分隔符號的字元或字元序列時，需要一些特殊考量。  
  
 接下來將提供 BizTalk Server 如何處理一般檔案執行個體訊息之標題、內文及結尾的簡要說明，尤其是它如何判斷選擇性的部分是否存在，以及如何分隔輸入一般檔案執行個體訊息，以及結合輸出一般檔案執行個體訊息。 本節也會提供採用位置記錄及欄位的一般檔案執行個體訊息，與採用分隔記錄及欄位的一般檔案執行個體訊息之間相異處的其他資訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [一般檔案訊息標頭](../core/flat-file-message-headers.md)  
  
-   [一般檔案訊息內文](../core/flat-file-message-bodies.md)  
  
-   [一般檔案訊息結尾](../core/flat-file-message-trailers.md)  
  
-   [具有位置記錄的一般檔案訊息](../core/flat-file-messages-with-positional-records.md)  
  
-   [具有分隔記錄的一般檔案訊息](../core/flat-file-messages-with-delimited-records.md)  
  
-   [移轉一般檔案記錄](../core/migrating-flat-file-records.md)