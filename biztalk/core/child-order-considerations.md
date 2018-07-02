---
title: 子順序考量 |Microsoft Docs
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
ms.openlocfilehash: ef7e2783bea6c67301c704319035ee0617296eed
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977159"
---
# <a name="child-order-considerations"></a><span data-ttu-id="d4e0e-102">子順序考量</span><span class="sxs-lookup"><span data-stu-id="d4e0e-102">Child Order Considerations</span></span>

## <a name="requirements-for-header-in-a-flat-file"></a><span data-ttu-id="d4e0e-103">一般檔案中的標頭需求</span><span class="sxs-lookup"><span data-stu-id="d4e0e-103">Requirements for header in a flat file</span></span>
<span data-ttu-id="d4e0e-104">有兩個相關的特殊考量適用於設定時的分隔式一般檔案的案例**子系順序**屬性。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-104">There are two scenarios related to delimited flat files for which special considerations apply when setting the **Child Order** property.</span></span> <span data-ttu-id="d4e0e-105">第一個實例是與一般檔案文件具有標頭、內文及結尾 (選擇性) 的情況相關。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-105">The first such scenario concerns situations in which the flat file document has a header, a body, and optionally, a trailer.</span></span> <span data-ttu-id="d4e0e-106">在這些實例中，您必須遵守下列需求：</span><span class="sxs-lookup"><span data-stu-id="d4e0e-106">In these scenarios, you must observe the following requirements:</span></span>  

- <span data-ttu-id="d4e0e-107">您必須設定**子系順序**屬性的 （分隔） 根記錄要的標頭**後置**。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-107">You must set the **Child Order** property of the (delimited) root record of the header to **Postfix**.</span></span>  

- <span data-ttu-id="d4e0e-108">若有結尾，您必須設定**子系順序**屬性的內文的 （分隔） 根記錄**後置**。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-108">If a trailer is present, you must set the **Child Order** property of the (delimited) root record of the body to **Postfix**.</span></span>  

- <span data-ttu-id="d4e0e-109">如果沒有結尾，您可以設定**子系順序**的內文的 （分隔） 根記錄的屬性**前置詞**， **InFix**，或**後置詞**.</span><span class="sxs-lookup"><span data-stu-id="d4e0e-109">If a trailer is not present, you may set the **Child Order** property of the (delimited) root record of the body to **Prefix**, **InFix**, or **Postfix**.</span></span>  

- <span data-ttu-id="d4e0e-110">若有結尾，您可以設定**子系順序**屬性以該結尾的 （分隔） 根記錄**前置詞**，**中置**，或**後置詞**.</span><span class="sxs-lookup"><span data-stu-id="d4e0e-110">If a trailer is present, you may set the **Child Order** property of the (delimited) root record of that trailer to **Prefix**, **InFix**, or **Postfix**.</span></span>  

- <span data-ttu-id="d4e0e-111">您可以設定**子系順序**屬性的標頭、 內文和結尾中的，以分隔附屬記錄**前置詞**，**中置**，或**後置**.</span><span class="sxs-lookup"><span data-stu-id="d4e0e-111">You may set the **Child Order** property of delimited subordinate records of the header, body, and trailer to **Prefix**, **InFix**, or **Postfix**.</span></span>  

  <span data-ttu-id="d4e0e-112">第二個相關的案例分隔式一般檔案和**子系順序**屬性是根據針對節點預期的執行階段元件，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-112">The second scenario related to delimited flat files and the **Child Order** property is that this property must be set according to what the runtime components expect for the nodes.</span></span> <span data-ttu-id="d4e0e-113">正確的設定，如**子系順序**屬性可能不明顯的根節點和群組節點，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d4e0e-113">The correct setting for the **Child Order** property may not be apparent for root and group nodes, as illustrated in the following scenarios:</span></span>  

