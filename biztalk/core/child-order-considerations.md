---
title: 子順序考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4f7aa81-5c08-4932-9e28-31e22e037999
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0909a8d69f5079e493fbc579d6ef4b0ca56f9c61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232734"
---
# <a name="child-order-considerations"></a><span data-ttu-id="7274a-102">子順序考量</span><span class="sxs-lookup"><span data-stu-id="7274a-102">Child Order Considerations</span></span>

## <a name="requirements-for-header-in-a-flat-file"></a><span data-ttu-id="7274a-103">一般檔案中的標頭的需求</span><span class="sxs-lookup"><span data-stu-id="7274a-103">Requirements for header in a flat file</span></span>
<span data-ttu-id="7274a-104">有兩種案例相關的特殊考量套用設定時的分隔式一般檔案**子系順序**屬性。</span><span class="sxs-lookup"><span data-stu-id="7274a-104">There are two scenarios related to delimited flat files for which special considerations apply when setting the **Child Order** property.</span></span> <span data-ttu-id="7274a-105">第一個實例是與一般檔案文件具有標頭、內文及結尾 (選擇性) 的情況相關。</span><span class="sxs-lookup"><span data-stu-id="7274a-105">The first such scenario concerns situations in which the flat file document has a header, a body, and optionally, a trailer.</span></span> <span data-ttu-id="7274a-106">在這些實例中，您必須遵守下列需求：</span><span class="sxs-lookup"><span data-stu-id="7274a-106">In these scenarios, you must observe the following requirements:</span></span>  
  
-   <span data-ttu-id="7274a-107">您必須設定**子系順序**屬性標頭的 （分隔） 根記錄**後置**。</span><span class="sxs-lookup"><span data-stu-id="7274a-107">You must set the **Child Order** property of the (delimited) root record of the header to **Postfix**.</span></span>  
  
-   <span data-ttu-id="7274a-108">如果結尾已存在，則必須設定**子系順序**屬性的內文的 （分隔） 根記錄**後置**。</span><span class="sxs-lookup"><span data-stu-id="7274a-108">If a trailer is present, you must set the **Child Order** property of the (delimited) root record of the body to **Postfix**.</span></span>  
  
-   <span data-ttu-id="7274a-109">如果沒有結尾，您可能設定**子系順序**的內文的 （分隔） 根記錄的屬性**首碼**，**中置**，或**後置**.</span><span class="sxs-lookup"><span data-stu-id="7274a-109">If a trailer is not present, you may set the **Child Order** property of the (delimited) root record of the body to **Prefix**, **InFix**, or **Postfix**.</span></span>  
  
-   <span data-ttu-id="7274a-110">如果結尾已存在，您可能設定**子系順序**（分隔） 根記錄，到該結尾屬性**首碼**，**中置**，或**後置**.</span><span class="sxs-lookup"><span data-stu-id="7274a-110">If a trailer is present, you may set the **Child Order** property of the (delimited) root record of that trailer to **Prefix**, **InFix**, or **Postfix**.</span></span>  
  
-   <span data-ttu-id="7274a-111">您可以設定**子系順序**屬性標頭、 內文和結尾中的，以分隔附屬記錄**前置詞**，**中置**，或**後置**.</span><span class="sxs-lookup"><span data-stu-id="7274a-111">You may set the **Child Order** property of delimited subordinate records of the header, body, and trailer to **Prefix**, **InFix**, or **Postfix**.</span></span>  
  
 <span data-ttu-id="7274a-112">第二個相關的實例分隔式一般檔案和**子系順序**屬性是根據針對節點預期的執行階段元件，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="7274a-112">The second scenario related to delimited flat files and the **Child Order** property is that this property must be set according to what the runtime components expect for the nodes.</span></span> <span data-ttu-id="7274a-113">正確設定**子系順序**屬性可能不明顯，根和群組 節點，如下列案例中所示：</span><span class="sxs-lookup"><span data-stu-id="7274a-113">The correct setting for the **Child Order** property may not be apparent for root and group nodes, as illustrated in the following scenarios:</span></span>  
  
