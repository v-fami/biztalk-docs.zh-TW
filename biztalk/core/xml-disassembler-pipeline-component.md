---
title: XML 解譯器管線元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML Disassembler [pipeline component], about XML Disassembler
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component]
ms.assetid: ef39b695-6ae7-401d-be1e-b066048c34e9
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6bdd26a8fe5f90b1fd12937d19483e25f1a1e19f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011287"
---
# <a name="xml-disassembler-pipeline-component"></a><span data-ttu-id="d62bd-102">XML 解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="d62bd-102">XML Disassembler Pipeline Component</span></span>
<span data-ttu-id="d62bd-103">XML 解譯器管線元件將 XML 剖析與解譯結合成一個元件。</span><span class="sxs-lookup"><span data-stu-id="d62bd-103">The XML Disassembler pipeline component combines XML parsing and disassembling into one component.</span></span> <span data-ttu-id="d62bd-104">它的主要功能為：</span><span class="sxs-lookup"><span data-stu-id="d62bd-104">Its primary functions are:</span></span>  
  
- <span data-ttu-id="d62bd-105">移除信封。</span><span class="sxs-lookup"><span data-stu-id="d62bd-105">Removing envelopes.</span></span>  
  
- <span data-ttu-id="d62bd-106">解譯交換。</span><span class="sxs-lookup"><span data-stu-id="d62bd-106">Disassembling the interchange.</span></span>  
  
- <span data-ttu-id="d62bd-107">將內容屬性從交換和個別文件層級升級至訊息內容。</span><span class="sxs-lookup"><span data-stu-id="d62bd-107">Promoting the content properties from interchange and individual document levels on to the message context.</span></span>  
  
  <span data-ttu-id="d62bd-108">在接收信封之後，XML 解譯器元件中會發生下列動作：</span><span class="sxs-lookup"><span data-stu-id="d62bd-108">The following actions occur in the XML Disassembler component after receiving an envelope:</span></span>  
  
1. <span data-ttu-id="d62bd-109">解譯器藉由使用信封結構描述在設計階段靜態地與元件相關聯或在執行階段動態地從訊息類型決定信封結構描述，以剖析信封。</span><span class="sxs-lookup"><span data-stu-id="d62bd-109">The disassembler parses the envelope by using the envelope schemas statically associated with the component at design time or dynamically by determining envelope schemas from the message type at run time.</span></span> <span data-ttu-id="d62bd-110">結構描述可在剖析信封期間用以驗證信封的結構。</span><span class="sxs-lookup"><span data-stu-id="d62bd-110">The schema is used to verify the structure of the envelope during envelope parsing.</span></span> <span data-ttu-id="d62bd-111">若未定義信封結構，則會藉由使用根節點的命名空間與基底名稱查詢結構描述遞迴找尋。</span><span class="sxs-lookup"><span data-stu-id="d62bd-111">If envelope structure is not defined, it is found recursively by using the root node's namespace and base name to look up the schemas.</span></span>  
  
