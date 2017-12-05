---
title: "EDI 批次結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26da8036-8fe0-481e-b1e9-7f2e5b090768
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e159734c7d6028eb7f54354140c40757cb212b3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="edi-batch-schemas"></a><span data-ttu-id="97390-102">EDI 批次結構描述</span><span class="sxs-lookup"><span data-stu-id="97390-102">EDI Batch Schemas</span></span>
<span data-ttu-id="97390-103">BizTalk Server 處理保留的交換時，會使用結構描述至少三次：</span><span class="sxs-lookup"><span data-stu-id="97390-103">When BizTalk Server processes a preserved interchange, it uses at least three schemas:</span></span>  
  
-   <span data-ttu-id="97390-104">批次結構描述 (交換 XML 結構描述)，用來驗證保留的批次交換根節點 ( BaseArtifacts.dll 中部署的 X12_BatchSchema 或 Edifact_BatchSchema)</span><span class="sxs-lookup"><span data-stu-id="97390-104">The batch schemas (Interchange XML schemas) to validate the root node of the preserved batched interchange (X12_BatchSchema or Edifact_BatchSchema deployed in BaseArtifacts.dll)</span></span>  
  
-   <span data-ttu-id="97390-105">信封服務結構描述，用來驗證交換、群組，以及交易集標頭和結尾 (BaseArtifacts.dll 中部署的 X12ServiceSchema 和 EdifactServiceSchema)。</span><span class="sxs-lookup"><span data-stu-id="97390-105">The envelope service schemas to validate the interchange, gorup, and transaction set headers and trailers (X12ServiceSchema or EdifactServiceSchema deployed in BaseArtifacts.dll).</span></span> <span data-ttu-id="97390-106">如需詳細資訊，請參閱[EDI 服務和控制結構描述](../core/edi-service-and-control-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="97390-106">For more information, see [EDI Service and Control Schemas](../core/edi-service-and-control-schemas.md).</span></span>  
  
-   <span data-ttu-id="97390-107">文件結構描述，用於批次交換中的每種文件類型 (部署在您的專案中)。</span><span class="sxs-lookup"><span data-stu-id="97390-107">Document schemas for each document type in the batched interchange (deployed in your project).</span></span> <span data-ttu-id="97390-108">如需詳細資訊，請參閱[EDI 文件結構描述](../core/edi-document-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="97390-108">For more information, see [EDI Document Schemas](../core/edi-document-schemas.md).</span></span>  
  
 <span data-ttu-id="97390-109">批次結構描述是在執行階段用來驗證將保留的輸入和輸出批次交換。</span><span class="sxs-lookup"><span data-stu-id="97390-109">Batch schemas are used at runtime to validate inbound and outbound batched interchanges that are being preserved.</span></span> <span data-ttu-id="97390-110">批次結構描述也可在設計階段用來驗證和產生訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="97390-110">Batch schemas are also used at design time to validate and generate message instances.</span></span>  
  
## <a name="batch-schemas-used-at-runtime"></a><span data-ttu-id="97390-111">執行階段使用的批次結構描述</span><span class="sxs-lookup"><span data-stu-id="97390-111">Batch Schemas Used at Runtime</span></span>  
 <span data-ttu-id="97390-112">批次結構描述的兩個標準版本存在： X12_BatchSchema.xsd for X12 編碼和 EDIFACT_BatchSchema.xsd 用於 EDIFACT 編碼。</span><span class="sxs-lookup"><span data-stu-id="97390-112">Two canonical versions of the batch schemas exist: X12_BatchSchema.xsd for X12 encoding and EDIFACT_BatchSchema.xsd for EDIFACT encoding.</span></span> <span data-ttu-id="97390-113">這兩個結構描述是包含控制區段的範本，</span><span class="sxs-lookup"><span data-stu-id="97390-113">These schemas are templates that include the control segment.</span></span> <span data-ttu-id="97390-114">並且擁有下列根名稱和命名空間：</span><span class="sxs-lookup"><span data-stu-id="97390-114">These schemas have the following root names and namespaces:</span></span>  
  
|<span data-ttu-id="97390-115">結構描述</span><span class="sxs-lookup"><span data-stu-id="97390-115">Schema</span></span>|<span data-ttu-id="97390-116">根節點</span><span class="sxs-lookup"><span data-stu-id="97390-116">Root Node</span></span>|<span data-ttu-id="97390-117">命名空間</span><span class="sxs-lookup"><span data-stu-id="97390-117">Namespace</span></span>|  
|------------|---------------|---------------|  
|<span data-ttu-id="97390-118">X12_BatchSchema</span><span class="sxs-lookup"><span data-stu-id="97390-118">X12_BatchSchema</span></span>|<span data-ttu-id="97390-119">X12InterchangeXML</span><span class="sxs-lookup"><span data-stu-id="97390-119">X12InterchangeXML</span></span>|<span data-ttu-id="97390-120">http://schemas.microsoft.com/Edi/X12_BatchSchema</span><span class="sxs-lookup"><span data-stu-id="97390-120">http://schemas.microsoft.com/Edi/X12_BatchSchema</span></span>|  
|<span data-ttu-id="97390-121">Edifact_BatchSchema</span><span class="sxs-lookup"><span data-stu-id="97390-121">Edifact_BatchSchema</span></span>|<span data-ttu-id="97390-122">EdifactInterchangeXML</span><span class="sxs-lookup"><span data-stu-id="97390-122">EdifactInterchangeXML</span></span>|<span data-ttu-id="97390-123">http://schemas.microsoft.com/Edi/Edifact</span><span class="sxs-lookup"><span data-stu-id="97390-123">http://schemas.microsoft.com/Edi/Edifact</span></span>|  
  
 <span data-ttu-id="97390-124">接收管線所產生的 XML 執行個體上的文件類型會是常數 (\<編碼\>_BatchSchema.xml)，它會參考此標準結構描述。</span><span class="sxs-lookup"><span data-stu-id="97390-124">The document type on the XML instance generated by the receive pipeline will be a constant (\<Encoding\>_BatchSchema.xml) and will reference this canonical schema.</span></span> <span data-ttu-id="97390-125">您可以在協調流程的對應中使用此執行個體，不過必須先將文件類型和命名空間變更為對應至實際需要的結構描述，才能使用此執行個體。</span><span class="sxs-lookup"><span data-stu-id="97390-125">You can use this instance in a map in an orchestration; however, before doing so you have to change the document type and namespace to map to the actual schema required.</span></span>  
  
 <span data-ttu-id="97390-126">您不需要在專案的設計階段指定批次結構描述，因為它會部署在 BaseArtifacts.dll 中。</span><span class="sxs-lookup"><span data-stu-id="97390-126">You do not need to specify the batch schema at design time in the project, because it is deployed in BaseArtifacts.dll.</span></span>  
  
## <a name="batch-schemas-in-the-schema-store"></a><span data-ttu-id="97390-127">結構描述保存區中的批次結構描述</span><span class="sxs-lookup"><span data-stu-id="97390-127">Batch Schemas in the Schema Store</span></span>  
 <span data-ttu-id="97390-128">BizTalk Server 在執行階段用來處理保留批次的批次結構描述會部署至 BaseArtifacts.dll 組件中。</span><span class="sxs-lookup"><span data-stu-id="97390-128">The batch schemas that BizTalk Server uses at runtime to process preserved batches are deployed in the BaseArtifacts.dll assembly.</span></span> <span data-ttu-id="97390-129">這些結構描述會自動供執行階段處理使用。</span><span class="sxs-lookup"><span data-stu-id="97390-129">These are automatically available for run-time processing.</span></span> <span data-ttu-id="97390-130">Edifact_BatchSchema 和 X12_BatchSchema 中還會提供在 BizTalk 結構描述保存區[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI。</span><span class="sxs-lookup"><span data-stu-id="97390-130">Edifact_BatchSchema and X12_BatchSchema are also available in the BizTalk schema store at [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI.</span></span> <span data-ttu-id="97390-131">這些結構描述只能在設計階段用來驗證或產生交換。</span><span class="sxs-lookup"><span data-stu-id="97390-131">Each of these schemas is only used at design time to validate or generate the interchange.</span></span> <span data-ttu-id="97390-132">在執行階段，無論接收管線或傳送管線都不需要使用結構描述進行驗證。</span><span class="sxs-lookup"><span data-stu-id="97390-132">Neither schema is required for validation in the receive pipeline or send pipeline at runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97390-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="97390-133">See Also</span></span>  
 <span data-ttu-id="97390-134">[EDI 結構描述](../core/edi-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="97390-134">[EDI Schemas](../core/edi-schemas.md) </span></span>  
 [<span data-ttu-id="97390-135">處理內送批次</span><span class="sxs-lookup"><span data-stu-id="97390-135">Processing Incoming Batches</span></span>](../core/processing-incoming-batches.md)