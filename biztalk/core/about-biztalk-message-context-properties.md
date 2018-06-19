---
title: 關於 BizTalk 訊息內容屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc700e43-a44c-482b-b91c-9f1d997a486a
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49d802ad2ca50538c25182311c68604c26d5a832
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225494"
---
# <a name="about-biztalk-message-context-properties"></a>關於 BizTalk 訊息內容屬性
BizTalk Server 配接器在收到文件時，會為該文件建立 BizTalk 訊息。 BizTalk 訊息包含收到的文件及訊息內容。 訊息內容是 BizTalk Server 處理文件時使用的各種屬性之容器。 「訊息內容」中的每個屬性都由三種項目構成：名稱、命名空間和值。 例如，下列訊息內容屬性描述文件的「交換 ID」：  
  
```  
<Property Name="InterchangeID" Namespace="http://schemas.microsoft.com/BizTalk/2003/system-properties" Value="{AC07BF30-2F1A-42B0-8390-191EF38BA839}"/>  
```  
  
 訊息內容屬性會在訊息通過 BizTalk Server 的存留期間新增至訊息內容中。  
  
 BizTalk 使用兩種不同類型的訊息內容屬性，描述如下：  
  
## <a name="property-fields"></a>屬性欄位  
 屬性欄位是「BizTalk Server 傳訊引擎」使用的訊息內容屬性，用於傳遞文件、追蹤訊息及在協調流程中進行評估。 您可在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 提供的「BizTalk Server 結構描述編輯器」中編輯文件的結構描述，明確地將文件中的欄位提升為訊息內容中的 [屬性] 欄位。 為了將文件中的欄位寫入訊息內容做為屬性欄位，文件結構描述必須具有相關聯的屬性結構描述。 [屬性] 欄位的限制是 255 個字元。 **IsPromoted**訊息內容中的 [屬性] 欄位的屬性設定為**True**。  
  
## <a name="distinguished-fields"></a>辨別欄位  
 [辨別] 欄位是不需要個別屬性結構描述的訊息內容屬性，並且只能從協調流程存取。 [辨別] 欄位不能用於路由或追蹤。 由於 [辨別] 欄位不需要個別屬性結構描述，協調流程引擎評估 [辨別] 欄位時所造成的負擔，會小於評估 [屬性] 欄位時所造成的負擔。 評估 [屬性] 欄位需要 XPath 查詢，評估 [辨別] 欄位則不需要 XPath 查詢，因為管線解譯器會填入內容中的 [辨別] 欄位，而且協調流程引擎也會讀取快取值。 不過，如果協調流程引擎在內容中找不到該屬性，則會起始 XPath 查詢來尋找值。 [辨別] 欄位沒有大小限制。 **IsPromoted**辨別 欄位中的訊息內容屬性設定為**False**。  
  
## <a name="summary-of-differences-between-property-fields-and-distinguished-fields"></a>屬性欄位和辨別欄位的差異摘要  
 下表摘總結 [屬性] 欄位和 [辨別] 欄位的相異處和相似處：  
  
|**Attribute**|**屬性欄位**|**辨別的欄位**|  
|-------------------|------------------------|-----------------------------|  
|IsPromoted 屬性|True|False|  
|大小限制|255 個字元|無限制|  
|用於路由|是|否|  
|用於追蹤|是|否|  
|用於協調流程中|是|是|  
|需要屬性結構描述|是|否|  
|可透過管線和連接埠存取|是|否|  
  
## <a name="see-also"></a>另請參閱  
 [使用訊息內容控制訊息處理方式](../core/ways-to-use-message-content-to-control-message-processing.md)