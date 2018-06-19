---
title: TIBCO Rendezvous 中的資料類型的傳送處理常式對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa1a9233-8781-45a8-9c55-a18ecaa0f456
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bda336d149d373477b26efeb2e4b05de4aac7554
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015237"
---
# <a name="data-type-mapping-for-send-handlers-in-tibco-rendezvous"></a><span data-ttu-id="2f06d-102">TIBCO Rendezvous 中的傳送處理常式資料型別對應</span><span class="sxs-lookup"><span data-stu-id="2f06d-102">Data Type Mapping for Send Handlers in TIBCO Rendezvous</span></span>
<span data-ttu-id="2f06d-103">只有當 TIBCO Rendezvous 提供了型別資訊 (xsi:type=) 時，才能從 XML 結構描述型別對應至 TIBCO Rendezvous 型別。</span><span class="sxs-lookup"><span data-stu-id="2f06d-103">The mapping from XML schema types to TIBCO Rendezvous types is only possible if TIBCO Rendezvous provides type information (xsi:type=).</span></span> <span data-ttu-id="2f06d-104">任何 不支援的型別都會對應至字串 (如果可以的話)。</span><span class="sxs-lookup"><span data-stu-id="2f06d-104">Any unsupported types are mapped to strings if it is possible.</span></span> <span data-ttu-id="2f06d-105">若無法進行對應，或傳送埠組態中已停用對應選項，即會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2f06d-105">If mapping is not possible, or if the option is disabled in the port configuration, an error is generated.</span></span>  
  
## <a name="xml-schema-to-tibco-rendezvous-data-type-mapping"></a><span data-ttu-id="2f06d-106">XML 結構描述至 TIBCO Rendezvous 資料型別的對應</span><span class="sxs-lookup"><span data-stu-id="2f06d-106">XML Schema to TIBCO Rendezvous Data Type Mapping</span></span>  
 <span data-ttu-id="2f06d-107">下表顯示從 XML 結構描述型別至 TIBCO Rendezvous 型別的可能對應。</span><span class="sxs-lookup"><span data-stu-id="2f06d-107">The following table shows the possible mapping from XML schema types to TIBCO Rendezvous types.</span></span>  
  
