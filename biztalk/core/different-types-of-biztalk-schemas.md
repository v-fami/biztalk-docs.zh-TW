---
title: 不同類型的 BizTalk 結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8847d3-6f0e-4982-b4a8-92a5f39a4b48
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 051cd8fb9824cece316ea6f56e318490eacf88c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240278"
---
# <a name="different-types-of-biztalk-schemas"></a>不同類型的 BizTalk 結構描述
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援下列四種類型的結構描述：  
  
-   **XML 結構描述**。 XML 結構描述定義 XML 執行個體訊息類別的結構。 由於這種類型的結構描述是使用 XML 結構描述定義 (XSD) 語言定義 XML 執行個體訊息的結構，而這正是 XSD 的用途，所以這類結構描述會以直接的方式使用 XSD。  
  
-   **一般檔案結構描述**。 一般檔案結構描述是用來定義使用一般檔案格式 (分隔或位置或這兩者的組合) 的執行個體訊息類別之結構。 由於 XSD 的原生語意功能無法滿足定義一般檔案執行個體訊息結構的所有需求 (例如可用於一般檔案中不同記錄和欄位的各種分隔符號)，因此，BizTalk Server 使用了 XSD 的註解功能，將此額外資訊儲存在 XSD 結構描述中。 BizTalk Server 定義了一組豐富的特定註解標記，可用來儲存所有必要的額外資訊。  
  
-   **信封結構描述**。 信封結構描述是特殊類型的 XML 結構描述。 信封結構描述是用來定義 XML 信封的結構，可用來將一或多個 XML 商務文件包裝成單一 XML 執行個體訊息。 將 XML 結構描述定義為信封結構描述時，根據信封結構描述中是否定義了一個以上的根記錄而定，會需要一些其他的屬性設定。  
  
-   **屬性結構描述**。 屬性結構描述是與 BizTalk Server 中所具有的兩種機制之一搭配使用，該種機制稱之為屬性升級。 屬性升級是將執行個體訊息內的特定值複製到訊息內容的程序。 透過訊息內容，這些值可以更容易被各種 BizTalk Server 元件存取。 這些元件可使用這些值來執行訊息路由等動作。 您也可以依相反方向複製升級的屬性值 (從較容易存取的訊息內容複製回執行個體訊息內)，只要是在執行個體訊息傳送到目的地之前即可。 屬性結構描述是 BizTalk 結構描述的簡單版本，在執行個體訊息與訊息內容之間來回複製升級屬性的過程中會使用到。  
  
 本節其餘部分會提供有關 BizTalk Server 中這四種類型的結構描述之詳細資訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [XML 結構描述](../core/xml-schemas.md)  
  
-   [一般檔案結構描述](../core/flat-file-schemas.md)  
  
-   [信封結構描述](../core/envelope-schemas.md)  
  
-   [屬性結構描述](../core/property-schemas.md)