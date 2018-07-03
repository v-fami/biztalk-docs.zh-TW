---
title: 命名空間管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4638c47c-3cdd-43af-aa00-da98e7293503
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa476034a578be24bf388c87f38f910565cd2548
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022468"
---
# <a name="namespace-management"></a><span data-ttu-id="905ad-102">命名空間管理</span><span class="sxs-lookup"><span data-stu-id="905ad-102">Namespace Management</span></span>
<span data-ttu-id="905ad-103">「BizTalk 編輯器」可支援命名空間。</span><span class="sxs-lookup"><span data-stu-id="905ad-103">BizTalk Editor provides support for namespaces.</span></span> <span data-ttu-id="905ad-104">XML 命名空間是名稱的集合，可以用來做為 XML 訊息中的項目或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="905ad-104">An XML namespace is a collection of names that can be used as element or attribute names in an XML message.</span></span> <span data-ttu-id="905ad-105">命名空間限定項目和屬性名稱，以避免相同結構描述中其他地方所定義的相同項目和屬性名稱之間發生衝突。</span><span class="sxs-lookup"><span data-stu-id="905ad-105">The namespace qualifies element and attribute names to avoid conflicts between the same element and attribute names that might be defined elsewhere within the same schema.</span></span>  
  
 <span data-ttu-id="905ad-106">命名空間由「通用資源識別項」(URI) 或「統一資源定位器」(URL) 識別。</span><span class="sxs-lookup"><span data-stu-id="905ad-106">Namespaces are identified by a Universal Resource Identifier (URI), either as a Uniform Resource Locator (URL) or a Uniform Resource Name (URN).</span></span> <span data-ttu-id="905ad-107">它們通常還會有一個簡短的前置詞別名，在項目或屬性名稱本身之前加上分隔符號 (:) 區隔。</span><span class="sxs-lookup"><span data-stu-id="905ad-107">They are also given a typically short prefix alias that is prepended with a separating colon (:) from the element or attribute name itself.</span></span> <span data-ttu-id="905ad-108">比方說，常會看到下列命名空間宣告內**結構描述**的結構描述之 XSD 表示中的項目。</span><span class="sxs-lookup"><span data-stu-id="905ad-108">For example, it is common to see the following namespace declaration within the **schema** element in the XSD representation of the schema.</span></span>  
  
```  
xmlns:xs="http://www.w3.org/2001/XMLSchema"  
  
```  
  
 <span data-ttu-id="905ad-109">前置詞為 xs，您會看到在整個 XSD 表示法中，限定為這類項目**項目**項目 (xs: element) 和**屬性**元素 (xs: attribute)。</span><span class="sxs-lookup"><span data-stu-id="905ad-109">The prefix is xs, which you see throughout the XSD representation, qualifying such elements as the **element** element (xs:element) and the **attribute** element (xs:attribute).</span></span>  
  
 <span data-ttu-id="905ad-110">當您第一次建立新的結構描述，而不論其是否訊息結構描述或屬性結構描述，請務必設定**目標命名空間**屬性**結構描述**節點正確。</span><span class="sxs-lookup"><span data-stu-id="905ad-110">When you first create a new schema, regardless of whether it is a message schema or a property schema, it is important to set the **Target Namespace** property of the **Schema** node properly.</span></span> <span data-ttu-id="905ad-111">您必須在其他結構描述以匯入/包含/重新定義機制使用此結構描述之前，以及定義任何屬性升級之前，先建立目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="905ad-111">You need to establish the target namespace before the schema is used by another schema with the import/include/redefine mechanisms, and before any property promotions are defined.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="905ad-112">如果您將會使用兩個只有大小寫不同的命名空間，BizTalk 資料庫必須安裝區分大小寫的定序。</span><span class="sxs-lookup"><span data-stu-id="905ad-112">If you will be using two namespaces that vary only by case, the BizTalk database must be installed with a case-sensitive collation.</span></span> <span data-ttu-id="905ad-113">區分大小寫定序的範例包括啟用區分大小寫的二進位和非二進位定序。</span><span class="sxs-lookup"><span data-stu-id="905ad-113">Examples of case-sensitive collations include binary and non-binary collations with case-sensitivity enabled.</span></span> <span data-ttu-id="905ad-114">如果沒有完成這個動作，結構描述解析就會失敗，因為 XML 是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="905ad-114">If this is not done, schema resolution will fail because XML is case-sensitive.</span></span>  
  
 <span data-ttu-id="905ad-115">下列兩個命名空間會自動新增為結構描述的 XML 結構描述定義 (XSD) 語言表示法中結構描述項目的命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="905ad-115">The following two namespaces are automatically added as namespace declarations to the schema element in the XML Schema definition (XSD) language representation of the schema:</span></span>  
  
- <span data-ttu-id="905ad-116">xmlns:b ="<http://schemas.microsoft.com/BizTalk/2003>」</span><span class="sxs-lookup"><span data-stu-id="905ad-116">xmlns:b="<http://schemas.microsoft.com/BizTalk/2003>"</span></span>  
  
- <span data-ttu-id="905ad-117">xmlns:xs ="<http://www.w3.org/2001/XMLSchema>」</span><span class="sxs-lookup"><span data-stu-id="905ad-117">xmlns:xs="<http://www.w3.org/2001/XMLSchema>"</span></span>  
  
  <span data-ttu-id="905ad-118">在使用您正建立的結構描述中之其他結構描述的過程中，會宣告其他命名空間。</span><span class="sxs-lookup"><span data-stu-id="905ad-118">In the course of using other schemas within the schema you are creating, other namespaces will be declared.</span></span> <span data-ttu-id="905ad-119">您可以檢查這些命名空間，以及自動包含的命名空間，在**匯入**對話方塊中，您可以使用存取**Imports**屬性**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="905ad-119">You can examine these namespaces, as well as the automatically included namespaces, in the **Imports** dialog box that you can access by using the **Imports** property of the **Schema** node.</span></span> <span data-ttu-id="905ad-120">多個您要建立使用其他結構描述內其他結構描述中宣告的資料類型的相關資訊，請參閱[，使用其他結構描述](../core/schemas-that-use-other-schemas.md)並[建立使用其他結構描述的](../core/how-to-create-schemas-that-use-other-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="905ad-120">For more information about using other data types declared in other schemas within the schema you are creating, see [Schemas That Use Other Schemas](../core/schemas-that-use-other-schemas.md) and [Creating Schemas That Use Other Schemas](../core/how-to-create-schemas-that-use-other-schemas.md).</span></span>  
  
  <span data-ttu-id="905ad-121">可在中檢查屬性結構描述相關聯的命名空間**升級屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="905ad-121">Namespaces associated with property schemas can be examined in the **Promote Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="905ad-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="905ad-122">See Also</span></span>  
 [<span data-ttu-id="905ad-123">建立結構描述時的考量</span><span class="sxs-lookup"><span data-stu-id="905ad-123">Considerations When Creating Schemas</span></span>](../core/considerations-when-creating-schemas.md)