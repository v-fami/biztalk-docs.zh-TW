---
title: HIPAA 結構描述的觸發程序欄位註解 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1389284-a2ec-44e7-a2f1-8d26f83fd31d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8c50db43b14899439877fde8ce0ee476feb5095
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "26005303"
---
# <a name="hipaa-schema-trigger-field-annotations"></a><span data-ttu-id="dd2c5-102">HIPAA 結構描述的觸發程序欄位註解</span><span class="sxs-lookup"><span data-stu-id="dd2c5-102">HIPAA Schema Trigger Field Annotations</span></span>
<span data-ttu-id="dd2c5-103">EDI 區段通常包含修飾區段意義的辨識符號。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-103">EDI segments often contain qualifier values that modify the meaning of the segment.</span></span> <span data-ttu-id="dd2c5-104">例如，N1 區段可能包含 “BT” 辨識元素以表示「帳單收件人」，或可能包含 “ST” 辨識元素以表示「出貨收件人」。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-104">For example, an N1 segment can contain a qualifying element of “BT” to signify a “bill-to name,” or it may contain a qualifying element of “ST” to indicate a “ship-to name.”</span></span> <span data-ttu-id="dd2c5-105">商務邏輯決定如何解譯這些欄位通常會維持和解譯器會將 N1 區段的所有執行個體解析成相同的 XML 記錄名稱。不過，BizTalk Server 所隨附的 HIPAA 結構描述包含註解可讓 EDI 解譯器來建立根據存在的辨識元素的唯一 XML 記錄。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-105">Normally it is left to business logic to determine how to interpret these fields and the disassembler resolves all instances of the N1 segment to the same XML record name; however, the HIPAA schemas shipped with BizTalk Server contain annotations that allow the EDI disassembler to create unique XML records based on the presence of a qualifying element.</span></span>  
  
 <span data-ttu-id="dd2c5-106">**觸發程序欄位實作**</span><span class="sxs-lookup"><span data-stu-id="dd2c5-106">**Trigger Field Implementation**</span></span>  
  
 <span data-ttu-id="dd2c5-107">觸發程序欄位會實作為一組描述區段元素的 XML 屬性以及造成此記錄建立的觸發程序值。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-107">Trigger fields are implemented as a pair of XML attributes that describe the segment element and the trigger value that causes this record to be created.</span></span> <span data-ttu-id="dd2c5-108">下表描述這些屬性︰</span><span class="sxs-lookup"><span data-stu-id="dd2c5-108">The following table describes these attributes:</span></span>  
  
|<span data-ttu-id="dd2c5-109">Attribute</span><span class="sxs-lookup"><span data-stu-id="dd2c5-109">Attribute</span></span>|<span data-ttu-id="dd2c5-110">目的</span><span class="sxs-lookup"><span data-stu-id="dd2c5-110">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="dd2c5-111">trigger_field</span><span class="sxs-lookup"><span data-stu-id="dd2c5-111">trigger_field</span></span>|<span data-ttu-id="dd2c5-112">觸發值檢查區段欄位。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-112">The segment field that will be inspected for the trigger value.</span></span>|  
|<span data-ttu-id="dd2c5-113">trigger_value</span><span class="sxs-lookup"><span data-stu-id="dd2c5-113">trigger_value</span></span>|<span data-ttu-id="dd2c5-114">觸發程序的值。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-114">The trigger value(s).</span></span><br /><br /> <span data-ttu-id="dd2c5-115">這可能會包含單一值，或以空格分隔的值清單。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-115">This may contain a single value, or a space delimited list of values.</span></span>|  
  
 <span data-ttu-id="dd2c5-116">下表顯示觸發程序註解，因為它會在處理區段之後，會出現在 HIPAA 結構描述會導致觸發程序啟用時，EDI 區段，產生的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-116">The following table shows the trigger annotation as it would appear in the HIPAA schema, the EDI segment that will cause the trigger to activate, and the resulting XML data after processing the segment.</span></span>  
  
