---
title: "HIPAA 結構描述的觸發程序欄位註解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1389284-a2ec-44e7-a2f1-8d26f83fd31d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d3bf6d53ec95ebfc57cff646ce5658fc6b1f4a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hipaa-schema-trigger-field-annotations"></a><span data-ttu-id="96a9f-102">HIPAA 結構描述的觸發程序欄位註解</span><span class="sxs-lookup"><span data-stu-id="96a9f-102">HIPAA Schema Trigger Field Annotations</span></span>
<span data-ttu-id="96a9f-103">EDI 區段通常包含修飾區段意義的辨識符號。</span><span class="sxs-lookup"><span data-stu-id="96a9f-103">EDI segments often contain qualifier values that modify the meaning of the segment.</span></span> <span data-ttu-id="96a9f-104">例如，N1 區段可能包含 “BT” 辨識元素以表示「帳單收件人」，或可能包含 “ST” 辨識元素以表示「出貨收件人」。</span><span class="sxs-lookup"><span data-stu-id="96a9f-104">For example, an N1 segment can contain a qualifying element of “BT” to signify a “bill-to name,” or it may contain a qualifying element of “ST” to indicate a “ship-to name.”</span></span> <span data-ttu-id="96a9f-105">通常這些欄位的解讀方式是交由商務邏輯決定，而且解譯器會將 N1 區段的所有執行個體解析成相同的 XML 記錄名稱。不過，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 隨附的 HIPAA 結構描述含有註解，可讓 EDI 解譯器根據存在的辨識元素來建立唯一的 XML 記錄。</span><span class="sxs-lookup"><span data-stu-id="96a9f-105">Normally it is left to business logic to determine how to interpret these fields and the disassembler resolves all instances of the N1 segment to the same XML record name; however, the HIPAA schemas shipped with [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] contain annotations that allow the EDI disassembler to create unique XML records based on the presence of a qualifying element.</span></span>  
  
 <span data-ttu-id="96a9f-106">**觸發程序欄位的實作**</span><span class="sxs-lookup"><span data-stu-id="96a9f-106">**Trigger Field Implementation**</span></span>  
  
 <span data-ttu-id="96a9f-107">觸發程序欄位會實作為一對描述區段元素的 XML 屬性和造成此記錄可建立的觸發程序值。</span><span class="sxs-lookup"><span data-stu-id="96a9f-107">Trigger fields are implemented as a pair of XML attributes that describe the segment element and the trigger value that causes this record to be created.</span></span> <span data-ttu-id="96a9f-108">下表描述這些屬性：</span><span class="sxs-lookup"><span data-stu-id="96a9f-108">The following table describes these attributes:</span></span>  
  
|<span data-ttu-id="96a9f-109">Attribute</span><span class="sxs-lookup"><span data-stu-id="96a9f-109">Attribute</span></span>|<span data-ttu-id="96a9f-110">目的</span><span class="sxs-lookup"><span data-stu-id="96a9f-110">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="96a9f-111">trigger_field</span><span class="sxs-lookup"><span data-stu-id="96a9f-111">trigger_field</span></span>|<span data-ttu-id="96a9f-112">會檢查觸發值區段欄位。</span><span class="sxs-lookup"><span data-stu-id="96a9f-112">The segment field that will be inspected for the trigger value.</span></span>|  
|<span data-ttu-id="96a9f-113">trigger_value</span><span class="sxs-lookup"><span data-stu-id="96a9f-113">trigger_value</span></span>|<span data-ttu-id="96a9f-114">觸發程序的值。</span><span class="sxs-lookup"><span data-stu-id="96a9f-114">The trigger value(s).</span></span><br /><br /> <span data-ttu-id="96a9f-115">這可能包含單一值，或以空格分隔的值清單。</span><span class="sxs-lookup"><span data-stu-id="96a9f-115">This may contain a single value, or a space delimited list of values.</span></span>|  
  
 <span data-ttu-id="96a9f-116">下表顯示觸發程序註解會顯示在 HIPAA 結構描述、 會導致觸發程序啟動，EDI 區段和產生的 XML 資料之後處理區段。</span><span class="sxs-lookup"><span data-stu-id="96a9f-116">The following table shows the trigger annotation as it would appear in the HIPAA schema, the EDI segment that will cause the trigger to activate, and the resulting XML data after processing the segment.</span></span>  
  