-   <span data-ttu-id="7274a-114">**根節點。**</span><span class="sxs-lookup"><span data-stu-id="7274a-114">**Root node.**</span></span> <span data-ttu-id="7274a-115">假設有一個典型的一般檔案，其結構是由記錄後面加上 CR/LF 的組合所構成。</span><span class="sxs-lookup"><span data-stu-id="7274a-115">Consider a typical flat file whose structure consists of records followed by a CR/LF combination.</span></span> <span data-ttu-id="7274a-116">分隔符號會分隔檔案中的記錄，且順序通常是記錄、分隔符號、記錄、分隔符號等等。</span><span class="sxs-lookup"><span data-stu-id="7274a-116">The delimiter separates records in the file, and the sequence is typically record, delimiter, record, delimiter, and so on.</span></span> <span data-ttu-id="7274a-117">在此情況下，分隔符號一律會跟資料，對應至**子系順序**屬性設定為**後置**。</span><span class="sxs-lookup"><span data-stu-id="7274a-117">In this situation, the delimiter always follows the data, which corresponds to a **Child Order** property setting of **Postfix**.</span></span>  
  
-   <span data-ttu-id="7274a-118">**群組節點。**</span><span class="sxs-lookup"><span data-stu-id="7274a-118">**Group nodes.**</span></span> <span data-ttu-id="7274a-119">顯示在 BizTalk Server 和結構描述之 XSD 表示法中的群組節點不會明確出現在執行個體訊息的一般檔案表示法中。</span><span class="sxs-lookup"><span data-stu-id="7274a-119">The group nodes shown in the BizTalk Server and XSD representation of the schema are not explicitly present in the flat file representation of the instance message.</span></span> <span data-ttu-id="7274a-120">假設有一筆訂單 (PO) 包含每個明細項目記錄之集合，而這些記錄會重複多次來表示單一 PO 中的多個明細項目。</span><span class="sxs-lookup"><span data-stu-id="7274a-120">Consider a purchase order (PO) that contains a collection of records for each line item, and those records repeat numerous times to represent multiple line items in a single PO.</span></span> <span data-ttu-id="7274a-121">這類訊息的結構描述可能會包含名為 LineItems 做為 （有時是概念性的） 重複集容器的節點： 在執行個體訊息的一般檔案表示法，LineItems 容器是概念性的本質，由資料和分隔符號，適當的順序在執行個體訊息的 XML 表示法，LineItems 容器是明確的形式出現**LineItems**中 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="7274a-121">The schema for such a message would likely include a node named LineItems to serve as the (sometimes conceptual) container for the repeating set: in the flat file representation of the instance message, the LineItems container is conceptual in nature, represented by the appropriate sequence of data and delimiters; in the XML representation of the instance message, the LineItems container is explicitly present in the form of a **LineItems** element in XML.</span></span>  
  
 <span data-ttu-id="7274a-122">假設有一個訊息包含根節點並僅含有一個群組節點。</span><span class="sxs-lookup"><span data-stu-id="7274a-122">Consider a message containing a root node and only one group node.</span></span> <span data-ttu-id="7274a-123">我們可以很容易看出，輸入資料流的最後一個分隔符號會屬於根節點。</span><span class="sxs-lookup"><span data-stu-id="7274a-123">It is easy to see where the last delimiter in the input stream would belong to the root node.</span></span> <span data-ttu-id="7274a-124">因此，概念性迴圈中的資料/分隔符號順序，就只不過是一或多筆明細項目記錄。</span><span class="sxs-lookup"><span data-stu-id="7274a-124">Therefore, the data/delimiter sequence in the conceptual loop would merely be one or more line item records.</span></span> <span data-ttu-id="7274a-125">只有在超過一筆明細項目記錄的情況下，才會有分隔符號來分隔它們。</span><span class="sxs-lookup"><span data-stu-id="7274a-125">Only in the case where there are more than one line item records would there be a delimiter to separate them.</span></span> <span data-ttu-id="7274a-126">因此，分隔符號的數目會比被分隔的項目組少一，且分隔符號會位於被分隔的項目之間，此結構稱為 [中置]。</span><span class="sxs-lookup"><span data-stu-id="7274a-126">In that case, the number of delimiters is one less than the sets of things being delimited, and the delimiters are located between the delimited items in a structure known as Infix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7274a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7274a-127">See Also</span></span>  
-  [<span data-ttu-id="7274a-128">分隔記錄的考量</span><span class="sxs-lookup"><span data-stu-id="7274a-128">Delimited Record Considerations</span></span>](../core/delimited-record-considerations.md)   
-  <span data-ttu-id="7274a-129">**Child Order （一般檔案結構描述中的節點屬性）**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="7274a-129">**Child Order (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>