|<span data-ttu-id="dd2c5-117">結構描述的觸發程序註解</span><span class="sxs-lookup"><span data-stu-id="dd2c5-117">Schema Trigger Annotation</span></span>|<span data-ttu-id="dd2c5-118">比對 N1 區段</span><span class="sxs-lookup"><span data-stu-id="dd2c5-118">Matching N1 Segment</span></span>|<span data-ttu-id="dd2c5-119">結果產生的 XML 資料</span><span class="sxs-lookup"><span data-stu-id="dd2c5-119">Resulting XML Data</span></span>|  
|-------------------------------|-------------------------|------------------------|  
|`<xs:element name="TS835W1_1000A_Loop">  <xs:annotation>   <xs:appinfo>    <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayerIdentification_TS835W1_1000A/N101__EntityIdentifierCode"     trigger_value="PR" notes="Payer Identification" />    </xs:appinfo>  </xs:annotation>`|<span data-ttu-id="dd2c5-120">N1 * PR\*Contoso\*1763\*0000000 ~</span><span class="sxs-lookup"><span data-stu-id="dd2c5-120">N1*PR\*Contoso\*XV\*0000000~</span></span>|`<ns0:TS835W1_1000A_Loop>  <N1_PayerIdentification_TS835W1_1000A>   <N101__EntityIdentifierCode>PR</N101__EntityIdentifierCode>    <N102__PayerName>Contoso</N102__PayerName>    <N103__IdentificationCodeQualifier>XV</N103__IdentificationCodeQualifier>    <N104__PayerIdentifier>0000000</N104__PayerIdentifier>   </N1_PayerIdentification_TS835W1_1000A>`|  
|`<xs:element name="TS835W1_1000B_Loop">   <xs:annotation>    <xs:appinfo>     <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayeeIdentification_TS835W1_1000B/N101__EntityIdentifierCode"     trigger_value="PE" notes="Payee Identification" />    </xs:appinfo>   </xs:annotation>`|<span data-ttu-id="dd2c5-121">N1 * PE\*Fabrikam\*FI\*9999999 ~</span><span class="sxs-lookup"><span data-stu-id="dd2c5-121">N1*PE\*Fabrikam\*FI\*9999999~</span></span>|`<TS835W1_1000B_Loop>   <N1_PayeeIdentification_TS835W1_1000B>    <N101__EntityIdentifierCode>PE</N101__EntityIdentifierCode>    <N102__PayeeName>Fabrikam</N102__PayeeName>    <N103__IdentificationCodeQualifier>FI</N103__IdentificationCodeQualifier>    <N104__PayeeIdentificationCode>9999999</N104__PayeeIdentificationCode>   </N1_PayeeIdentification_TS835W1_1000B>`|  
  
 <span data-ttu-id="dd2c5-122">**EDI 解譯器處理的觸發程序欄位**</span><span class="sxs-lookup"><span data-stu-id="dd2c5-122">**EDI Disassembler Processing of Trigger Fields**</span></span>  
  
 <span data-ttu-id="dd2c5-123">當收到 HIPAA 交易設定，如果 EDI 解譯器遇到含有觸發程序欄位的區段時，它會使用觸發程序資訊來產生區段和觸發程序組合特有的 XML 記錄。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-123">When receiving a HIPAA transaction set, if the EDI disassembler encounters a segment that contains a trigger field, it uses the trigger information to generate an XML record specific to the segment and trigger combination.</span></span> <span data-ttu-id="dd2c5-124">比方說，在下列 EDI 資料中，有兩個具有不同的值 N101、 PR 和 PE 的 N1 區段︰</span><span class="sxs-lookup"><span data-stu-id="dd2c5-124">For example, in the following EDI data, there are two N1 segments that have different values for N101, PR and PE:</span></span>  
  
```  
  
N1*PR*Contoso*XV*0000000~  
N3*N301__PayerAddressLine~  
N4*N401__PayerCityName*N4*N403__PayerPost**N4*N406~  
……  
N1*PE*Fabrikam*FI*9999999~  
N3*N301__PayeeAddressLine~  
N4*N401__PayeeCityName*N4*N403__PayeePost**N4*N406~  
  
```  
  
 <span data-ttu-id="dd2c5-125">當處理 EDI 解譯器，存在於結構描述的觸發程序欄位註解會導致兩個獨立的 XML 記錄根據 N101，< N1_PayerIdentification_TS835W1_1000A > 值 < N1_PayeeIdentification_TS835W1_1000B >，並對應至 N1 * PR 和 N1\*PE。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-125">When processed by the EDI disassembler, the trigger field annotations present in the schema will result in two separate XML records based on the value of N101, <N1_PayerIdentification_TS835W1_1000A> and <N1_PayeeIdentification_TS835W1_1000B>, corresponding to N1*PR and N1\*PE.</span></span>  
  
 <span data-ttu-id="dd2c5-126">傳送時，EDI 組合器將會卸除後置字元"_"字元，包含觸發程序註解欄位的後面。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-126">When sending, the EDI assembler will drop the suffix following the “_” character for fields that contain a trigger annotation.</span></span> <span data-ttu-id="dd2c5-127">比方說，這兩個 < N1_PayerIdentification_TS835W1_1000A > 和 < N1_PayeeIdentification_TS835W1_1000B > 將兩者都變成 N1。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-127">For example, both <N1_PayerIdentification_TS835W1_1000A> and <N1_PayeeIdentification_TS835W1_1000B> will both become N1.</span></span>  
  
 <span data-ttu-id="dd2c5-128">**預設值區段和觸發程序欄位**</span><span class="sxs-lookup"><span data-stu-id="dd2c5-128">**Default Segments and Trigger Fields**</span></span>  
  
 <span data-ttu-id="dd2c5-129">下表包含預設值區段和 HIPAA 文件提供 BizTalk Server 的過程中使用的觸發程序欄位的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="dd2c5-129">The following table contains information on the default segments and trigger fields used in HIPAA documents supplied as part of BizTalk Server:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd2c5-130">觸發程序欄位搭配使用個別的觸發程序值可能不同結構描述之間。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-130">The individual trigger values used with the trigger fields may vary between schemas.</span></span>  
  