|<span data-ttu-id="96a9f-117">結構描述的觸發程序註解</span><span class="sxs-lookup"><span data-stu-id="96a9f-117">Schema Trigger Annotation</span></span>|<span data-ttu-id="96a9f-118">比對 N1 區段</span><span class="sxs-lookup"><span data-stu-id="96a9f-118">Matching N1 Segment</span></span>|<span data-ttu-id="96a9f-119">結果產生的 XML 資料</span><span class="sxs-lookup"><span data-stu-id="96a9f-119">Resulting XML Data</span></span>|  
|-------------------------------|-------------------------|------------------------|  
|`<xs:element name="TS835W1_1000A_Loop">  <xs:annotation>   <xs:appinfo>    <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayerIdentification_TS835W1_1000A/N101__EntityIdentifierCode"     trigger_value="PR" notes="Payer Identification" />    </xs:appinfo>  </xs:annotation>`|<span data-ttu-id="96a9f-120">N1 * PR\*Contoso\*1763\*0000000 ~</span><span class="sxs-lookup"><span data-stu-id="96a9f-120">N1*PR\*Contoso\*XV\*0000000~</span></span>|`<ns0:TS835W1_1000A_Loop>  <N1_PayerIdentification_TS835W1_1000A>   <N101__EntityIdentifierCode>PR</N101__EntityIdentifierCode>    <N102__PayerName>Contoso</N102__PayerName>    <N103__IdentificationCodeQualifier>XV</N103__IdentificationCodeQualifier>    <N104__PayerIdentifier>0000000</N104__PayerIdentifier>   </N1_PayerIdentification_TS835W1_1000A>`|  
|`<xs:element name="TS835W1_1000B_Loop">   <xs:annotation>    <xs:appinfo>     <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayeeIdentification_TS835W1_1000B/N101__EntityIdentifierCode"     trigger_value="PE" notes="Payee Identification" />    </xs:appinfo>   </xs:annotation>`|<span data-ttu-id="96a9f-121">N1 * PE\*Fabrikam\*FI\*9999999 ~</span><span class="sxs-lookup"><span data-stu-id="96a9f-121">N1*PE\*Fabrikam\*FI\*9999999~</span></span>|`<TS835W1_1000B_Loop>   <N1_PayeeIdentification_TS835W1_1000B>    <N101__EntityIdentifierCode>PE</N101__EntityIdentifierCode>    <N102__PayeeName>Fabrikam</N102__PayeeName>    <N103__IdentificationCodeQualifier>FI</N103__IdentificationCodeQualifier>    <N104__PayeeIdentificationCode>9999999</N104__PayeeIdentificationCode>   </N1_PayeeIdentification_TS835W1_1000B>`|  
  
 <span data-ttu-id="96a9f-122">**觸發程序欄位的 EDI 解譯器處理**</span><span class="sxs-lookup"><span data-stu-id="96a9f-122">**EDI Disassembler Processing of Trigger Fields**</span></span>  
  
 <span data-ttu-id="96a9f-123">收到 HIPAA 交易設定，如果 EDI 解譯器遇到含有觸發程序欄位的區段，它會使用觸發程序資訊產生的區段和觸發程序組合特有的 XML 記錄。</span><span class="sxs-lookup"><span data-stu-id="96a9f-123">When receiving a HIPAA transaction set, if the EDI disassembler encounters a segment that contains a trigger field, it uses the trigger information to generate an XML record specific to the segment and trigger combination.</span></span> <span data-ttu-id="96a9f-124">比方說，在下列 EDI 資料中，有兩個有不同的值 N101、 PR 和 PE 的 N1 區段：</span><span class="sxs-lookup"><span data-stu-id="96a9f-124">For example, in the following EDI data, there are two N1 segments that have different values for N101, PR and PE:</span></span>  
  
