---
title: 從 TIBCO Rendezvous 接收的資料類型對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36908a94-3c0d-466e-aa49-f674ba4a26af
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dcb17ceac0c323bba7a6f25cff0d07473b6d7fa3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014661"
---
# <a name="data-type-mapping-for-receive-handlers-in-tibco-rendezvous"></a><span data-ttu-id="37756-102">TIBCO Rendezvous 中的接收處理常式資料型別對應</span><span class="sxs-lookup"><span data-stu-id="37756-102">Data Type Mapping for Receive Handlers in TIBCO Rendezvous</span></span>
<span data-ttu-id="37756-103">Microsoft BizTalk Adapter for TIBCO Rendezvous 會將 TIBCO RV 類型對應至如下表所指定的 XML 結構描述類型中。</span><span class="sxs-lookup"><span data-stu-id="37756-103">Microsoft BizTalk Adapter for TIBCO Rendezvous maps TIBCO RV types to XML Schema types as specified in the following table.</span></span>  
  
## <a name="tibco-rv-to-xml-data-type-mapping"></a><span data-ttu-id="37756-104">TIBCO RV 與 XML 資料類型的對應</span><span class="sxs-lookup"><span data-stu-id="37756-104">TIBCO RV to XML Data Type Mapping</span></span>  
  
