---
title: 管線元件中的結構描述解析 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, schema resolution
- pipeline components, schema resolution
- schemas, pipeline components
ms.assetid: 35a79a6f-788b-4ca1-8483-36dcba5ae580
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c269ff3a7a5d973356754a222699c93179c90362
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984783"
---
# <a name="schema-resolution-in-pipeline-components"></a><span data-ttu-id="93a2a-102">管線元件中的結構描述解析</span><span class="sxs-lookup"><span data-stu-id="93a2a-102">Schema Resolution in Pipeline Components</span></span>
<span data-ttu-id="93a2a-103">管線解譯器和組合器元件使用 XSD 結構描述來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="93a2a-103">Pipeline disassembler and assembler components use XSD schemas to process messages.</span></span> <span data-ttu-id="93a2a-104">此類結構描述包含如升級屬性清單、辨別欄位、一般檔案訊息的註解以及 XML 封套的註解等資訊。</span><span class="sxs-lookup"><span data-stu-id="93a2a-104">The schemas contain information such as the list of promoted properties, distinguished fields, annotations for flat file messages, and annotations for XML envelopes.</span></span>  
  
 <span data-ttu-id="93a2a-105">標準解譯器和組合器元件使用結構描述類型名稱及訊息類型以支援擷取部署的結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-105">Standard disassembler and assembler components support retrieval of deployed schemas by using the schema type name and message type.</span></span> <span data-ttu-id="93a2a-106">部分元件使用結構描述類型名稱和訊息類型來擷取，而其他元件 (例如，一般檔案解譯器) 則僅使用結構描述類型來擷取。</span><span class="sxs-lookup"><span data-stu-id="93a2a-106">Some components retrieve by using both the schema type name and the message type, while others (for example, the Flat File Disassembler) retrieve only by the schema type.</span></span>  
  
 <span data-ttu-id="93a2a-107">接收 XML 訊息的管線元件以檢查訊息根項目和命名空間的方式來判斷訊息。</span><span class="sxs-lookup"><span data-stu-id="93a2a-107">Pipeline components that receive XML messages determine the message type by examining the message root element and namespace.</span></span> <span data-ttu-id="93a2a-108">例如，下列 XML 的訊息類型是"<http://MyDocument.org#MyDocument>」。</span><span class="sxs-lookup"><span data-stu-id="93a2a-108">For example, the message type for the following XML is "<http://MyDocument.org#MyDocument>".</span></span>  
  
```  
<ns0:MyDocument xmlns:ns0="http://MyDocument.org">  
  
</ns0:MyDocument>  
```  
  
 <span data-ttu-id="93a2a-109">如果結構描述沒有定義命名空間，訊息類型是"\<**rootNode**\>"。</span><span class="sxs-lookup"><span data-stu-id="93a2a-109">If a schema does not have a namespace defined for it, the message type is "\<**rootNode**\>".</span></span> <span data-ttu-id="93a2a-110">例如，若先前的範例 XML 沒有命名空間，則訊息類型是 "MyDocument"。</span><span class="sxs-lookup"><span data-stu-id="93a2a-110">For example, if the preceding example XML had no namespace, the message type would be "MyDocument".</span></span>  
  
 <span data-ttu-id="93a2a-111">標準管線元件使用訊息類型從資料庫擷取適當的結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-111">Standard pipeline components use the message type to retrieve the appropriate schema from the database.</span></span> <span data-ttu-id="93a2a-112">預設 XML 接收和傳送管線永遠會使用在執行階段從訊息 XML 內容動態探索到的訊息類型，判斷要載入哪個結構描述 (除非管線元件設定為允許無法辨識的訊息)。</span><span class="sxs-lookup"><span data-stu-id="93a2a-112">Default XML receive and send pipelines always determine which schema to load by using the message type dynamically discovered at runtime from the message XML content (unless the pipeline component is set to allow unrecognized messages).</span></span> <span data-ttu-id="93a2a-113">XML 解譯器透過使用此機制可移除訊息信封，不過，若 XML 組合器不知道要使用何種信封結構描述，則無法建立外寄訊息的信封。</span><span class="sxs-lookup"><span data-stu-id="93a2a-113">The XML Disassembler can remove the message envelope by using this mechanism; however, the XML Assembler cannot create an envelope for an outgoing message without knowing what envelope schema to use.</span></span>  
  
 <span data-ttu-id="93a2a-114">您要在管線設計師內的 XML 組合器的組態屬性中指定信封結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-114">You specify the envelope schema in the configuration properties for the XML Assembler from within the pipeline designer.</span></span>  
  
