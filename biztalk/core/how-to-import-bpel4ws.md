---
title: 如何匯入 BPEL4WS |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3626fcb9-8e7d-4812-a0c9-bde6e7954ec8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0043cca1305f0acf7f07878acd7e75b1390ffea5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995967"
---
# <a name="import-bpel4ws-in-biztalk-server"></a><span data-ttu-id="6d189-102">在 BizTalk Server 中匯入 BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="6d189-102">Import BPEL4WS in BizTalk Server</span></span>
<span data-ttu-id="6d189-103">您可以從現有的 BPEL4WS 匯入，以建立協調流程。</span><span class="sxs-lookup"><span data-stu-id="6d189-103">You can import from existing BPEL4WS to create an orchestration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6d189-104">這個版本的 BizTalk Server 支援 BPEL4WS 1.1。</span><span class="sxs-lookup"><span data-stu-id="6d189-104">This release of BizTalk Server supports BPEL4WS 1.1.</span></span> <span data-ttu-id="6d189-105">您不能匯入或匯出 BPEL4WS 1.0。</span><span class="sxs-lookup"><span data-stu-id="6d189-105">You cannot import or export BPEL4WS 1.0.</span></span>  
  
 <span data-ttu-id="6d189-106">如需如何匯入 BPEL4WS 的範例，請參閱 < [BPEL 匯入 （BizTalk Server 範例）](../core/bpel-import-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="6d189-106">For an example of how to import BPEL4WS, see [BPEL Import (BizTalk Server Sample)](../core/bpel-import-biztalk-server-sample.md).</span></span>  
  
## <a name="import-bpel4ws-into-an-orchestration"></a><span data-ttu-id="6d189-107">在符合 BPEL4WS 匯入到協調流程</span><span class="sxs-lookup"><span data-stu-id="6d189-107">Import BPEL4WS into an orchestration</span></span>  
  
1. <span data-ttu-id="6d189-108">建立新專案。</span><span class="sxs-lookup"><span data-stu-id="6d189-108">Create a new project.</span></span>  
  
2. <span data-ttu-id="6d189-109">從 [BizTalk 專案] 類型，按兩下 [BizTalk Server BPEL 匯入專案]，或選取 [BizTalk Server BPEL 匯入專案] 並按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6d189-109">From the BizTalk Project types, double-click BizTalk Server BPEL Import Project, or select BizTalk Server BPEL Import Project and press OK.</span></span>  
  
3. <span data-ttu-id="6d189-110">在精靈中，選取必須匯入的 BPEL、WSDL 和 XSD 檔案，以產生新 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="6d189-110">In the wizard, select the BPEL, WSDL and XSD files that should be imported to form the new BizTalk project.</span></span> <span data-ttu-id="6d189-111">加入透過匯入與包含陳述式所參考的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="6d189-111">Include all files that are referenced via import and include statements.</span></span>  
  
4. <span data-ttu-id="6d189-112">選取叫用的 Web 服務之 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="6d189-112">Select WSDL files for invoked Web services.</span></span>  
  
    <span data-ttu-id="6d189-113">您現在可以修改或部署新協調流程。</span><span class="sxs-lookup"><span data-stu-id="6d189-113">You can now modify or deploy the new orchestration.</span></span>  
  
   <span data-ttu-id="6d189-114">**匯入 BPEL4WS 的限制**</span><span class="sxs-lookup"><span data-stu-id="6d189-114">**Import restrictions on BPEL4WS**</span></span>  
  
-   <span data-ttu-id="6d189-115">匯入 BPEL 和 WSDL 時，請確定 WSDL 定義節點的 [名稱] 屬性和 BPEL 程序節點不相符。</span><span class="sxs-lookup"><span data-stu-id="6d189-115">When importing BPEL and WSDL, make sure that the Name property of the WSDL definition node and the BPEL process node do not match.</span></span>  
  
-   <span data-ttu-id="6d189-116">不要在您匯入的 BPEL4WS 中使用 XLANG/s 保留字。</span><span class="sxs-lookup"><span data-stu-id="6d189-116">Do not use XLANG/s reserved words in BPEL4WS that you import.</span></span> <span data-ttu-id="6d189-117">如需完整清單，請參閱 < [XLANG/s 保留字](../core/xlang-s-reserved-words.md)。</span><span class="sxs-lookup"><span data-stu-id="6d189-117">For a complete list, see [XLANG/s Reserved Words](../core/xlang-s-reserved-words.md).</span></span>  
  
-   <span data-ttu-id="6d189-118">僅支援 XSD 預先定義的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="6d189-118">Only XSD predefined simple types are supported.</span></span>  
  
-   <span data-ttu-id="6d189-119">不支援 xsd: qname;它是以 System.String 匯入。</span><span class="sxs-lookup"><span data-stu-id="6d189-119">xsd:QName is not supported; it is imported as System.String.</span></span> <span data-ttu-id="6d189-120">請改用 xsd: string。</span><span class="sxs-lookup"><span data-stu-id="6d189-120">Use xsd:string instead.</span></span>  
  
-   <span data-ttu-id="6d189-121">匯入 BPEL4WS 時請考慮使用標準的 XPath。</span><span class="sxs-lookup"><span data-stu-id="6d189-121">Consider using canonical XPaths when importing BPEL4WS.</span></span>  
  
     <span data-ttu-id="6d189-122">最好只匯入標準的 XPath，以達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="6d189-122">It is good practice to import only canonical XPaths in order to achieve optimal performance.</span></span> <span data-ttu-id="6d189-123">整個路徑從根節點到升級節點都必須使用 '/\*[local-name()="someName" and namespace-uri()="someUri"]' 拼寫。</span><span class="sxs-lookup"><span data-stu-id="6d189-123">The entire path from root to the promoted node must be spelled out by using '/\*[local-name()="someName" and namespace-uri()="someUri"]'.</span></span>  
  
     <span data-ttu-id="6d189-124">如果您匯入的非標準 XPath，您可以移除升級並 repromote 相同的欄位才會有結構描述編輯器建立正確的標準 XPath。</span><span class="sxs-lookup"><span data-stu-id="6d189-124">If you import a non-canonical XPath, you can remove a promotion and repromote the same field in order to have the Schema Editor create the correct canonical XPath.</span></span>  
  
     <span data-ttu-id="6d189-125">範例: (targetNamespace = http://BizTalk_Server_Project3.Schema1)</span><span class="sxs-lookup"><span data-stu-id="6d189-125">Example: (targetNamespace = http://BizTalk_Server_Project3.Schema1)</span></span>  
  
    ```  
    <element name=Root type=complexType>  
                <sequence>  
                            <element name=promotedField/>  
                </sequence>  
    </element>  
    ```  
  
     `XPath - /*[local-name()='Root' and namespace-uri()='http://BizTalk_Server_Project3.Schema1']/\*[local-name()='promotedField' and namespace-uri()='']` 
  
    |<span data-ttu-id="6d189-126">標準 XPath</span><span class="sxs-lookup"><span data-stu-id="6d189-126">Canonical XPath</span></span>|<span data-ttu-id="6d189-127">非標準 XPath</span><span class="sxs-lookup"><span data-stu-id="6d189-127">Non-Canonical XPath</span></span>|  
    |---------------------|--------------------------|  
    |<span data-ttu-id="6d189-128">BizTalk 編輯器會顯示特殊圖示 (![](../core/media/ebiz-orch-promotedprop.gif "ebiz_orch_promotedprop")) 來表示已升級的欄位。</span><span class="sxs-lookup"><span data-stu-id="6d189-128">BizTalk Editor displays a special icon (![](../core/media/ebiz-orch-promotedprop.gif "ebiz_orch_promotedprop")) to denote that the field has been promoted.</span></span> <span data-ttu-id="6d189-129">使用標準 XPath 運算式升級欄位，以透過更有效的 XML 使用來改善效能</span><span class="sxs-lookup"><span data-stu-id="6d189-129">Usage of canonical XPath expressions to promote fields improves performance through more efficient traversal of the XML</span></span>|<span data-ttu-id="6d189-130">「BizTalk 編輯器」未顯示特殊圖示。</span><span class="sxs-lookup"><span data-stu-id="6d189-130">BizTalk Editor does not display a special icon.</span></span> <span data-ttu-id="6d189-131">編譯器和升級對話方塊皆提出警告。</span><span class="sxs-lookup"><span data-stu-id="6d189-131">Both the compiler and the promotion dialog give warnings.</span></span> <span data-ttu-id="6d189-132">隨著訊息大小增加，對效能會產生線性且重要的影響。</span><span class="sxs-lookup"><span data-stu-id="6d189-132">There is a linear but nontrivial effect on performance as the message size increases.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d189-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d189-133">See Also</span></span>  
 <span data-ttu-id="6d189-134">[如何匯出 BPEL4WS](../core/how-to-export-bpel4ws.md) </span><span class="sxs-lookup"><span data-stu-id="6d189-134">[How to Export BPEL4WS](../core/how-to-export-bpel4ws.md) </span></span>  
 [<span data-ttu-id="6d189-135">XLANG-s 至 BPEL4WS 類型轉換</span><span class="sxs-lookup"><span data-stu-id="6d189-135">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)
