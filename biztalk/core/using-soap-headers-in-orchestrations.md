---
title: 在協調流程中使用 SOAP 標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, code samples
- SOAP headers, creating
- SOAP headers, properties
- Web services, SOAP headers
- orchestrations, SOAP headers
- creating, SOAP headers
ms.assetid: 4754dd23-386b-4093-8ea4-4da6b4d9279c
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faae7013c824926adea67feab296e1993f93e326
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288534"
---
# <a name="using-soap-headers-in-orchestrations"></a><span data-ttu-id="9581b-102">在協調流程中使用 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="9581b-102">Using SOAP Headers in Orchestrations</span></span>
<span data-ttu-id="9581b-103">協調流程會使用屬性結構描述來定義 SOAP 標頭內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9581b-103">Orchestrations use property schemas to define SOAP header context properties.</span></span> <span data-ttu-id="9581b-104">您可以使用 BizTalk 編輯器設定 SOAP 標頭內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9581b-104">You use the BizTalk Editor to set SOAP header context properties.</span></span>  
  
## <a name="defining-soap-header-context-properties-with-property-schemas"></a><span data-ttu-id="9581b-105">使用屬性結構描述定義 SOAP 標頭內容屬性</span><span class="sxs-lookup"><span data-stu-id="9581b-105">Defining SOAP header context properties with property schemas</span></span>  
 <span data-ttu-id="9581b-106">您需要屬性結構描述，才能在協調流程中使用已定義的 SOAP 標頭內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9581b-106">You need a property schema to use defined SOAP header context properties in orchestrations.</span></span> <span data-ttu-id="9581b-107">屬性結構描述必須有目標命名空間**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**，而**Property Schema Base**屬性設定為**MessageContextPropertyBase**。</span><span class="sxs-lookup"><span data-stu-id="9581b-107">The property schema must have the target namespace of **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**, and the **Property Schema Base** property set to **MessageContextPropertyBase**.</span></span> <span data-ttu-id="9581b-108">屬性結構描述中的各根項目名稱，必須符合已定義 SOAP 標頭中的根項目名稱。</span><span class="sxs-lookup"><span data-stu-id="9581b-108">Each root element name in the property schema must match the root element name in the defined SOAP header.</span></span> <span data-ttu-id="9581b-109">您接著便可以使用屬性結構描述的命名空間和屬性名稱，來設定內容屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9581b-109">You can then set values for the context properties using the namespace of the property schema and the property name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9581b-110">屬性結構描述的命名空間是不同的目標結構描述命名空間 (**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**)。</span><span class="sxs-lookup"><span data-stu-id="9581b-110">The namespace of the property schema is different from the namespace of the target schema (**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**).</span></span> <span data-ttu-id="9581b-111">雖然您的命名空間可以是任何字串，但通常會預設為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="9581b-111">Your namespace can be any string; however, it usually defaults to the name of the project.</span></span>  
  
 <span data-ttu-id="9581b-112">下列程式碼顯示指定 SOAP 標頭內容屬性的屬性結構描述命名空間所在**SOAPHeader**與屬性名稱的**OrigDest**:</span><span class="sxs-lookup"><span data-stu-id="9581b-112">The following code shows assigning a SOAP header context property where the property schema namespace is **SOAPHeader** with a property name of **OrigDest**:</span></span>  
  