- <span data-ttu-id="d4e0e-114">**根節點。**</span><span class="sxs-lookup"><span data-stu-id="d4e0e-114">**Root node.**</span></span> <span data-ttu-id="d4e0e-115">假設有一個典型的一般檔案，其結構是由記錄後面加上 CR/LF 的組合所構成。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-115">Consider a typical flat file whose structure consists of records followed by a CR/LF combination.</span></span> <span data-ttu-id="d4e0e-116">分隔符號會分隔檔案中的記錄，且順序通常是記錄、分隔符號、記錄、分隔符號等等。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-116">The delimiter separates records in the file, and the sequence is typically record, delimiter, record, delimiter, and so on.</span></span> <span data-ttu-id="d4e0e-117">在此情況下，分隔符號一律會跟資料，其對應至**子系順序**屬性設定**後置**。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-117">In this situation, the delimiter always follows the data, which corresponds to a **Child Order** property setting of **Postfix**.</span></span>  

- <span data-ttu-id="d4e0e-118">**群組節點。**</span><span class="sxs-lookup"><span data-stu-id="d4e0e-118">**Group nodes.**</span></span> <span data-ttu-id="d4e0e-119">顯示在 BizTalk Server 和結構描述之 XSD 表示法中的群組節點不會明確出現在執行個體訊息的一般檔案表示法中。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-119">The group nodes shown in the BizTalk Server and XSD representation of the schema are not explicitly present in the flat file representation of the instance message.</span></span> <span data-ttu-id="d4e0e-120">假設有一筆訂單 (PO) 包含每個明細項目記錄之集合，而這些記錄會重複多次來表示單一 PO 中的多個明細項目。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-120">Consider a purchase order (PO) that contains a collection of records for each line item, and those records repeat numerous times to represent multiple line items in a single PO.</span></span> <span data-ttu-id="d4e0e-121">這類訊息的結構描述可能會包含名為 LineItems 做為重複組 （有時是概念性的） 容器的節點： 在執行個體訊息的一般檔案表示法，LineItems 容器是在本質上，由概念資料和分隔符號，適當的順序在執行個體訊息的 XML 表示法，LineItems 容器是明確的形式出現**LineItems** XML 中的項目。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-121">The schema for such a message would likely include a node named LineItems to serve as the (sometimes conceptual) container for the repeating set: in the flat file representation of the instance message, the LineItems container is conceptual in nature, represented by the appropriate sequence of data and delimiters; in the XML representation of the instance message, the LineItems container is explicitly present in the form of a **LineItems** element in XML.</span></span>  

  <span data-ttu-id="d4e0e-122">假設有一個訊息包含根節點並僅含有一個群組節點。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-122">Consider a message containing a root node and only one group node.</span></span> <span data-ttu-id="d4e0e-123">我們可以很容易看出，輸入資料流的最後一個分隔符號會屬於根節點。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-123">It is easy to see where the last delimiter in the input stream would belong to the root node.</span></span> <span data-ttu-id="d4e0e-124">因此，概念性迴圈中的資料/分隔符號順序，就只不過是一或多筆明細項目記錄。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-124">Therefore, the data/delimiter sequence in the conceptual loop would merely be one or more line item records.</span></span> <span data-ttu-id="d4e0e-125">只有在超過一筆明細項目記錄的情況下，才會有分隔符號來分隔它們。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-125">Only in the case where there are more than one line item records would there be a delimiter to separate them.</span></span> <span data-ttu-id="d4e0e-126">因此，分隔符號的數目會比被分隔的項目組少一，且分隔符號會位於被分隔的項目之間，此結構稱為 [中置]。</span><span class="sxs-lookup"><span data-stu-id="d4e0e-126">In that case, the number of delimiters is one less than the sets of things being delimited, and the delimiters are located between the delimited items in a structure known as Infix.</span></span>  

## <a name="see-also"></a><span data-ttu-id="d4e0e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4e0e-127">See Also</span></span>  
- [<span data-ttu-id="d4e0e-128">分隔記錄考量</span><span class="sxs-lookup"><span data-stu-id="d4e0e-128">Delimited Record Considerations</span></span>](../core/delimited-record-considerations.md)   
- <span data-ttu-id="d4e0e-129">**子系順序 （一般檔案結構描述中的節點屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="d4e0e-129">**Child Order (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