## <a name="how-schemas-are-resolved"></a><span data-ttu-id="93a2a-115">結構描述解析的方式</span><span class="sxs-lookup"><span data-stu-id="93a2a-115">How Schemas Are Resolved</span></span>  
 <span data-ttu-id="93a2a-116">假設您未直接在 XmlDisassembler 中指定結構描述，結構描述會以下列方式進行解析：</span><span class="sxs-lookup"><span data-stu-id="93a2a-116">Assuming you are not specifying the schema directly in the XmlDisassembler, schemas will be resolved in the following manner:</span></span>  
  
1. <span data-ttu-id="93a2a-117">首先，使用的根節點名稱和命名空間進行不合格的搜尋上部署的結構描述 (例如http://MyNamespace#MyRoot)。</span><span class="sxs-lookup"><span data-stu-id="93a2a-117">First, an unqualified search on the deployed schemas is made using the root node name and namespace (for example, http://MyNamespace#MyRoot).</span></span> <span data-ttu-id="93a2a-118">如果找到唯一的符合項目，則會解析該結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-118">If a unique match is found the schema is resolved.</span></span> <span data-ttu-id="93a2a-119">如果找到多個符合項目，這些項目只有版本號碼不同，且只有一個是作用中，則會使用該版本，並解析該結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-119">If multiple matches are found and differ only by version number and only one is active, that version is used and the schema is resolved.</span></span> <span data-ttu-id="93a2a-120">如果相同的結構描述在多個應用程式中都是作用中，則會找到多個作用中的結構描述，搜尋就會繼續執行下列步驟 2。</span><span class="sxs-lookup"><span data-stu-id="93a2a-120">If the same schema is active in multiple applications, multiple active schemas will be found and the search will continue with step 2 below.</span></span>  
  
2. <span data-ttu-id="93a2a-121">如果有無法解析步驟 1 的多個相符項目，搜尋會在管線正在執行中的組件所限定。</span><span class="sxs-lookup"><span data-stu-id="93a2a-121">If there are multiple matches that step 1 cannot resolve, the search is qualified by the assembly the pipeline is executing in.</span></span> <span data-ttu-id="93a2a-122">如果相同的組件中找到唯一的結構描述，則在管線正在執行中，則會解析結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-122">If a unique schema is found within the same assembly the pipeline is executing in, then the schema is resolved.</span></span>  
  
3. <span data-ttu-id="93a2a-123">如果仍然沒有符合的項目，就會使用發行者來解析結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-123">If there are still no matches, then the publisher is used to resolve the schema.</span></span> <span data-ttu-id="93a2a-124">搜尋可使用根節點、命名空間和公開金鑰 Token 縮小範圍。</span><span class="sxs-lookup"><span data-stu-id="93a2a-124">The search is narrowed by using the root node, namespace, and public key token.</span></span> <span data-ttu-id="93a2a-125">如果使用此搜尋找到唯一的結構描述，則會解析該結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-125">If a unique schema is found using this search, the schema is resolved.</span></span>  
  
4. <span data-ttu-id="93a2a-126">無法解析結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-126">Schema cannot be resolved.</span></span> <span data-ttu-id="93a2a-127">傳回錯誤，指出找不到唯一的結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-127">An error is returned noting that no unique schema can be found.</span></span>  
  
   <span data-ttu-id="93a2a-128">包括對結構描述解析的 SQL Server 定序和區分大小寫效果其他考量，請參閱[命名空間管理](../core/namespace-management.md)。</span><span class="sxs-lookup"><span data-stu-id="93a2a-128">For other considerations including the effect of SQL Server collation and case-sensitivity on schema resolution, see [Namespace Management](../core/namespace-management.md).</span></span>  
  
   <span data-ttu-id="93a2a-129">若要在 XML 組合器中建立信封或在一般檔案組合器中建立標頭和結尾，可執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="93a2a-129">To create an envelope in the XML Assembler or a header and trailer in the Flat File Assembler, you may do one of the following:</span></span>  
  
- <span data-ttu-id="93a2a-130">在 XML 組合器的組態屬性中建立自訂傳送管線以及指定信封的結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-130">Create a custom send pipeline and specify the schemas for the envelope in the configuration properties for the XML Assembler.</span></span> <span data-ttu-id="93a2a-131">這要在管線設計師中完成。</span><span class="sxs-lookup"><span data-stu-id="93a2a-131">This is done from within the pipeline designer.</span></span>  
  
- <span data-ttu-id="93a2a-132">在 [BizTalk Server 管理] 主控台中，為傳送埠上的傳送管線屬性指定 XMLTransmit。</span><span class="sxs-lookup"><span data-stu-id="93a2a-132">In the BizTalk Server Administration console specify XMLTransmit for the Send pipeline property on a send port.</span></span> <span data-ttu-id="93a2a-133">在 [EnvelopeDocSpecNames] 屬性中，按一下省略符號以設定管線屬性並指定信封的結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-133">Click the ellipsis to configure the pipeline properties and specify the schema for the envelope in the EnvelopeDocSpecNames property.</span></span>  
  
  <span data-ttu-id="93a2a-134">若相同結構描述的數個版本有意或無意地部署到資料庫中 (例如，並存部署或多個實例沒有唯一訊息類型)，則依訊息類型解析結構描述可能無法運作。</span><span class="sxs-lookup"><span data-stu-id="93a2a-134">Schema resolution by message type may not work if several versions of the same schema are intentionally or accidentally deployed in the database (for example, in a side-by-side deployment or if multiple scenarios do not have unique message types).</span></span> <span data-ttu-id="93a2a-135">若依訊息類型解析結構描述失敗，則會在事件日誌中加入 "schema ambiguity" (結構描述模擬兩可) 錯誤。</span><span class="sxs-lookup"><span data-stu-id="93a2a-135">If schema resolution by message type fails, a "schema ambiguity" error is added to the event log.</span></span> <span data-ttu-id="93a2a-136">若要確保依訊息類型解析結構描述成功，請執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="93a2a-136">To ensure that schema resolution by message type succeeds, do one of the following:</span></span>  
  
- <span data-ttu-id="93a2a-137">在與自訂管線相同的 BizTalk 專案中定義結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-137">Define the schemas in the same BizTalk project as your custom pipeline.</span></span>  
  
- <span data-ttu-id="93a2a-138">使用與包含管線的組件相同的金鑰簽署具有結構描述的組件。</span><span class="sxs-lookup"><span data-stu-id="93a2a-138">Sign the assembly with the schemas with the same key as the assembly containing the pipelines.</span></span>  
  
- <span data-ttu-id="93a2a-139">明確指定管線元件中的結構描述 (訊息類型名稱在整個 BizTalk 管理資料庫上應為唯一)。</span><span class="sxs-lookup"><span data-stu-id="93a2a-139">Explicitly specify schemas in pipeline components (message type names should be unique across the BizTalk Management database).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="93a2a-140">當相同組件中的結構描述共用訊息類型時，不可在同一個管線元件組件中包含結構描述，因為模擬兩可解析有其限制，相反地，而是要參考管線元件組件外的結構描述。</span><span class="sxs-lookup"><span data-stu-id="93a2a-140">When schemas in the same assembly share a message type, you must not include the schemas in the same pipeline component assembly due to the limitations of ambiguity resolution; instead, reference schemas that are external to the pipeline component assembly.</span></span> <span data-ttu-id="93a2a-141">即使在自訂管線的管線元件中已明確指定結構描述類型名稱，但是只要結構描述和管線元件在相同組件中，模擬兩可解析就不能運作。</span><span class="sxs-lookup"><span data-stu-id="93a2a-141">Ambiguity resolution does not work when schemas and pipeline components are in the same assembly, even if schema type names are explicitly specified in pipeline components in custom pipelines.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93a2a-142">使用的自訂管線元件**IPipelineContext**取得部署的結構描述應該取得依結構描述類型，只有當結構描述型別名稱未指定元件在執行階段，並取得結構描述的訊息類型如果在元件執行時，不使用結構描述型別資訊。</span><span class="sxs-lookup"><span data-stu-id="93a2a-142">Custom pipeline components that use **IPipelineContext** to obtain deployed schemas should obtain schemas by schema type only if the schema type name is not specified for the component at run time, and obtain schemas by message type only if the schema type information is not available when the component is run.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a2a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93a2a-143">See Also</span></span>  
 [<span data-ttu-id="93a2a-144">管線元件</span><span class="sxs-lookup"><span data-stu-id="93a2a-144">Pipeline Components</span></span>](../core/pipeline-components.md)