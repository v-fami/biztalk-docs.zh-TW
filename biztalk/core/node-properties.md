---
title: 節點屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 366080f0-c21a-467d-8051-fd280264c5c3
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d41f0f3b0fe0b302a763629b8777669b54f6cc86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264214"
---
# <a name="node-properties"></a><span data-ttu-id="d73a9-102">節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-102">Node Properties</span></span>

## <a name="overview"></a><span data-ttu-id="d73a9-103">概觀</span><span class="sxs-lookup"><span data-stu-id="d73a9-103">Overview</span></span>
<span data-ttu-id="d73a9-104">在 [BizTalk 編輯器] 中，您可以在 [Visual Studio 屬性] 視窗中檢查和設定節點屬性。</span><span class="sxs-lookup"><span data-stu-id="d73a9-104">In BizTalk Editor, you examine and set node properties in the Visual Studio Properties window.</span></span> <span data-ttu-id="d73a9-105">當您在結構描述樹狀結構檢視中選取不同的節點類型時，[屬性] 視窗中會顯示不同的屬性集合。</span><span class="sxs-lookup"><span data-stu-id="d73a9-105">As you select different types of nodes in the schema tree view, different sets of properties are displayed in the Properties window.</span></span> <span data-ttu-id="d73a9-106">因為是 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的標準，這些屬性可以依照類別顯示，或依字母順序而不指示其類別的方式顯示。</span><span class="sxs-lookup"><span data-stu-id="d73a9-106">As is standard in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], these properties can be displayed either in categories or alphabetically with no indication of their categories.</span></span> <span data-ttu-id="d73a9-107">使用靠近 [屬性] 視窗上方的標準按鈕，以切換此設定。</span><span class="sxs-lookup"><span data-stu-id="d73a9-107">Use the standard buttons near the top of the Properties window to toggle this setting.</span></span>  
  
 <span data-ttu-id="d73a9-108">節點屬性，特別在不是設定為預設值時，通常都會以 XML 結構描述定義 (XSD) 語言表示為屬性和與對應項目相關聯的屬性值。</span><span class="sxs-lookup"><span data-stu-id="d73a9-108">Node properties, especially when set to values other than their defaults, are generally represented in the XML Schema definition (XSD) language as attributes and attribute values associated with the corresponding element.</span></span> <span data-ttu-id="d73a9-109">例如，當設定的屬性**Min Occurs**和**Max Occurs**屬性，可供數個不同節點型別，所設定的值會用做值**minOccurs**和**maxOccurs**屬性，分別代表節點的項目與相關**Min Occurs**和**最大值發生**設定屬性。</span><span class="sxs-lookup"><span data-stu-id="d73a9-109">For example, when properties are set for the **Min Occurs** and **Max Occurs** properties, which are available for several different node types, the values that are set are used as the values of the **minOccurs** and **maxOccurs** attributes, respectively, associated with the element that represents the node for which the **Min Occurs** and **Max Occurs** properties are being set.</span></span>  

## <a name="property-types"></a><span data-ttu-id="d73a9-110">屬性類型</span><span class="sxs-lookup"><span data-stu-id="d73a9-110">Property types</span></span>
 <span data-ttu-id="d73a9-111">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]開發人員參考包含內容的各種節點類型，依照類別和依字母順序參考區段。</span><span class="sxs-lookup"><span data-stu-id="d73a9-111">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] developer reference contains a reference section for the properties of the various node types, organized by category and alphabetically.</span></span> <span data-ttu-id="d73a9-112">以下摘要說明每個節點類型相關聯的屬性：</span><span class="sxs-lookup"><span data-stu-id="d73a9-112">The following summarize the properties associated with each node type:</span></span>  
  
-   <span data-ttu-id="d73a9-113">結構描述節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-113">Schema Node Properties</span></span>
  
-   <span data-ttu-id="d73a9-114">記錄節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-114">Record Node Properties</span></span>
  
-   <span data-ttu-id="d73a9-115">欄位項目節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-115">Field Element Node Properties</span></span>
  