2. <span data-ttu-id="d62bd-112">解譯器元件會剖析信封中的每個文件。</span><span class="sxs-lookup"><span data-stu-id="d62bd-112">The disassembler component parses each document within the envelope.</span></span> <span data-ttu-id="d62bd-113">對於每一個文件，會以它自己的內容建立 BizTalk 訊息物件，所有屬性都在此從信封與它本身複製的文件升級。</span><span class="sxs-lookup"><span data-stu-id="d62bd-113">For each document, the BizTalk message object is created with its own context where all the properties promoted from the envelope and from the document itself get copied.</span></span> <span data-ttu-id="d62bd-114">藉由使用預先定義並已編碼成與信封和訊息關聯的 XSD 結構描述中的註解之 XPath，此元件可從信封與訊息執行個體中提取內容屬性。</span><span class="sxs-lookup"><span data-stu-id="d62bd-114">The component pulls the content properties from the envelope and message instances by using the predefined XPaths coded as annotations in the XSD schemas associated with the envelope and message.</span></span> <span data-ttu-id="d62bd-115">信封結構描述與個別文件結構描述均與管線設計師中的解譯器元件相關聯。</span><span class="sxs-lookup"><span data-stu-id="d62bd-115">The envelope schemas as well as the individual document schemas are associated with the disassembler component in Pipeline Designer.</span></span>  
  
   <span data-ttu-id="d62bd-116">XML 解譯器只處理訊息內文部分中的資料。</span><span class="sxs-lookup"><span data-stu-id="d62bd-116">The XML Disassembler only processes data in the body part of the message.</span></span> <span data-ttu-id="d62bd-117">因此，僅升級內文部分中的屬性。</span><span class="sxs-lookup"><span data-stu-id="d62bd-117">Thus, only properties from body part can be promoted.</span></span> <span data-ttu-id="d62bd-118">在發生屬性升級時，與可升級屬性相關聯的欄位之日期時間值將轉換成 UTC。</span><span class="sxs-lookup"><span data-stu-id="d62bd-118">Datetime values from the fields associated with the promotable properties get converted to UTC when property promotion occurs.</span></span> <span data-ttu-id="d62bd-119">非內文部分則未變更地複製到輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="d62bd-119">Non-body parts are copied to the output message unchanged.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d62bd-120">XML 解譯器管線元件目前會在所有日期時間屬性到達訊息存放區之前，強制將它們轉換成 UTC。</span><span class="sxs-lookup"><span data-stu-id="d62bd-120">The XML Disassembler pipeline component currently forces conversion of all datetime properties to UTC before they reach the message store.</span></span> <span data-ttu-id="d62bd-121">BizTalk Server 在內部使用 SQL 日期時間類型，其中沒有時區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d62bd-121">BizTalk Server uses an SQL datetime type internally, which does not have information about the time zone.</span></span> <span data-ttu-id="d62bd-122">若您在協調流程中產生日期時間屬性，然後嘗試將它用於與後續訊息相互關聯，則可能無法正確運作，因為 XML 解譯器管線元件會回應將它轉換成 UTC，而 Microsoft SQL Server 將無法將原始與回應時間欄位識別為相同。</span><span class="sxs-lookup"><span data-stu-id="d62bd-122">If you generate a datetime property in an orchestration, and then try to use it for correlation with subsequent messages, it may not work correctly, because the XML Disassembler pipeline component will convert it on response into UTC, and Microsoft SQL Server will have no way to identify the original and response time fields as identical.</span></span> <span data-ttu-id="d62bd-123">同樣地，您可能會遇到不一致的地方檢視訊息事件和服務執行個體追蹤資料時。</span><span class="sxs-lookup"><span data-stu-id="d62bd-123">Similarly, you may encounter discrepancies when viewing message event and service instance tracking data.</span></span>  
  
 <span data-ttu-id="d62bd-124">如需設定 XML 解譯器管線元件的資訊，請參閱[如何設定 XML 解譯器管線元件](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="d62bd-124">For information about configuring the XML Disassembler pipeline component, see [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d62bd-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="d62bd-125">In This Section</span></span>  
  
-   [<span data-ttu-id="d62bd-126">XML 解譯器管線元件中的 XML 資訊設定項目</span><span class="sxs-lookup"><span data-stu-id="d62bd-126">XML Information Set Elements in the XML Disassembler Pipeline Component</span></span>](../core/xml-information-set-elements-in-the-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="d62bd-127">XML 解譯器管線元件中無法辨識的訊息</span><span class="sxs-lookup"><span data-stu-id="d62bd-127">Unrecognized Messages in the XML Disassembler Pipeline Component</span></span>](../core/unrecognized-messages-in-the-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="d62bd-128">XML 解譯器管線元件中的文件驗證</span><span class="sxs-lookup"><span data-stu-id="d62bd-128">Document Validation in the XML Disassembler Pipeline Component</span></span>](../core/document-validation-in-the-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="d62bd-129">XML 解譯器管線元件中的文件結構強化</span><span class="sxs-lookup"><span data-stu-id="d62bd-129">Document Structure Enforcement in the XML Disassembler Pipeline Component</span></span>](../core/document-structure-enforcement-in-the-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="d62bd-130">XML 解譯器管線元件中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="d62bd-130">Character Encoding in XML Disassembler Pipeline Component</span></span>](../core/character-encoding-in-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="d62bd-131">逐步解說：使用 XML 信封 (基本)</span><span class="sxs-lookup"><span data-stu-id="d62bd-131">Walkthrough: Using XML Envelopes (Basic)</span></span>](../core/walkthrough-using-xml-envelopes-basic.md)