---
title: 使用辨別的欄位和屬性欄位 |Microsoft 文件
description: 閱讀 [辨別] 欄位、 屬性欄位和屬性集之間的差異。 辨別的欄位使用的路徑，在 [訊息] 欄位中，屬性欄位會使用郵件名稱和結構描述命名空間，並且屬性集，將一則訊息 （屬性集） 的內容屬性指派給 BizTalk Server 中的另一個訊息的內容屬性
ms.custom: ''
ms.date: 05/02/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 264ee15e-be9a-4ba2-9c61-a1570b20378e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2dc6233f71bb56fe831fded343e6557292cdb315
ms.sourcegitcommit: 3371ffd8ceca02e2b3715d53a1e0c0a59045912e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34848902"
---
# <a name="using-distinguished-fields-and-property-fields"></a>使用辨別的欄位和屬性欄位
辨別欄位是您在協調流程中制定決策或是操控資料時，主要所使用的有用訊息資料。  
  
 訊息屬性是資料 (訊息本身的內容) 或「中繼資料」(訊息相關資訊的內容，例如時間戳記或路由資訊)。 您可以使用系統定義的訊息內容屬性或傳輸內容屬性，也可以從屬性結構描述中參考結構描述欄位來定義自己的屬性。 屬性會用於訂閱和相互關聯。  
  
-   您可以將結構描述中的欄位指定為辨別的欄位或屬性欄位使用**升級屬性**對話方塊編輯器中的。 如需詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)  
  
-   您可以使用 DistinguishedField 屬性 (Attribute) 裝飾 .NET 類型中的欄位，將它指定為辨別欄位；或者以 Property 屬性來裝飾，將它指定為屬性 (Property)。  
  
## <a name="using-distinguished-fields"></a>使用辨別欄位  
 辨別欄位是由訊息中欄位的路徑所參考，並使用句號來分隔訊息名稱、任何包含欄位之記錄的名稱與欄位名稱本身：  
  
```  
MyMessage.MyRecord.MySubrecord.MyDistinguishedField  
```  
  
## <a name="using-property-fields"></a>使用屬性欄位  
 將某個欄位加入至屬性結構描述之後，您就可以利用程式碼和篩選條件運算式，在協調流程中存取其值。 如需屬性結構描述的詳細資訊，請參閱[屬性結構描述](../core/property-schemas.md)。  
  
> [!NOTE]
>  訊息內容或資料屬性是基本上是基礎資料的捷徑： 如果您修改屬性時，資料會被修改，反之亦然。  
  
 訊息屬性是由訊息名稱所參考，此名稱後面跟隨著以括號包住的命名空間 (結構描述) 及屬性名稱：  
  
```  
MyMessage(Invoice.PropertySchema.InvoiceID)  
```  
  
> [!NOTE]
>  當您使用保留的關鍵字做為結構描述中的欄位名稱和您選取 [快速升級] 升級欄位時，欄位的屬性名稱變更為 __\<保留的關鍵字\>。 (屬性名稱前會加上兩個底線)。不過，如果在協調流程運算式中使用這個屬性名稱，您將會在建置協調流程時收到編譯器錯誤。  若要解決這個錯誤，您必須手動加入\@在雙底線前面。 例如，  
>   
>  `MyMessage(Invoice.PropertySchema.@__Name) = "Product Name";`  
  
## <a name="property-sets"></a>屬性集  
 您也可以將一個訊息的所有內容屬性 (屬性集) 指派給另一個訊息的內容屬性。 若要指派屬性集，只需在兩個訊息名稱之後的括號中放置星號，就和您將屬性放在括號中一樣：  
  
```  
MyMessage2(*)=MyMessage1(*);  
```  
  
 將屬性集指派給範例中的 MyMessage2 之後，MyMessage2 中的所有屬性都會包含與 MyMessage1 之屬性相同的值。  
  
## <a name="see-also"></a>另請參閱  
 [升級屬性](../core/promoting-properties.md)   
 [使用篩選器與接收訊息 」 圖形](../core/using-filters-with-the-receive-message-shape.md)   
 [協調流程中使用訊息](../core/using-messages-in-orchestrations.md)   
 [關於 BizTalk 訊息內容屬性](../core/about-biztalk-message-context-properties.md)
