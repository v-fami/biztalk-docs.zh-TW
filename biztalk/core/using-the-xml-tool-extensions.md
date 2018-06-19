---
title: 使用 XML 工具延伸模組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5613bf15-6c0a-4a82-b200-24d0801d7ece
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 976082fc14eb37d550956ec447eb63938706daa3
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006311"
---
# <a name="using-the-xml-tool-extensions"></a><span data-ttu-id="cd2ed-102">使用 XML 工具延伸模組</span><span class="sxs-lookup"><span data-stu-id="cd2ed-102">Using the XML Tool Extensions</span></span>
<span data-ttu-id="cd2ed-103">XML 工具延伸[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您在結構描述、 對應、 執行工作和訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-103">The XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enable you to perform tasks on schemas, maps, and message instances.</span></span> <span data-ttu-id="cd2ed-104">您可以在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 環境中的設計階段使用這些延伸模組。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-104">You use these extensions at design time in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="cd2ed-105">您可以執行的工作如下：</span><span class="sxs-lookup"><span data-stu-id="cd2ed-105">The tasks you can perform are:</span></span>  
  
-   <span data-ttu-id="cd2ed-106">**驗證結構描述**。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-106">**Validating a schema**.</span></span> <span data-ttu-id="cd2ed-107">這項作業會根據 EDI 規則來驗證 EDI 結構描述。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-107">This operation validates an EDI schema based on EDI rules.</span></span> <span data-ttu-id="cd2ed-108">如需詳細資訊，請參閱[驗證結構描述 (EDI)](../core/validating-a-schema-edi.md)。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-108">For more information, see [Validating a Schema (EDI)](../core/validating-a-schema-edi.md).</span></span>  
  
-   <span data-ttu-id="cd2ed-109">**驗證訊息執行個體**。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-109">**Validating a message instance**.</span></span> <span data-ttu-id="cd2ed-110">這項作業會驗證單一交易集 (不含交換和群組標頭) 或包含多個交易集的完整批次交換 (含交換和群組標頭)。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-110">This operation validates a single transaction set (without interchange and group headers) or a complete batched interchange with multiple transaction sets (with interchange and group headers).</span></span> <span data-ttu-id="cd2ed-111">若要驗證非批次交換，您必須將交換和群組標頭從執行個體移除。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-111">To validate an unbatched interchange, you need to remove the interchange and group headers from the instance.</span></span> <span data-ttu-id="cd2ed-112">如需詳細資訊，請參閱[驗證執行個體 (EDI)](../core/validating-an-instance-edi.md)。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-112">For more information, see [Validating an Instance (EDI)](../core/validating-an-instance-edi.md).</span></span>  
  
-   <span data-ttu-id="cd2ed-113">**產生訊息執行個體**。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-113">**Generating a message instance**.</span></span> <span data-ttu-id="cd2ed-114">這項作業會產生完整的批次交換或不含交換和群組標頭的交易集。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-114">This operation generates either a complete batched interchange or a transaction set without interchange and group headers.</span></span> <span data-ttu-id="cd2ed-115">您必須指定分隔符號、識別碼和其他用來產生執行個體的格式設定。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-115">You must specify the separators, identifiers, and other formatting used to generate the instance.</span></span> <span data-ttu-id="cd2ed-116">如需詳細資訊，請參閱[產生執行個體 (EDI)](../core/generating-an-instance-edi.md)。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-116">For more information, see [Generating an Instance (EDI)](../core/generating-an-instance-edi.md).</span></span>  
  
-   <span data-ttu-id="cd2ed-117">**測試對應**。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-117">**Testing a map**.</span></span> <span data-ttu-id="cd2ed-118">這項作業會根據來源文件和對應產生輸出文件 (包含虛構資料)。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-118">This operation generates an output document (with fictitious data) based upon a source document and a map.</span></span> <span data-ttu-id="cd2ed-119">如需詳細資訊，請參閱[測試對應](../core/testing-a-map.md)。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-119">For more information, see [Testing a Map](../core/testing-a-map.md).</span></span>  
  
-   <span data-ttu-id="cd2ed-120">**驗證對應**。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-120">**Validating a map**.</span></span> <span data-ttu-id="cd2ed-121">這項作業會產生兩個檔案：一個檔案包含對應的基礎 XSLT，一個檔案包含延伸模組物件。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-121">This operation generates a file containing the underlying XSLT of the map and a file containing extension objects.</span></span> <span data-ttu-id="cd2ed-122">如需詳細資訊，請參閱[驗證對應 (EDI)](../core/validating-a-map-edi.md)。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-122">For more information, see [Validating a Map (EDI)](../core/validating-a-map-edi.md).</span></span>  
  
 <span data-ttu-id="cd2ed-123">在 BizTalk Server 中，這些延伸模組可處理 EDI 結構描述、 對應和訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-123">In BizTalk Server, these extensions work on EDI schemas, maps, and message instances.</span></span> <span data-ttu-id="cd2ed-124">這些延伸模組可讓您更有效率地處理複雜的 EDI 結構描述、對應和交換。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-124">These extensions enable you to work more effectively with complex EDI schemas, maps, and interchanges.</span></span>  
  
 <span data-ttu-id="cd2ed-125">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式預設會啟用 XML 工具延伸模組。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-125">XML Tool extensions are enabled by default by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup program.</span></span> <span data-ttu-id="cd2ed-126">如果您按兩下方案總管的 Visual Studio 中的結構描述**Schema Editor Extensions**結構描述的屬性設定為**EDI 結構描述編輯器延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-126">If you double-click a schema in Solution Explorer of Visual Studio, the **Schema Editor Extensions** property of the schema is set to **EDI Schema Editor Extension**.</span></span> <span data-ttu-id="cd2ed-127">如此 XML 工具延伸模組才能運作。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-127">This is required for the XML Tool extensions to function.</span></span> <span data-ttu-id="cd2ed-128">您可以在保留選取 EDI 延伸模組的同時，選取其他結構描述編輯器延伸模組。</span><span class="sxs-lookup"><span data-stu-id="cd2ed-128">You can select other schema editor extension while leaving the EDI extensions selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2ed-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd2ed-129">See Also</span></span>  
 <span data-ttu-id="cd2ed-130">[產生執行個體 (EDI)](../core/generating-an-instance-edi.md) </span><span class="sxs-lookup"><span data-stu-id="cd2ed-130">[Generating an Instance (EDI)](../core/generating-an-instance-edi.md) </span></span>  
 <span data-ttu-id="cd2ed-131">[驗證執行個體 (EDI)](../core/validating-an-instance-edi.md) </span><span class="sxs-lookup"><span data-stu-id="cd2ed-131">[Validating an Instance (EDI)](../core/validating-an-instance-edi.md) </span></span>  
 <span data-ttu-id="cd2ed-132">[驗證結構描述 (EDI)](../core/validating-a-schema-edi.md) </span><span class="sxs-lookup"><span data-stu-id="cd2ed-132">[Validating a Schema (EDI)](../core/validating-a-schema-edi.md) </span></span>  
 <span data-ttu-id="cd2ed-133">[測試對應](../core/testing-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="cd2ed-133">[Testing a Map](../core/testing-a-map.md) </span></span>  
 [<span data-ttu-id="cd2ed-134">驗證對應 (EDI)</span><span class="sxs-lookup"><span data-stu-id="cd2ed-134">Validating a Map (EDI)</span></span>](../core/validating-a-map-edi.md)