|<span data-ttu-id="37756-105">TIBCO RV 型別</span><span class="sxs-lookup"><span data-stu-id="37756-105">TIBCO RV Type</span></span>|<span data-ttu-id="37756-106">XML 結構描述類型</span><span class="sxs-lookup"><span data-stu-id="37756-106">XML Schema Type</span></span>|<span data-ttu-id="37756-107">註解</span><span class="sxs-lookup"><span data-stu-id="37756-107">Comments</span></span>|  
|-------------------|---------------------|--------------|  
|<span data-ttu-id="37756-108">TIBRVMSG_MSG</span><span class="sxs-lookup"><span data-stu-id="37756-108">TIBRVMSG_MSG</span></span>|<span data-ttu-id="37756-109">tibrv:message</span><span class="sxs-lookup"><span data-stu-id="37756-109">tibrv:message</span></span>|<span data-ttu-id="37756-110">從整個訊息所建構的完整 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="37756-110">Complete XML document constructed from entire message.</span></span>|  
|<span data-ttu-id="37756-111">TIBRVMSG_XML</span><span class="sxs-lookup"><span data-stu-id="37756-111">TIBRVMSG_XML</span></span>|<span data-ttu-id="37756-112">tibrv:rawxml</span><span class="sxs-lookup"><span data-stu-id="37756-112">tibrv:rawxml</span></span>|<span data-ttu-id="37756-113">從位元組陣列建構的 XML 文件 (未經過配接器解譯)。</span><span class="sxs-lookup"><span data-stu-id="37756-113">XML Document constructed from the array of bytes (not interpreted by the adapter).</span></span>|  
|<span data-ttu-id="37756-114">TIBRVMSG_DATETIME</span><span class="sxs-lookup"><span data-stu-id="37756-114">TIBRVMSG_DATETIME</span></span>|<span data-ttu-id="37756-115">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="37756-115">xsd:dateTime</span></span>|<span data-ttu-id="37756-116">配接器會使用 System.Xml.XmlConvert 類別，以在 XML 結構描述 `dateTime` 與 `System.DateTime` 執行個體之間轉換。</span><span class="sxs-lookup"><span data-stu-id="37756-116">The adapter uses the System.Xml.XmlConvert class to convert between XML Schema `dateTime` and `System.DateTime` instances.</span></span>|  
|<span data-ttu-id="37756-117">TIBRVMSG_OPAQUE</span><span class="sxs-lookup"><span data-stu-id="37756-117">TIBRVMSG_OPAQUE</span></span>|<span data-ttu-id="37756-118">xsd:base64Binary</span><span class="sxs-lookup"><span data-stu-id="37756-118">xsd:base64Binary</span></span>||  
|<span data-ttu-id="37756-119">TIBRVMSG_STRING</span><span class="sxs-lookup"><span data-stu-id="37756-119">TIBRVMSG_STRING</span></span>|<span data-ttu-id="37756-120">xsd:string</span><span class="sxs-lookup"><span data-stu-id="37756-120">xsd:string</span></span>||  
|<span data-ttu-id="37756-121">TIBRVMSG_BOOL</span><span class="sxs-lookup"><span data-stu-id="37756-121">TIBRVMSG_BOOL</span></span>|<span data-ttu-id="37756-122">xsd:boolean</span><span class="sxs-lookup"><span data-stu-id="37756-122">xsd:boolean</span></span>||  
|<span data-ttu-id="37756-123">TIBRVMSG_I8</span><span class="sxs-lookup"><span data-stu-id="37756-123">TIBRVMSG_I8</span></span>|<span data-ttu-id="37756-124">xsd:byte</span><span class="sxs-lookup"><span data-stu-id="37756-124">xsd:byte</span></span>||  
|<span data-ttu-id="37756-125">TIBRVMSG_I16</span><span class="sxs-lookup"><span data-stu-id="37756-125">TIBRVMSG_I16</span></span>|<span data-ttu-id="37756-126">xsd:short</span><span class="sxs-lookup"><span data-stu-id="37756-126">xsd:short</span></span>||  
|<span data-ttu-id="37756-127">TIBRVMSG_I32</span><span class="sxs-lookup"><span data-stu-id="37756-127">TIBRVMSG_I32</span></span>|<span data-ttu-id="37756-128">xsd:int</span><span class="sxs-lookup"><span data-stu-id="37756-128">xsd:int</span></span>||  
|<span data-ttu-id="37756-129">TIBRVMSG_I64</span><span class="sxs-lookup"><span data-stu-id="37756-129">TIBRVMSG_I64</span></span>|<span data-ttu-id="37756-130">xsd:long</span><span class="sxs-lookup"><span data-stu-id="37756-130">xsd:long</span></span>||  
|<span data-ttu-id="37756-131">TIBRVMSG_U8</span><span class="sxs-lookup"><span data-stu-id="37756-131">TIBRVMSG_U8</span></span>|<span data-ttu-id="37756-132">xsd:unsignedByte</span><span class="sxs-lookup"><span data-stu-id="37756-132">xsd:unsignedByte</span></span>||  
|<span data-ttu-id="37756-133">TIBRVMSG_U16</span><span class="sxs-lookup"><span data-stu-id="37756-133">TIBRVMSG_U16</span></span>|<span data-ttu-id="37756-134">xsd:unsignedShort</span><span class="sxs-lookup"><span data-stu-id="37756-134">xsd:unsignedShort</span></span>||  
|<span data-ttu-id="37756-135">TIBRVMSG_U32</span><span class="sxs-lookup"><span data-stu-id="37756-135">TIBRVMSG_U32</span></span>|<span data-ttu-id="37756-136">xsd:unsignedInt</span><span class="sxs-lookup"><span data-stu-id="37756-136">xsd:unsignedInt</span></span>||  
|<span data-ttu-id="37756-137">TIBRVMSG_U64</span><span class="sxs-lookup"><span data-stu-id="37756-137">TIBRVMSG_U64</span></span>|<span data-ttu-id="37756-138">xsd:unsignedLong</span><span class="sxs-lookup"><span data-stu-id="37756-138">xsd:unsignedLong</span></span>||  
|<span data-ttu-id="37756-139">TIBRVMSG_F32</span><span class="sxs-lookup"><span data-stu-id="37756-139">TIBRVMSG_F32</span></span>|<span data-ttu-id="37756-140">xsd:float</span><span class="sxs-lookup"><span data-stu-id="37756-140">xsd:float</span></span>||  
|<span data-ttu-id="37756-141">TIBRVMSG_F64</span><span class="sxs-lookup"><span data-stu-id="37756-141">TIBRVMSG_F64</span></span>|<span data-ttu-id="37756-142">xsd:double</span><span class="sxs-lookup"><span data-stu-id="37756-142">xsd:double</span></span>||  
|<span data-ttu-id="37756-143">TIBRVMSG_IPADDR32</span><span class="sxs-lookup"><span data-stu-id="37756-143">TIBRVMSG_IPADDR32</span></span>|<span data-ttu-id="37756-144">tibrv:IPaddress</span><span class="sxs-lookup"><span data-stu-id="37756-144">tibrv:IPaddress</span></span>|<span data-ttu-id="37756-145">`System.Net.IPAddress.ToString( )` 用於產生輸出。</span><span class="sxs-lookup"><span data-stu-id="37756-145">`System.Net.IPAddress.ToString( )` is used to generate the output.</span></span> <span data-ttu-id="37756-146">內容以網路位元組順序排序。</span><span class="sxs-lookup"><span data-stu-id="37756-146">Content is in network byte order.</span></span> <span data-ttu-id="37756-147">由 ToString() 負責處理。</span><span class="sxs-lookup"><span data-stu-id="37756-147">ToString() takes care of that.</span></span>|  
|<span data-ttu-id="37756-148">TIBRVMSG_IPPORT16</span><span class="sxs-lookup"><span data-stu-id="37756-148">TIBRVMSG_IPPORT16</span></span>|<span data-ttu-id="37756-149">tibrv:IPport</span><span class="sxs-lookup"><span data-stu-id="37756-149">tibrv:IPport</span></span>|<span data-ttu-id="37756-150">內容以網路位元組順序排序</span><span class="sxs-lookup"><span data-stu-id="37756-150">Content is in network byte order</span></span>|  
|<span data-ttu-id="37756-151">TIBRVMSG_I8ARRAY</span><span class="sxs-lookup"><span data-stu-id="37756-151">TIBRVMSG_I8ARRAY</span></span>|<span data-ttu-id="37756-152">tibrv:arrayOfByte</span><span class="sxs-lookup"><span data-stu-id="37756-152">tibrv:arrayOfByte</span></span>|<span data-ttu-id="37756-153">'tibrv' 結構描述命名空間會隨配接器一起提供。</span><span class="sxs-lookup"><span data-stu-id="37756-153">'tibrv' schema namespace is provided with the adapter.</span></span>|  
|<span data-ttu-id="37756-154">TIBRVMSG_I16ARRAY</span><span class="sxs-lookup"><span data-stu-id="37756-154">TIBRVMSG_I16ARRAY</span></span>|<span data-ttu-id="37756-155">tibrv:arrayOfShort</span><span class="sxs-lookup"><span data-stu-id="37756-155">tibrv:arrayOfShort</span></span>||  
|<span data-ttu-id="37756-156">TIBRVMSG_I32ARRAY</span><span class="sxs-lookup"><span data-stu-id="37756-156">TIBRVMSG_I32ARRAY</span></span>|<span data-ttu-id="37756-157">tibrv:arrayOfInt</span><span class="sxs-lookup"><span data-stu-id="37756-157">tibrv:arrayOfInt</span></span>||  
|<span data-ttu-id="37756-158">TIBRVMSG_I64ARRAY</span><span class="sxs-lookup"><span data-stu-id="37756-158">TIBRVMSG_I64ARRAY</span></span>|<span data-ttu-id="37756-159">tibrv:arrayOfLong</span><span class="sxs-lookup"><span data-stu-id="37756-159">tibrv:arrayOfLong</span></span>||  
|<span data-ttu-id="37756-160">TIBRVMSG_U8ARRAY</span><span class="sxs-lookup"><span data-stu-id="37756-160">TIBRVMSG_U8ARRAY</span></span>|<span data-ttu-id="37756-161">tibrv:arrayOfUnsignedByte</span><span class="sxs-lookup"><span data-stu-id="37756-161">tibrv:arrayOfUnsignedByte</span></span>||  
|<span data-ttu-id="37756-162">TIBRVMSG_U16ARRAY</span><span class="sxs-lookup"><span data-stu-id="37756-162">TIBRVMSG_U16ARRAY</span></span>|<span data-ttu-id="37756-163">tibrv:arrayOfUnsignedShort</span><span class="sxs-lookup"><span data-stu-id="37756-163">tibrv:arrayOfUnsignedShort</span></span>||  
|<span data-ttu-id="37756-164">TIBRVMSG_U32ARRAY</span><span class="sxs-lookup"><span data-stu-id="37756-164">TIBRVMSG_U32ARRAY</span></span>|<span data-ttu-id="37756-165">tibrv:arrayOfUnsignedInt</span><span class="sxs-lookup"><span data-stu-id="37756-165">tibrv:arrayOfUnsignedInt</span></span>||  
|<span data-ttu-id="37756-166">TIBRVMSG_U64ARRAY</span><span class="sxs-lookup"><span data-stu-id="37756-166">TIBRVMSG_U64ARRAY</span></span>|<span data-ttu-id="37756-167">tibrv:arrayOfUnsignedLong</span><span class="sxs-lookup"><span data-stu-id="37756-167">tibrv:arrayOfUnsignedLong</span></span>||  
|<span data-ttu-id="37756-168">TIBRVMSG_F32ARRAY</span><span class="sxs-lookup"><span data-stu-id="37756-168">TIBRVMSG_F32ARRAY</span></span>|<span data-ttu-id="37756-169">tibrv:arrayOfFloat</span><span class="sxs-lookup"><span data-stu-id="37756-169">tibrv:arrayOfFloat</span></span>||  
|<span data-ttu-id="37756-170">TIBRVMSG_F64ARRAY</span><span class="sxs-lookup"><span data-stu-id="37756-170">TIBRVMSG_F64ARRAY</span></span>|<span data-ttu-id="37756-171">tibrv:arrayOfDouble</span><span class="sxs-lookup"><span data-stu-id="37756-171">tibrv:arrayOfDouble</span></span>||  
  
 <span data-ttu-id="37756-172">TIBCO Rendezvous 陣列與名稱相同的一系列欄位不同。</span><span class="sxs-lookup"><span data-stu-id="37756-172">TIBCO Rendezvous arrays differ from a sequence of fields with the same name.</span></span> <span data-ttu-id="37756-173">例如，在 TIBCO Rendezvous 訊息中，含有 70,000 個元素的陣列有效，但含有 70,000 個欄位的陣列則無效。</span><span class="sxs-lookup"><span data-stu-id="37756-173">For example, in a TIBCO Rendezvous message, it is valid to have an array with 70,000 elements, but it is not valid to have 70,000 fields.</span></span>  
  
 <span data-ttu-id="37756-174">以上表格中的陣列類型結構描述看起來與下列內容類似：</span><span class="sxs-lookup"><span data-stu-id="37756-174">The schema for the array types in the previous table looks like this:</span></span>  
  