|<span data-ttu-id="2f06d-108">XML 型別</span><span class="sxs-lookup"><span data-stu-id="2f06d-108">XML Type</span></span>|<span data-ttu-id="2f06d-109">TIBCO RV 型別</span><span class="sxs-lookup"><span data-stu-id="2f06d-109">TIBCO RV Type</span></span>|  
|--------------|-------------------|  
||<span data-ttu-id="2f06d-110">TIBRVMSG_MSG</span><span class="sxs-lookup"><span data-stu-id="2f06d-110">TIBRVMSG_MSG</span></span>|  
||<span data-ttu-id="2f06d-111">TIBRVMSG_XML</span><span class="sxs-lookup"><span data-stu-id="2f06d-111">TIBRVMSG_XML</span></span>|  
|<span data-ttu-id="2f06d-112">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="2f06d-112">xsd:dateTime</span></span>|<span data-ttu-id="2f06d-113">TIBRVMSG_DATETIME</span><span class="sxs-lookup"><span data-stu-id="2f06d-113">TIBRVMSG_DATETIME</span></span>|  
|<span data-ttu-id="2f06d-114">xsd:boolean</span><span class="sxs-lookup"><span data-stu-id="2f06d-114">xsd:boolean</span></span>|<span data-ttu-id="2f06d-115">TIBRVMSG_BOOL</span><span class="sxs-lookup"><span data-stu-id="2f06d-115">TIBRVMSG_BOOL</span></span>|  
|<span data-ttu-id="2f06d-116">xsd:byte</span><span class="sxs-lookup"><span data-stu-id="2f06d-116">xsd:byte</span></span>|<span data-ttu-id="2f06d-117">TIBRVMSG_I8</span><span class="sxs-lookup"><span data-stu-id="2f06d-117">TIBRVMSG_I8</span></span>|  
|<span data-ttu-id="2f06d-118">xsd:short</span><span class="sxs-lookup"><span data-stu-id="2f06d-118">xsd:short</span></span>|<span data-ttu-id="2f06d-119">TIBRVMSG_I16</span><span class="sxs-lookup"><span data-stu-id="2f06d-119">TIBRVMSG_I16</span></span>|  
|<span data-ttu-id="2f06d-120">xsd:int</span><span class="sxs-lookup"><span data-stu-id="2f06d-120">xsd:int</span></span>|<span data-ttu-id="2f06d-121">TIBRVMSG_I32</span><span class="sxs-lookup"><span data-stu-id="2f06d-121">TIBRVMSG_I32</span></span>|  
|<span data-ttu-id="2f06d-122">xsd:long</span><span class="sxs-lookup"><span data-stu-id="2f06d-122">xsd:long</span></span>|<span data-ttu-id="2f06d-123">TIBRVMSG_I64</span><span class="sxs-lookup"><span data-stu-id="2f06d-123">TIBRVMSG_I64</span></span>|  
|<span data-ttu-id="2f06d-124">xsd:unsignedByte</span><span class="sxs-lookup"><span data-stu-id="2f06d-124">xsd:unsignedByte</span></span>|<span data-ttu-id="2f06d-125">TIBRVMSG_U8</span><span class="sxs-lookup"><span data-stu-id="2f06d-125">TIBRVMSG_U8</span></span>|  
|<span data-ttu-id="2f06d-126">xsd:unsignedShort</span><span class="sxs-lookup"><span data-stu-id="2f06d-126">xsd:unsignedShort</span></span>|<span data-ttu-id="2f06d-127">TIBRVMSG_U16</span><span class="sxs-lookup"><span data-stu-id="2f06d-127">TIBRVMSG_U16</span></span>|  
|<span data-ttu-id="2f06d-128">xsd:unsignedInt</span><span class="sxs-lookup"><span data-stu-id="2f06d-128">xsd:unsignedInt</span></span>|<span data-ttu-id="2f06d-129">TIBRVMSG_U32</span><span class="sxs-lookup"><span data-stu-id="2f06d-129">TIBRVMSG_U32</span></span>|  
|<span data-ttu-id="2f06d-130">xsd:unsignedLong</span><span class="sxs-lookup"><span data-stu-id="2f06d-130">xsd:unsignedLong</span></span>|<span data-ttu-id="2f06d-131">TIBRVMSG_U64</span><span class="sxs-lookup"><span data-stu-id="2f06d-131">TIBRVMSG_U64</span></span>|  
|<span data-ttu-id="2f06d-132">xsd:float</span><span class="sxs-lookup"><span data-stu-id="2f06d-132">xsd:float</span></span>|<span data-ttu-id="2f06d-133">TIBRVMSG_F32</span><span class="sxs-lookup"><span data-stu-id="2f06d-133">TIBRVMSG_F32</span></span>|  
|<span data-ttu-id="2f06d-134">xsd:double</span><span class="sxs-lookup"><span data-stu-id="2f06d-134">xsd:double</span></span>|<span data-ttu-id="2f06d-135">TIBRVMSG_F64</span><span class="sxs-lookup"><span data-stu-id="2f06d-135">TIBRVMSG_F64</span></span>|  
|<span data-ttu-id="2f06d-136">tibrv:IPaddress</span><span class="sxs-lookup"><span data-stu-id="2f06d-136">tibrv:IPaddress</span></span>|<span data-ttu-id="2f06d-137">TIBRVMSG_IPADDR32</span><span class="sxs-lookup"><span data-stu-id="2f06d-137">TIBRVMSG_IPADDR32</span></span>|  
|<span data-ttu-id="2f06d-138">tibrv:IPport</span><span class="sxs-lookup"><span data-stu-id="2f06d-138">tibrv:IPport</span></span>|<span data-ttu-id="2f06d-139">TIBRVMSG_IPPORT16</span><span class="sxs-lookup"><span data-stu-id="2f06d-139">TIBRVMSG_IPPORT16</span></span>|  
|<span data-ttu-id="2f06d-140">tibrv:arrayOfByte</span><span class="sxs-lookup"><span data-stu-id="2f06d-140">tibrv:arrayOfByte</span></span>|<span data-ttu-id="2f06d-141">TIBRVMSG_I8ARRAY</span><span class="sxs-lookup"><span data-stu-id="2f06d-141">TIBRVMSG_I8ARRAY</span></span>|  
|<span data-ttu-id="2f06d-142">tibrv:arrayOfShort</span><span class="sxs-lookup"><span data-stu-id="2f06d-142">tibrv:arrayOfShort</span></span>|<span data-ttu-id="2f06d-143">TIBRVMSG_I16ARRAY</span><span class="sxs-lookup"><span data-stu-id="2f06d-143">TIBRVMSG_I16ARRAY</span></span>|  
|<span data-ttu-id="2f06d-144">tibrv:arrayOfInt</span><span class="sxs-lookup"><span data-stu-id="2f06d-144">tibrv:arrayOfInt</span></span>|<span data-ttu-id="2f06d-145">TIBRVMSG_I32ARRAY</span><span class="sxs-lookup"><span data-stu-id="2f06d-145">TIBRVMSG_I32ARRAY</span></span>|  
|<span data-ttu-id="2f06d-146">tibrv:arrayOfLong</span><span class="sxs-lookup"><span data-stu-id="2f06d-146">tibrv:arrayOfLong</span></span>|<span data-ttu-id="2f06d-147">TIBRVMSG_I64ARRAY</span><span class="sxs-lookup"><span data-stu-id="2f06d-147">TIBRVMSG_I64ARRAY</span></span>|  
|<span data-ttu-id="2f06d-148">tibrv:arrayOfUnsignedByte</span><span class="sxs-lookup"><span data-stu-id="2f06d-148">tibrv:arrayOfUnsignedByte</span></span>|<span data-ttu-id="2f06d-149">TIBRVMSG_U8ARRAY</span><span class="sxs-lookup"><span data-stu-id="2f06d-149">TIBRVMSG_U8ARRAY</span></span>|  
|<span data-ttu-id="2f06d-150">tibrv:arrayOfUnsignedShort</span><span class="sxs-lookup"><span data-stu-id="2f06d-150">tibrv:arrayOfUnsignedShort</span></span>|<span data-ttu-id="2f06d-151">TIBRVMSG_U16ARRAY</span><span class="sxs-lookup"><span data-stu-id="2f06d-151">TIBRVMSG_U16ARRAY</span></span>|  
|<span data-ttu-id="2f06d-152">tibrv:arrayOfUnsignedInt</span><span class="sxs-lookup"><span data-stu-id="2f06d-152">tibrv:arrayOfUnsignedInt</span></span>|<span data-ttu-id="2f06d-153">TIBRVMSG_U32ARRAY</span><span class="sxs-lookup"><span data-stu-id="2f06d-153">TIBRVMSG_U32ARRAY</span></span>|  
|<span data-ttu-id="2f06d-154">tibrv:arrayOfUnsignedLong</span><span class="sxs-lookup"><span data-stu-id="2f06d-154">tibrv:arrayOfUnsignedLong</span></span>|<span data-ttu-id="2f06d-155">TIBRVMSG_U64ARRAY</span><span class="sxs-lookup"><span data-stu-id="2f06d-155">TIBRVMSG_U64ARRAY</span></span>|  
|<span data-ttu-id="2f06d-156">tibrv:arrayOfFloat</span><span class="sxs-lookup"><span data-stu-id="2f06d-156">tibrv:arrayOfFloat</span></span>|<span data-ttu-id="2f06d-157">TIBRVMSG_F32ARRAY</span><span class="sxs-lookup"><span data-stu-id="2f06d-157">TIBRVMSG_F32ARRAY</span></span>|  
|<span data-ttu-id="2f06d-158">tibrv:arrayOfDouble</span><span class="sxs-lookup"><span data-stu-id="2f06d-158">tibrv:arrayOfDouble</span></span>|<span data-ttu-id="2f06d-159">TIBRVMSG_F64ARRAY</span><span class="sxs-lookup"><span data-stu-id="2f06d-159">TIBRVMSG_F64ARRAY</span></span>|  
|<span data-ttu-id="2f06d-160">任何其他型別 - 會有偵錯訊息</span><span class="sxs-lookup"><span data-stu-id="2f06d-160">Anything else - with a debug message</span></span>|<span data-ttu-id="2f06d-161">TIBRVMSG_STRING 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2f06d-161">TIBRVMSG_STRING the log.</span></span>|  
  
 <span data-ttu-id="2f06d-162">因為 BizTalk Adapter for TIBCO Rendezvous 無權存取結構描述，所以當您從 BizTalk Server 傳輸至 TIBCO Rendezvous 時，必須為任何非字串欄位提供 XML `xsi:type` 屬性。</span><span class="sxs-lookup"><span data-stu-id="2f06d-162">Because BizTalk Adapter for TIBCO Rendezvous does not have access to a schema, when you transmit from BizTalk Server to TIBCO Rendezvous, you must provide the XML `xsi:type` attribute for any non-string field.</span></span> <span data-ttu-id="2f06d-163">此配接器會使用該資訊在 TIBCO Rendezvous 訊息中產生適當的訊息欄位型別。</span><span class="sxs-lookup"><span data-stu-id="2f06d-163">The adapter uses that information to generate the appropriate message field type in the TIBCO Rendezvous message.</span></span>  
  