|<span data-ttu-id="dd2c5-131">觸發程序具有區段。</span><span class="sxs-lookup"><span data-stu-id="dd2c5-131">Segment with Trigger</span></span>|<span data-ttu-id="dd2c5-132">觸發程序欄位</span><span class="sxs-lookup"><span data-stu-id="dd2c5-132">Trigger field</span></span>|  
|--------------------------|-------------------|  
|<span data-ttu-id="dd2c5-133">AMT</span><span class="sxs-lookup"><span data-stu-id="dd2c5-133">AMT</span></span>|<span data-ttu-id="dd2c5-134">AMT01</span><span class="sxs-lookup"><span data-stu-id="dd2c5-134">AMT01</span></span>|  
|<span data-ttu-id="dd2c5-135">CRC</span><span class="sxs-lookup"><span data-stu-id="dd2c5-135">CRC</span></span>|<span data-ttu-id="dd2c5-136">CRC01</span><span class="sxs-lookup"><span data-stu-id="dd2c5-136">CRC01</span></span>|  
|<span data-ttu-id="dd2c5-137">DTM</span><span class="sxs-lookup"><span data-stu-id="dd2c5-137">DTM</span></span>|<span data-ttu-id="dd2c5-138">DTM01</span><span class="sxs-lookup"><span data-stu-id="dd2c5-138">DTM01</span></span>|  
|<span data-ttu-id="dd2c5-139">DTP</span><span class="sxs-lookup"><span data-stu-id="dd2c5-139">DTP</span></span>|<span data-ttu-id="dd2c5-140">DTP01</span><span class="sxs-lookup"><span data-stu-id="dd2c5-140">DTP01</span></span>|  
|<span data-ttu-id="dd2c5-141">輸入</span><span class="sxs-lookup"><span data-stu-id="dd2c5-141">ENT</span></span>|<span data-ttu-id="dd2c5-142">ENT02</span><span class="sxs-lookup"><span data-stu-id="dd2c5-142">ENT02</span></span>|  
|<span data-ttu-id="dd2c5-143">HI</span><span class="sxs-lookup"><span data-stu-id="dd2c5-143">HI</span></span>|<span data-ttu-id="dd2c5-144">HI01:01</span><span class="sxs-lookup"><span data-stu-id="dd2c5-144">HI01:01</span></span>|  
|<span data-ttu-id="dd2c5-145">N1</span><span class="sxs-lookup"><span data-stu-id="dd2c5-145">N1</span></span>|<span data-ttu-id="dd2c5-146">N101</span><span class="sxs-lookup"><span data-stu-id="dd2c5-146">N101</span></span>|  
|<span data-ttu-id="dd2c5-147">NM1</span><span class="sxs-lookup"><span data-stu-id="dd2c5-147">NM1</span></span>|<span data-ttu-id="dd2c5-148">NM01</span><span class="sxs-lookup"><span data-stu-id="dd2c5-148">NM01</span></span>|  
|<span data-ttu-id="dd2c5-149">NTE</span><span class="sxs-lookup"><span data-stu-id="dd2c5-149">NTE</span></span>|<span data-ttu-id="dd2c5-150">NTE01</span><span class="sxs-lookup"><span data-stu-id="dd2c5-150">NTE01</span></span>|  
|<span data-ttu-id="dd2c5-151">REF</span><span class="sxs-lookup"><span data-stu-id="dd2c5-151">REF</span></span>|<span data-ttu-id="dd2c5-152">REF01</span><span class="sxs-lookup"><span data-stu-id="dd2c5-152">REF01</span></span>|  
|<span data-ttu-id="dd2c5-153">RMR</span><span class="sxs-lookup"><span data-stu-id="dd2c5-153">RMR</span></span>|<span data-ttu-id="dd2c5-154">RMR01</span><span class="sxs-lookup"><span data-stu-id="dd2c5-154">RMR01</span></span>|