```  
…  
<xsd:complexType name='arrayOfShort'>  
<xsd:sequence>  
<xsd:element name="item" type="xsd:short"/>  
</xsd:sequence>  
</xsd:complexType>  
  
```  
  
 <span data-ttu-id="37756-175">訊息中的陣列元素看起來與下列內容類似：</span><span class="sxs-lookup"><span data-stu-id="37756-175">An array element in a message looks like this:</span></span>  
  
```  
<someElement xsi:type='tibrv:arrayOfShort'>  
<item>100</item>  
<item>200</item>  
<item>300</item>  
<item>400</item>  
<item>500</item>  
</someElement>  
  
```  
  
 <span data-ttu-id="37756-176">IPaddress 的結構描述看起來與下列內容類似：</span><span class="sxs-lookup"><span data-stu-id="37756-176">The schema for the IPaddress looks like this:</span></span>  
  
```  
<xsd:simpleType name='IPaddress'>  
  
 <xsd:restriction base="xs:string">  
   <xsd:minLength value="7" />  
   <xsd:maxLength value="15" />  
  
 </xsd:restriction>  
       </xsd:simpleType>   
</xsd:simpleType>  
  
```  
  
 <span data-ttu-id="37756-177">IPport 的結構描述看起來與下列內容類似：</span><span class="sxs-lookup"><span data-stu-id="37756-177">The schema for the IPport looks like this:</span></span>  
  
```  
<xsd:simpleType name='IPport'>  
  
<xsd:restriction base='xsd:ushort'>  
</xsd:simpleType>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37756-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37756-178">See Also</span></span>  
 <span data-ttu-id="37756-179">[TIBCO Rendezvous 中的訊息對應](../core/message-mapping-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="37756-179">[Message Mapping in TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="37756-180">建立 TIBCO Rendezvous 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="37756-180">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)