-   <span data-ttu-id="d73a9-116">欄位屬性節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-116">Field Attribute Node Properties</span></span>
  
-   <span data-ttu-id="d73a9-117">Sequence 群組節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-117">Sequence Group Node Properties</span></span>
  
-   <span data-ttu-id="d73a9-118">Choice 群組節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-118">Choice Group Node Properties</span></span> 
  
-   <span data-ttu-id="d73a9-119">All 群組節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-119">All Group Node Properties</span></span>
  
-   <span data-ttu-id="d73a9-120">Attribute 群組節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-120">Attribute Group Node Properties</span></span>
  
-   <span data-ttu-id="d73a9-121">Any 項目節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-121">Any Element Node Properties</span></span>
  
-   <span data-ttu-id="d73a9-122">Any 屬性節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-122">Any Attribute Node Properties</span></span>
  
-   <span data-ttu-id="d73a9-123">相等節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-123">Equivalent Node Properties</span></span>
  
-   <span data-ttu-id="d73a9-124">相等子節點屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-124">Equivalent Child Node Properties</span></span>

<span data-ttu-id="d73a9-125">這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="d73a9-125">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="d73a9-126">**節點屬性-字母順序清單**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]包含的所有個別參考主題每個節點的屬性，其中部分適用於各種類型的節點。</span><span class="sxs-lookup"><span data-stu-id="d73a9-126">**Node Properties — Alphabetical Listings** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] contains all of the individual reference topics for each node property, some of which apply to various types of nodes.</span></span> <span data-ttu-id="d73a9-127">個別參考主題的分類是根據它們屬於可適用於所有結構描述類型的基本屬性，還是屬於與結構描述編輯器延伸模組 (如一般檔案延伸模組) 相關聯的特殊屬性。</span><span class="sxs-lookup"><span data-stu-id="d73a9-127">The individual reference topics are categorized according to whether they are basic properties that apply to all types of schemas, or a specialized properties that are associated with a schema editor extension, such as the flat file extension.</span></span> <span data-ttu-id="d73a9-128">在這些類別中，這些屬性是依照字母順序列出。</span><span class="sxs-lookup"><span data-stu-id="d73a9-128">Within these categories, they are listed alphabetically.</span></span>  
  
 <span data-ttu-id="d73a9-129">「BizTalk 編輯器」使用 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗，讓您檢查和設定結構描述樹狀結構中的節點屬性。</span><span class="sxs-lookup"><span data-stu-id="d73a9-129">BizTalk Editor uses the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window to enable you to examine and set the properties of the nodes in the schema tree.</span></span> <span data-ttu-id="d73a9-130">本章節描述使用在 [屬性] 視窗中，包括的特殊考量屬性的某些特性**節點名稱**屬性，屬性之間的相依性的說明和資訊的最大長度都允許特定屬性的型別。</span><span class="sxs-lookup"><span data-stu-id="d73a9-130">This section describes some characteristics of working with properties in the Properties window, including special considerations for the **Node Name** property, an explanation of the interdependencies between properties, and information about the maximum lengths allowed for certain properties or types of properties.</span></span>  
  
 <span data-ttu-id="d73a9-131">本節的其餘部分提供有關特定和特殊節點屬性的其他資訊，以及一般適用於節點屬性的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="d73a9-131">The remainder of this section provides additional information about particular, special node properties and other information that applies generally to node properties.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d73a9-132">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="d73a9-132">Next steps</span></span>
  
-   [<span data-ttu-id="d73a9-133">節點名稱屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-133">Node Name Property</span></span>](../core/node-name-property.md)  
  
-   [<span data-ttu-id="d73a9-134">屬性相互依存性</span><span class="sxs-lookup"><span data-stu-id="d73a9-134">Property Interdependencies</span></span>](../core/property-interdependencies.md)  
  
-   [<span data-ttu-id="d73a9-135">其他一般檔案屬性</span><span class="sxs-lookup"><span data-stu-id="d73a9-135">Additional Flat File Properties</span></span>](../core/additional-flat-file-properties.md)