```  
requestMessageInstance(SOAPHeader.OrigDest) = stringVar;  
```  
  
 <span data-ttu-id="9581b-113">如需屬性結構描述和內容屬性的詳細資訊，請參閱[屬性結構描述](../core/property-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="9581b-113">For more information about property schemas and context properties, see [Property Schemas](../core/property-schemas.md).</span></span>  
  
## <a name="using-biztalk-editor-to-set-soap-header-context-properties"></a><span data-ttu-id="9581b-114">使用 BizTalk 編輯器設定 SOAP 標頭內容屬性</span><span class="sxs-lookup"><span data-stu-id="9581b-114">Using BizTalk Editor to set SOAP header context properties</span></span>  
 <span data-ttu-id="9581b-115">針對協調流程，SOAP 標頭內容屬性會設為包含 XML 資料的字串。</span><span class="sxs-lookup"><span data-stu-id="9581b-115">For orchestrations, the SOAP header context properties are set to strings that contain XML data.</span></span> <span data-ttu-id="9581b-116">設定這些字串時，使用 BizTalk 運算式編輯器**訊息指派**或**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="9581b-116">You set these strings using the BizTalk Expression Editor in a **Message Assignment** or **Expression** shape.</span></span>  
  
 <span data-ttu-id="9581b-117">下列範例說明設定內容屬性的字串：</span><span class="sxs-lookup"><span data-stu-id="9581b-117">The following example shows the string setting the context property:</span></span>  
  
```  
RequestMessageInstance(SOAPHeader.OrigDest) = "<?xml version=\"1.0\"?>  
<OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">  
<Origination>Home</Origination>  
<Destination>Work</Destination>  
</OrigDest>"  
```  
  
## <a name="using-biztalk-editor-to-create-an-instance-of-a-soap-header-root-element"></a><span data-ttu-id="9581b-118">使用 BizTalk 編輯器建立 SOAP 標頭根項目的執行個體</span><span class="sxs-lookup"><span data-stu-id="9581b-118">Using BizTalk Editor to create an instance of a SOAP header root element</span></span>  
 <span data-ttu-id="9581b-119">要將 SOAP 標頭設定為正確的字串，可能並不容易。</span><span class="sxs-lookup"><span data-stu-id="9581b-119">Setting the SOAP header to the correct string can be difficult.</span></span> <span data-ttu-id="9581b-120">將 Web 參考加入到 BizTalk 專案時，所有複雜的 Web 訊息部分都會當做根項目加入到 Reference.xsd 中。</span><span class="sxs-lookup"><span data-stu-id="9581b-120">When adding a Web reference to a BizTalk project, all complex Web message parts are added to Reference.xsd as root elements.</span></span> <span data-ttu-id="9581b-121">Reference.xsd 還包含每個已定義的 SOAP 標頭的根項目。</span><span class="sxs-lookup"><span data-stu-id="9581b-121">Reference.xsd also contains root elements for each defined SOAP header.</span></span> <span data-ttu-id="9581b-122">為確保您使用正確的字串設定 SOAP 標頭，請使用 BizTalk 編輯器為 Reference.xsd 建立 SOAP 標頭根項目的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9581b-122">To ensure that you set the SOAP header with the correct string, you should use BizTalk Editor to create an instance of the SOAP header root element for Reference.xsd.</span></span> <span data-ttu-id="9581b-123">您可以直接使用產生的執行個體資料，或使用執行個體資料來包含實際的資料。</span><span class="sxs-lookup"><span data-stu-id="9581b-123">You can use the generated instance data directly or the instance data to contain your real data.</span></span>  
  
 <span data-ttu-id="9581b-124">如需有關如何使用 BizTalk 編輯器產生執行個體資料的詳細資訊，請參閱[如何產生執行個體訊息](../core/how-to-generate-instance-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="9581b-124">For more information about using the BizTalk Editor to generate instance data, see [How to Generate Instance Messages](../core/how-to-generate-instance-messages.md).</span></span>  
  
## <a name="creating-an-xmldocument-to-set-context-properties"></a><span data-ttu-id="9581b-125">建立 XmlDocument 來設定內容屬性</span><span class="sxs-lookup"><span data-stu-id="9581b-125">Creating an XmlDocument to set context properties</span></span>  
 <span data-ttu-id="9581b-126">您可以設定內容屬性，藉由建立**XmlDocument**和寫入的字串值**XmlDocument**內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9581b-126">You can set context properties by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property.</span></span> <span data-ttu-id="9581b-127">宣告類型的變數**XMLDocument**並指派 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="9581b-127">You declare a variable of type **XMLDocument** and assign the XML data.</span></span>  
  
 <span data-ttu-id="9581b-128">下列範例示範如何設定宣告型別的變數**XMLDocument**並指派 XML 資料：</span><span class="sxs-lookup"><span data-stu-id="9581b-128">The following example shows setting a declaring a variable of type **XMLDocument** and assign the XML data:</span></span>  
  
```  
xmlDoc.LoadXml("<?xml version=\"1.0\"?><OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\"><Origination>Home</Origination><Destination>Work</Destination></OrigDest>");  
```  
  
 <span data-ttu-id="9581b-129">下列範例說明如何設定內容屬性：</span><span class="sxs-lookup"><span data-stu-id="9581b-129">The following example shows setting the context property:</span></span>  
  
```  
RequestMessageInstance(SOAPHeader.OrigDest) = xmlDoc.OuterXml;  
```  
  
 <span data-ttu-id="9581b-130">如需有關如何使用 BizTalk 運算式編輯器的詳細資訊，請參閱[運算式的需求與限制](../core/requirements-and-limitations-for-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="9581b-130">For more information about using BizTalk Expression Editor, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).</span></span> <span data-ttu-id="9581b-131">如需呼叫.NET 類別的詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。</span><span class="sxs-lookup"><span data-stu-id="9581b-131">For more information about calling .NET classes, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
## <a name="creating-soap-headers-for-a-soap-request"></a><span data-ttu-id="9581b-132">建立 SOAP 要求的 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="9581b-132">Creating SOAP headers for a SOAP request</span></span>  
 <span data-ttu-id="9581b-133">建立 SOAP 要求的 SOAP 標頭時，您必須確定建立的 SOAP 標頭是否正確無誤。</span><span class="sxs-lookup"><span data-stu-id="9581b-133">When you create SOAP headers for the SOAP request, you must ensure that you have correctly created the SOAP headers.</span></span> <span data-ttu-id="9581b-134">SOAP 配接器不會驗證 SOAP 標頭內容屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="9581b-134">The SOAP adapter does not verify the contents of the SOAP header context properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9581b-135">如果 SOAP 標頭不正確，BizTalk 將無法傳送 SOAP 要求至 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="9581b-135">If the SOAP header is incorrect, BizTalk cannot send the SOAP request to the Web service.</span></span>  
  
 <span data-ttu-id="9581b-136">BizTalk 傳回 Web 服務的 SOAP 回應可能也包含 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="9581b-136">The SOAP response that BizTalk returns to the Web service may also contain SOAP headers.</span></span> <span data-ttu-id="9581b-137">您只能存取其中已定義的 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="9581b-137">You can only access these SOAP headers if they are defined SOAP headers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9581b-138">已使用的 Web 服務只支援已定義的 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="9581b-138">Consumed Web services support only defined SOAP headers.</span></span>  
  
 <span data-ttu-id="9581b-139">如需定義的 SOAP 標頭的詳細資訊，請參閱[使用 SOAP 標頭](../core/using-soap-headers.md)。</span><span class="sxs-lookup"><span data-stu-id="9581b-139">For more information about defined SOAP headers, see [Using SOAP Headers](../core/using-soap-headers.md).</span></span> <span data-ttu-id="9581b-140">將回應 SOAP 標頭設定為內容屬性所使用的語法，與設定要求 SOAP 標頭的語法相同。</span><span class="sxs-lookup"><span data-stu-id="9581b-140">The response SOAP headers are set to context properties using the same syntax as the request SOAP headers.</span></span>  
  
 <span data-ttu-id="9581b-141">下列程式碼說明如何存取回應 SOAP 標頭：</span><span class="sxs-lookup"><span data-stu-id="9581b-141">The following code shows how to access the response SOAP headers:</span></span>  
  
```  
stringVar = ResponseMessageInstance(SOAPHeader.OrigDest);  
```  
  
 <span data-ttu-id="9581b-142">內容屬性中包含的值是包含 XML 資料的字串。</span><span class="sxs-lookup"><span data-stu-id="9581b-142">The values contained in the context properties are strings containing XML data.</span></span> <span data-ttu-id="9581b-143">設定這些字串時，使用 BizTalk 運算式編輯器**訊息指派**或**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="9581b-143">You set these strings using BizTalk Expression Editor in a **Message Assignment** or **Expression** shape.</span></span> <span data-ttu-id="9581b-144">您可以將字串載入**XmlDocument**並使用 XPath 查詢來存取特定欄位。</span><span class="sxs-lookup"><span data-stu-id="9581b-144">You load the string in an **XmlDocument** and use XPath queries to access specific fields.</span></span>  
  
 <span data-ttu-id="9581b-145">如需在 [BizTalk 運算式編輯器] 中建立 XML 文件的詳細資訊，請參閱[XLANG 的語言](../core/xlang-s-language.md)。</span><span class="sxs-lookup"><span data-stu-id="9581b-145">For more information about creating XML documents in BizTalk Expression Editor, see [XLANG-s Language](../core/xlang-s-language.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9581b-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9581b-146">See Also</span></span>  
 <span data-ttu-id="9581b-147">[XLANG 的語言](../core/xlang-s-language.md) </span><span class="sxs-lookup"><span data-stu-id="9581b-147">[XLANG-s Language](../core/xlang-s-language.md) </span></span>  
 [<span data-ttu-id="9581b-148">SOAP 標頭與已使用的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9581b-148">SOAP Headers with Consumed Web Services</span></span>](../core/soap-headers-with-consumed-web-services.md)