## <a name="message-mapping-example"></a><span data-ttu-id="2f06d-164">訊息對應 範例</span><span class="sxs-lookup"><span data-stu-id="2f06d-164">Message Mapping Example</span></span>  
 <span data-ttu-id="2f06d-165">下列範例會示範將訊息從 BizTalk Server 對應到 TIBCO Rendezvous。</span><span class="sxs-lookup"><span data-stu-id="2f06d-165">The following example demonstrates mapping a message from BizTalk Server to TIBCO Rendezvous.</span></span> <span data-ttu-id="2f06d-166">如需瞭解型別對應的方式，請參閱資料型別對應表中的資訊。</span><span class="sxs-lookup"><span data-stu-id="2f06d-166">Refer to the data type mapping table for information about how types are mapped.</span></span>  
  
```  
<ns:QuoteUpdate xmlns:xsi http://www.w3.org/2001/XMLSchema-instance"  
xmlns:xsd http://www.w3.org/2001/XMLSchema"  
xmlns:tibrv="http://schemas.microsoft.com/TibcoRendezvous/Types"  
xmlns:ns="some namespace for this message [value not important, unless the schema is also used for receive ports]">  
  
<ns:SymbolName id=1 xsi:type="xsd:string">MSFT</ns:SymbolName>  
  
<ns:LastTrade id=2 xsi:type="xsd:double">28.40</ns:LastTrade>   
<ns:DayLow id=3 xsi:type="xsd:double">28.25</ns:DayLow>  
  
```  
  
