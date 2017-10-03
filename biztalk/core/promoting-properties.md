---
title: "升級屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties, promoting
- promoting properties
- promoting properties, about promoting properties
ms.assetid: e1825028-7dd9-4eae-a383-4db12a83a402
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1c5ac3e6e9aeadccc4eaefcb1457821ef36a93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="promoting-properties"></a>升級屬性
升級屬性牽涉到將**欄位項目**或**欄位屬性**是結構描述中的節點**辨別欄位**或**屬性欄位**。 您也可以升級**記錄**節點做為**屬性欄位**有簡單內容 (**內容型別**屬性**記錄**節點設定為**SimpleContent**)。 本節提供逐步指示，將節點升級為 **辨別欄位**或**屬性欄位**。  
  
 若要升級**記錄**（具有簡單內容）、**欄位項目**，或**欄位屬性**節點，做為**屬性欄位**，您可以先定義特殊類型的結構描述也稱為屬性結構描述。 屬性結構描述定義的非結構化的集合**欄位項目**在您升級到其中的節點**記錄**（具有簡單內容）、**欄位項目**，或**欄位屬性**節點。 建立屬性結構描述的逐步指示，請參閱[如何建立屬性結構描述](../core/how-to-create-property-schemas.md)。  
  
 或者，您可以使用**快速升級**功能，它會自動建立並更新單一屬性結構描述，只要當您升級新**欄位項目**，**欄位屬性**，或**記錄**（具有簡單內容） 節點。  
  
> [!NOTE]
>  您可以將欄位同時升級**辨別欄位**和**屬性欄位**。  
  
> [!NOTE]
>  **快速升級**功能插入具有升級的節點名稱的新屬性，藉以修改屬性結構描述。  
  
> [!IMPORTANT]
>  一旦您升級結構描述中的欄位之後，就不能將它移動或重新命名。 當您移動或重新命名結構描述欄位時，BizTalk 編輯器不會更新用來定義升級欄位位置的 XPath。  
  
## <a name="xsd-and-clr-data-types"></a>XSD 與 CLR 資料型別  
 在某些地方，例如在屬性升級中，XSD 資料型別會升級為 Common Language Runtime (CLR) 資料型別。 下表顯示可以升級的 XSD 資料型別以及對應的 CLR 資料型別。  
  
|XSD 資料型別|CLR 資料類型|  
|-------------------|-------------------|  
|anyURI|字串|  
|布林|布林|  
|Byte|sbyte|  
|日期|DateTime|  
|dateTime|DateTime|  
|Decimal|Decimal|  
|Double|Double|  
|ENTITY|字串|  
|Float|Single|  
|gDay|DateTime|  
|gMonth|DateTime|  
|gMonthDay|DateTime|  
|gYear|DateTime|  
|gYearMonth|DateTime|  
|ID|字串|  
|IDREF|字串|  
|int|Int32|  
|Integer|Decimal|  
|語言|字串|  
|名稱|字串|  
|NCName|字串|  
|negativeInteger|Decimal|  
|NMTOKEN|字串|  
|nonNegativeInteger|Decimal|  
|nonPositiveInteger|Decimal|  
|normalizedString|字串|  
|NOTATION|字串|  
|positiveInteger|Decimal|  
|QName|字串|  
|Short|Int16|  
|字串|字串|  
|Time|DateTime|  
|Token|字串|  
|unsignedByte|Byte|  
|unsignedInt|UInt32|  
|unsignedShort|UInt16|  
  
> [!NOTE]
>  XSD 的資料型別 base64Binary、duration、ENTITES、hexBinary、IDREFS、long、NMTOKENS 和 unsignedLong 不支援升級。  
  
## <a name="limitations-for-promoting-properties"></a>升級屬性的限制  
 在升級屬性時請考量下列事項：  
  
-   升級屬性的長度有 256 個字元的限制，但是寫入屬性並無長度限制。  
  
-   升級屬性是用於訊息路由中，且基於比較與儲存效率的原因，所以在大小上會有所限制。 雖然寫入屬性在大小上並無嚴格限制，在內容中使用過大的值會影響效能，因為這些值仍會被處理並與訊息一起傳遞。 [辨別欄位] 即為寫入屬性的範例。  
  
-   記錄節點永遠不會升級為**辨別欄位**。  
  
-   升級屬性僅限非重複項目/屬性。  
  
-   請勿將屬於相同根節點的欄位升級至相同的屬性。 這類升級會產生編譯或部署錯誤。  
  
-   在訊息內容中無法使用部分屬性，這是因為這些屬性尚未升級。  BTS.ReceiveLocationName 屬性即為其中一個屬性。 如果您可以將新的屬性結構描述或新的 BizTalk Server 專案加到開發中，就有辦法從協調流程中存取這個屬性。  
  
     屬性值是以屬性目標命名空間和屬性名稱來識別。  下列範例顯示如何以程式碼存取接收位置。  
  
     `string receiveLocationName =       pInMsg.Context.Read("ReceiveLocationName", sysNamespace);`  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何開啟升級屬性對話方塊](../core/how-to-open-the-promote-properties-dialog-box.md)  
  
-   [如何將資料複製到訊息內容做為辨別欄位](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)  
  
-   [如何將資料複製到訊息內容做為屬性欄位](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)