```  
  
N1*PR*Contoso*XV*0000000~  
N3*N301__PayerAddressLine~  
N4*N401__PayerCityName*N4*N403__PayerPost**N4*N406~  
……  
N1*PE*Fabrikam*FI*9999999~  
N3*N301__PayeeAddressLine~  
N4*N401__PayeeCityName*N4*N403__PayeePost**N4*N406~  
  
```  
  
 <span data-ttu-id="96a9f-125">當 EDI 解譯器處理，出現在結構描述的觸發程序欄位註解會在兩個不同的 XML 記錄根據 N101，< N1_PayerIdentification_TS835W1_1000A > 的值與 < N1_PayeeIdentification_TS835W1_1000B >，對應至 N1 * PR 和 N1\*PE。</span><span class="sxs-lookup"><span data-stu-id="96a9f-125">When processed by the EDI disassembler, the trigger field annotations present in the schema will result in two separate XML records based on the value of N101, <N1_PayerIdentification_TS835W1_1000A> and <N1_PayeeIdentification_TS835W1_1000B>, corresponding to N1*PR and N1\*PE.</span></span>  
  
 <span data-ttu-id="96a9f-126">傳送時，EDI 組合器將會卸除後置字元"_"字元，對於包含觸發程序的註解欄位之後。</span><span class="sxs-lookup"><span data-stu-id="96a9f-126">When sending, the EDI assembler will drop the suffix following the “_” character for fields that contain a trigger annotation.</span></span> <span data-ttu-id="96a9f-127">比方說，這兩個 < N1_PayerIdentification_TS835W1_1000A > 和 < N1_PayeeIdentification_TS835W1_1000B > 將會同時變成 N1。</span><span class="sxs-lookup"><span data-stu-id="96a9f-127">For example, both <N1_PayerIdentification_TS835W1_1000A> and <N1_PayeeIdentification_TS835W1_1000B> will both become N1.</span></span>  
  
 <span data-ttu-id="96a9f-128">**預設值區段和觸發程序欄位**</span><span class="sxs-lookup"><span data-stu-id="96a9f-128">**Default Segments and Trigger Fields**</span></span>  
  
 <span data-ttu-id="96a9f-129">下表包含有關的預設區段和觸發程序欄位用於 HIPAA 文件的一部分提供[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="96a9f-129">The following table contains information on the default segments and trigger fields used in HIPAA documents supplied as part of [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96a9f-130">與觸發程序欄位搭配使用個別的觸發程序值可能不同結構描述之間。</span><span class="sxs-lookup"><span data-stu-id="96a9f-130">The individual trigger values used with the trigger fields may vary between schemas.</span></span>  
  
|<span data-ttu-id="96a9f-131">觸發程序具有區段。</span><span class="sxs-lookup"><span data-stu-id="96a9f-131">Segment with Trigger</span></span>|<span data-ttu-id="96a9f-132">觸發程序欄位</span><span class="sxs-lookup"><span data-stu-id="96a9f-132">Trigger field</span></span>|  
|--------------------------|-------------------|  
|<span data-ttu-id="96a9f-133">AMT</span><span class="sxs-lookup"><span data-stu-id="96a9f-133">AMT</span></span>|<span data-ttu-id="96a9f-134">AMT01</span><span class="sxs-lookup"><span data-stu-id="96a9f-134">AMT01</span></span>|  
|<span data-ttu-id="96a9f-135">CRC</span><span class="sxs-lookup"><span data-stu-id="96a9f-135">CRC</span></span>|<span data-ttu-id="96a9f-136">CRC01</span><span class="sxs-lookup"><span data-stu-id="96a9f-136">CRC01</span></span>|  
|<span data-ttu-id="96a9f-137">DTM</span><span class="sxs-lookup"><span data-stu-id="96a9f-137">DTM</span></span>|<span data-ttu-id="96a9f-138">DTM01</span><span class="sxs-lookup"><span data-stu-id="96a9f-138">DTM01</span></span>|  
|<span data-ttu-id="96a9f-139">DTP</span><span class="sxs-lookup"><span data-stu-id="96a9f-139">DTP</span></span>|<span data-ttu-id="96a9f-140">DTP01</span><span class="sxs-lookup"><span data-stu-id="96a9f-140">DTP01</span></span>|  
|<span data-ttu-id="96a9f-141">ENT</span><span class="sxs-lookup"><span data-stu-id="96a9f-141">ENT</span></span>|<span data-ttu-id="96a9f-142">ENT02</span><span class="sxs-lookup"><span data-stu-id="96a9f-142">ENT02</span></span>|  
|<span data-ttu-id="96a9f-143">HI</span><span class="sxs-lookup"><span data-stu-id="96a9f-143">HI</span></span>|<span data-ttu-id="96a9f-144">HI01:01</span><span class="sxs-lookup"><span data-stu-id="96a9f-144">HI01:01</span></span>|  
|<span data-ttu-id="96a9f-145">N1</span><span class="sxs-lookup"><span data-stu-id="96a9f-145">N1</span></span>|<span data-ttu-id="96a9f-146">N101</span><span class="sxs-lookup"><span data-stu-id="96a9f-146">N101</span></span>|  
|<span data-ttu-id="96a9f-147">NM1</span><span class="sxs-lookup"><span data-stu-id="96a9f-147">NM1</span></span>|<span data-ttu-id="96a9f-148">NM01</span><span class="sxs-lookup"><span data-stu-id="96a9f-148">NM01</span></span>|  
|<span data-ttu-id="96a9f-149">NTE</span><span class="sxs-lookup"><span data-stu-id="96a9f-149">NTE</span></span>|<span data-ttu-id="96a9f-150">NTE01</span><span class="sxs-lookup"><span data-stu-id="96a9f-150">NTE01</span></span>|  
|<span data-ttu-id="96a9f-151">REF</span><span class="sxs-lookup"><span data-stu-id="96a9f-151">REF</span></span>|<span data-ttu-id="96a9f-152">REF01</span><span class="sxs-lookup"><span data-stu-id="96a9f-152">REF01</span></span>|  
|<span data-ttu-id="96a9f-153">RMR</span><span class="sxs-lookup"><span data-stu-id="96a9f-153">RMR</span></span>|<span data-ttu-id="96a9f-154">RMR01</span><span class="sxs-lookup"><span data-stu-id="96a9f-154">RMR01</span></span>|