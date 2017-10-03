---
title: "訊息中的使用者程式碼的參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a1584be-35fd-4dc2-a5a9-559300e67e0e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 264f50da516f44d8fc87186614a79bb81aaf77ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-references-in-user-code"></a>使用者程式碼中的訊息參考
在建構訊息時，訊息的某一表示法會儲存在 MessageBox 資料庫，另一個表示法則會儲存在電腦的記憶體。 如果您將訊息參考傳送至 .NET 物件或外部組件進行訊息指派，接著此 .NET 物件或外部組件修改電腦記憶體中的表示法，則 BizTalk 協調流程引擎不會知道此修改。  
  
 而且，協調流程引擎也不會使 MessageBox 資料庫中之表示法的訊息部分資料無效。 訊息部分資料有下列各種表示法：  
  
-   XmlDocument 表示法  
  
-   物件表示法  
  
-   資料流表示法  
  
-   UnderlyingPart 表示法  
  
 訊息部分資料在記憶體中的表示方式取決於訊息建構，以及類型為 .NET 類別還是 XML 結構描述定義語言 (XSD) 結構描述。 不過，UnderlyingPart 表示法永遠是指向 MessageBox 資料庫的資料流。 因為 BizTalk Server 中的訊息在 MessageBox 資料庫認可後即無法改變，所以協調流程引擎會使用 MessageBox 資料庫中的表示法來參考訊息部分資料。  
  
> [!NOTE]
>  如果您從已認可的訊息中指定某些部分，MessageBox 資料庫可能已有所建構之訊息的表示法。  
  
 例如，下列程式碼會從 MessageBox 資料庫中的表示法傳送 UnderlyingPart 資料。  
  
```  
// In this example, assume m1 is committed to the MessageBox  
Construct m2 {   
               m2 = m1; // m2’s part data representation is the UnderlyingPart data of m1  
               m2(myContextProperty) = “123”; // m2’s part data representation is still the UnderlyingPart data of m1  
               A.test(m2.part); // orchestration engine does not invalidate the UnderlyingPart MessageBox representation  
             }  
Send(p.o, m2);  
```  
  
 如果不使用以上的使用者程式碼，您也可以使用類似下列的程式碼，將 XmlDocument 文件傳回至訊息 XLANG 變數：  
  
```  
Void A.test(ref XmlDocument xd) {…}  
XmlDocument B.test(XmlDocument xd) {…}  
construct m2 {  
               m2 = m1;  
               m2(myContextProperty) = “123”; // m2’s part data representation is the UnderlyingPart data of m1  
               A.test(ref m2.part); // orchestration engine has enough information to know it has to invalidate the UnderlyingPart MessageBox representation  
               // or  
               m2.part = B.test(m2.part); // orchestration engine has enough information to know it has to invalidate the UnderlyingPart MessageBox representation  
             }  
```