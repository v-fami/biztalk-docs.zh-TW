---
title: "來源與目的結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- destination schemas
- source schemas, maps
- XML schemas, defining
- destination schemas, about destination schemas
- schemas, destination
- destination schemas, maps
- maps, source schemas
- schemas, Root Reference property
- Root Reference property, modifying
- source schemas
- modifying, Root Reference property
- maps, Root Reference property
- source schemas, about source schemas
- schemas, maps
- maps, schema requirements
- schemas, requirements
- schemas, source schemas
- maps, destination schemas
- Root Reference property
ms.assetid: 8c805854-9fa1-4ce3-938d-a2e61ba17fa1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d82fb8445260b505fbd04b648c251b99fe896dcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="source-and-destination-schemas"></a><span data-ttu-id="442b5-102">來源與目的結構描述</span><span class="sxs-lookup"><span data-stu-id="442b5-102">Source and Destination Schemas</span></span>
<span data-ttu-id="442b5-103">每一個 BizTalk 對應均使用兩個結構描述：一個來源結構描述和一個目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="442b5-103">Each BizTalk map uses two schemas: a source schema and a destination schema.</span></span> <span data-ttu-id="442b5-104">來源結構描述會定義您從中取得資料的執行個體訊息之結構。</span><span class="sxs-lookup"><span data-stu-id="442b5-104">A source schema defines the structure of the instance messages from which you are taking data.</span></span> <span data-ttu-id="442b5-105">目的結構描述則會定義對應產生的執行個體訊息之結構。</span><span class="sxs-lookup"><span data-stu-id="442b5-105">The destination schema defines the structure of the instance messages the map produces.</span></span> <span data-ttu-id="442b5-106">例如，若要將訂單的出貨和帳單資訊對應到發票，您需要一個結構描述以定義訂單為來源結構描述，以及另一個結構描述以定義發票為目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="442b5-106">For example, if you want to map the shipping and billing information from a purchase order to an invoice, you need a schema to define purchase orders for the source schema and a schema defining invoices for the destination schema.</span></span>  
  
 <span data-ttu-id="442b5-107">用於 BizTalk 對應的結構描述必須符合以下條件：</span><span class="sxs-lookup"><span data-stu-id="442b5-107">Schemas used in BizTalk maps must meet the following conditions:</span></span>  
  
-   <span data-ttu-id="442b5-108">來源與目的結構描述必須為目前 BizTalk 專案的一部分，或者必須將結構描述的參考包含在組件中，以便可在執行階段存取結構描述。</span><span class="sxs-lookup"><span data-stu-id="442b5-108">The source and destination schemas need to be a part of your current BizTalk project, or you must include a reference to the schemas in the assembly so that the schemas can be accessed during run time.</span></span>  
  
-   <span data-ttu-id="442b5-109">用於「BizTalk 對應工具」的結構描述必須以 XML 結構描述定義 (XSD) 語言為基礎。</span><span class="sxs-lookup"><span data-stu-id="442b5-109">The schemas used in BizTalk Mapper must be based on the XML Schema definition (XSD) language.</span></span> <span data-ttu-id="442b5-110">「BizTalk 編輯器」提供簡易的方式，以建立這類結構描述。</span><span class="sxs-lookup"><span data-stu-id="442b5-110">BizTalk Editor provides an easy way to create such schemas.</span></span> <span data-ttu-id="442b5-111">如需有關使用 「 BizTalk 編輯器建立結構描述的詳細資訊，請參閱[建立結構描述使用 BizTalk 編輯器](../core/creating-schemas-using-biztalk-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="442b5-111">For more information about creating schemas with BizTalk Editor, see [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md).</span></span> <span data-ttu-id="442b5-112">另請參閱[建立結構描述](../core/creating-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="442b5-112">Also see [Creating Schemas](../core/creating-schemas.md).</span></span>  
  
 <span data-ttu-id="442b5-113">在「BizTalk 編輯器」中，您可以建立具有多個根節點的結構描述。</span><span class="sxs-lookup"><span data-stu-id="442b5-113">In BizTalk Editor, you can create schemas with multiple root nodes.</span></span> <span data-ttu-id="442b5-114">但是，若您在 BizTalk 對應中使用具有多個根節點的結構描述，則必須選擇要在對應中使用哪一個根節點 (與對應的子結構)。</span><span class="sxs-lookup"><span data-stu-id="442b5-114">However, if you use a schema with multiple root nodes in a BizTalk map, you must choose which root node (and corresponding substructure) to use in the map.</span></span> <span data-ttu-id="442b5-115">結構描述有**根參考**識別哪一個根屬性為主要。</span><span class="sxs-lookup"><span data-stu-id="442b5-115">Schemas have a **Root Reference** property identifying which root is primary.</span></span> <span data-ttu-id="442b5-116">如果結構描述具有多個根節點和**根參考**屬性設定結構描述第一次開啟時做為來源或目的結構描述，BizTalk 對應工具會使用指定的根目錄。</span><span class="sxs-lookup"><span data-stu-id="442b5-116">If a schema has multiple roots and the **Root Reference** property is set when the schema is first opened as the source or destination schema, BizTalk Mapper uses the specified root.</span></span> <span data-ttu-id="442b5-117">如果結構描述具有多個根節點和**根參考**未設定屬性，BizTalk 對應工具會提示您選擇的根。</span><span class="sxs-lookup"><span data-stu-id="442b5-117">If a schema has multiple roots and the **Root Reference** property is not set, BizTalk Mapper prompts you to choose a root.</span></span>  
  
 <span data-ttu-id="442b5-118">如果您變更**根參考**的對應時，BizTalk 對應工具中已使用的結構描述屬性不會不會注意到變更，會繼續使用原先指定的根目錄。</span><span class="sxs-lookup"><span data-stu-id="442b5-118">If you change the **Root Reference** property of a schema already used in a map, BizTalk Mapper does not notice the change and continues to use the originally specified root.</span></span> <span data-ttu-id="442b5-119">如果您想要建置不同對應使用相同的結構描述的不同根目錄，最好是將設定為**根參考**屬性。</span><span class="sxs-lookup"><span data-stu-id="442b5-119">If you want to build different maps using different roots of the same schema, it is best not to set the **Root Reference** property.</span></span> <span data-ttu-id="442b5-120">若設定該屬性，則只要結構描述用於新的對應時，您都必須明確地選擇根目錄。</span><span class="sxs-lookup"><span data-stu-id="442b5-120">That way, whenever the schema is used for a new map, you must explicitly choose the root.</span></span>  
  
 <span data-ttu-id="442b5-121">如果它包含在對應後，您可以編輯結構描述，可能會中斷模式中的連結。</span><span class="sxs-lookup"><span data-stu-id="442b5-121">If you edit a schema after it is included in a map, the links within the map may break.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="442b5-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="442b5-122">See Also</span></span>  
 <span data-ttu-id="442b5-123">[對應](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="442b5-123">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="442b5-124">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="442b5-124">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)