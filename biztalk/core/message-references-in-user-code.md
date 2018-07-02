---
title: 訊息中使用者程式碼的參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a1584be-35fd-4dc2-a5a9-559300e67e0e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71e73eb9b953e514e48ae4e927ec3e4c104feb43
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972495"
---
# <a name="message-references-in-user-code"></a><span data-ttu-id="25894-102">使用者程式碼中的訊息參考</span><span class="sxs-lookup"><span data-stu-id="25894-102">Message References in User Code</span></span>
<span data-ttu-id="25894-103">在建構訊息時，訊息的某一表示法會儲存在 MessageBox 資料庫，另一個表示法則會儲存在電腦的記憶體。</span><span class="sxs-lookup"><span data-stu-id="25894-103">When a message is constructed, a representation of the message is in the MessageBox database and another representation is in memory on the computer.</span></span> <span data-ttu-id="25894-104">如果您將訊息參考傳送至 .NET 物件或外部組件進行訊息指派，接著此 .NET 物件或外部組件修改電腦記憶體中的表示法，則 BizTalk 協調流程引擎不會知道此修改。</span><span class="sxs-lookup"><span data-stu-id="25894-104">If you make the message assignment by passing a message reference to a .NET object or to an external assembly, and then the .NET object or the external assembly modifies the representation in memory on the computer, the BizTalk Orchestration Engine is not aware of the modification.</span></span>  
  
 <span data-ttu-id="25894-105">而且，協調流程引擎也不會使 MessageBox 資料庫中之表示法的訊息部分資料無效。</span><span class="sxs-lookup"><span data-stu-id="25894-105">Moreover, the orchestration engine does not invalidate the message part data that is in the representation in the MessageBox database.</span></span> <span data-ttu-id="25894-106">訊息部分資料有下列各種表示法：</span><span class="sxs-lookup"><span data-stu-id="25894-106">Message part data has the following modes of representation:</span></span>  
  
- <span data-ttu-id="25894-107">XmlDocument 表示法</span><span class="sxs-lookup"><span data-stu-id="25894-107">XmlDocument representation</span></span>  
  
- <span data-ttu-id="25894-108">物件表示法</span><span class="sxs-lookup"><span data-stu-id="25894-108">Object representation</span></span>  
  
- <span data-ttu-id="25894-109">資料流表示法</span><span class="sxs-lookup"><span data-stu-id="25894-109">Stream representation</span></span>  
  
- <span data-ttu-id="25894-110">UnderlyingPart 表示法</span><span class="sxs-lookup"><span data-stu-id="25894-110">UnderlyingPart representation</span></span>  
  
  <span data-ttu-id="25894-111">訊息部分資料在記憶體中的表示方式取決於訊息建構，以及類型為 .NET 類別還是 XML 結構描述定義語言 (XSD) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="25894-111">How the message part data is represented in memory depends on the message construction and whether the type is a .NET class or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="25894-112">不過，UnderlyingPart 表示法永遠是指向 MessageBox 資料庫的資料流。</span><span class="sxs-lookup"><span data-stu-id="25894-112">However, the UnderlyingPart representation is always a stream pointing into the MessageBox database.</span></span> <span data-ttu-id="25894-113">因為 BizTalk Server 中的訊息在 MessageBox 資料庫認可後即無法改變，所以協調流程引擎會使用 MessageBox 資料庫中的表示法來參考訊息部分資料。</span><span class="sxs-lookup"><span data-stu-id="25894-113">Because messages in BizTalk Server are immutable after the message is committed to the MessageBox database, the orchestration engine uses the representation in the MessageBox database to reference message part data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25894-114">如果您從已認可的訊息中指定某些部分，MessageBox 資料庫可能已有所建構之訊息的表示法。</span><span class="sxs-lookup"><span data-stu-id="25894-114">A constructed message may already have a representation in the MessageBox database if you assign parts from a message that is already committed.</span></span>  
  
 <span data-ttu-id="25894-115">例如，下列程式碼會從 MessageBox 資料庫中的表示法傳送 UnderlyingPart 資料。</span><span class="sxs-lookup"><span data-stu-id="25894-115">For example, the following code sends the UnderlyingPart data from the representation in the MessageBox database:</span></span>  
  
```  
// In this example, assume m1 is committed to the MessageBox  
Construct m2 {   
               m2 = m1; // m2’s part data representation is the UnderlyingPart data of m1  
               m2(myContextProperty) = “123”; // m2’s part data representation is still the UnderlyingPart data of m1  
               A.test(m2.part); // orchestration engine does not invalidate the UnderlyingPart MessageBox representation  
             }  
Send(p.o, m2);  
```  
  
 <span data-ttu-id="25894-116">如果不使用以上的使用者程式碼，您也可以使用類似下列的程式碼，將 XmlDocument 文件傳回至訊息 XLANG 變數：</span><span class="sxs-lookup"><span data-stu-id="25894-116">Instead of using the preceding user code, you can use code that is similar to the following to return an XmlDocument document to a Message XLANG variable:</span></span>  
  
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