|||  
|-|-|  
|`<ns:DayHigh`|`id=4 xsi:type="xsd:double">28.40</ns:DayHigh>`|  
|`<ns:MarketCap`|`id=10>262575234981</ns:MarketCap>`|  
|`<ns:Bids`|`id=100 xsi:type="tibrv:message">`|  
  
```  
<ns:TopBids id=1 xsi:type="tibrv:arrayOfDouble">  
<item>28.40</item>  
<item>28.39</item>  
<item>28.39</item>  
<item>28.39</item>  
<item>28.38</item>  
  
</ns:TopBids>  
  
<ns:BidsSize id=2 xsi:type="tibrv:arrayOfLong">  
<item>500</item>  
<item>1000</item>  
<item>100</item>  
<item>100</item>  
<item>2000</item>  
  
</ns:BidsSize>  
</ns:Bids>  
</ns:QuoteUpdate>  
  
```  
  
 <span data-ttu-id="2f06d-167">先前的訊息在產生為結構化的 TIBCO Rendezvous 訊息之後，即會成為含有六個欄位的最上層 TibcoMsg 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2f06d-167">After the previous message is generated as a structured TIBCO Rendezvous message, it would be a top-level TibcoMsg instance with six fields.</span></span> <span data-ttu-id="2f06d-168">最後一個欄位是子訊息，由兩個陣列型別的欄位所組成 ('item' 項目不會對應至 TIBCO Rendezvous 訊息欄位，而是對應至 `array` 型別之訊息欄位中的項目)。</span><span class="sxs-lookup"><span data-stu-id="2f06d-168">The last fields are a sub-message, composed of two fields of array types (the 'item' elements are not mapped to TIBCO Rendezvous Message fields, but to elements in one Message Field of type `array`).</span></span> <span data-ttu-id="2f06d-169">MarketCap 欄位沒有型別規格，會當成字串訊息欄位來傳送。</span><span class="sxs-lookup"><span data-stu-id="2f06d-169">The MarketCap field, having no type specification, would be sent as a string message field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f06d-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f06d-170">See Also</span></span>  
 [<span data-ttu-id="2f06d-171">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="2f06d-171">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)