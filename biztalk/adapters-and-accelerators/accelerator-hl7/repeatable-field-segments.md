---
title: 可重複的欄位區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- segments, repeatable fields
- QPD
- Table Row Data (RDT)
- Query Parameter Definition (QPD)
- Segments table
- RDT
ms.assetid: 4c31cb56-21e5-4918-aaf6-67e8ceddd74f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9651b8d3414f792b81633cafbe41dd66559df04c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981975"
---
# <a name="repeatable-field-segments"></a><span data-ttu-id="634e7-102">可重複的欄位區段</span><span class="sxs-lookup"><span data-stu-id="634e7-102">Repeatable Field Segments</span></span>
<span data-ttu-id="634e7-103">HL7 Access 資料庫中的區段資料表包含資料行的區段 （ADD、 RDT 和 QPD） 和最後一個欄位，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會定義為可重複 (**Last_field_repeatable**  =  **，則為 true**)。</span><span class="sxs-lookup"><span data-stu-id="634e7-103">The Segments table in the HL7 Access database contains a column for the last field of segments (ADD, RDT, and QPD) that Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) defines as repeatable (**Last_field_repeatable** = **True**).</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="634e7-104"> 不支援新增。</span><span class="sxs-lookup"><span data-stu-id="634e7-104"> does not support ADD.</span></span> <span data-ttu-id="634e7-105">不過，同時 RDT QPD 有查詢資料表並以資料表值的回應。</span><span class="sxs-lookup"><span data-stu-id="634e7-105">However, both RDT and QPD are present to query tables and respond with table values.</span></span> <span data-ttu-id="634e7-106">下列範例會示範如何[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理這些資料行。</span><span class="sxs-lookup"><span data-stu-id="634e7-106">The following sample demonstrates how [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] handles these columns.</span></span>  
  
 <span data-ttu-id="634e7-107">在用戶端提交下列查詢，與指出用戶端設定需要立即回應**RCP-1-回應的優先順序**到 「**我**」:</span><span class="sxs-lookup"><span data-stu-id="634e7-107">A client submits the following query and indicates that the client wants an immediate response by setting **RCP-1-Response priority** to "**I**":</span></span>  
  
```  
MSH|^&~\|PCR|Gen Hosp|PIMS||199811201400-0800||QBP^Q42^QBP_Q13|ACK9901|P|2.4||||||||  
QPD|Q42^Tabular Dispense History^HL7nnn|Q0010|555444222111^^^MPI^MR| |19980531|19990531|  
RCP|I|999^RD|  
RDF|3|PatientList^ST^20~PatientName^XPN^48~MedicationDispensed^ST^40~RXD.3^TS^26  
```  
  
 <span data-ttu-id="634e7-108">伺服器會回應一分鐘之後出現下列訊息：</span><span class="sxs-lookup"><span data-stu-id="634e7-108">The server responds one minute later with the following message:</span></span>  
  
```  
MSH|^&~\|PIMS|Gen Hosp|PCR||199811201401-0800||RTB^K42^RTB_K13|8858|P|2.3||||||||  
MSA|AA|8699|  
QAK|Q010|OK|Q42^Tabular Dispense History^HL7nnn|4  
QPD|Q42^Tabular Dispense History^HL7nnn|Q0010|555444222111^^^MPI^MR||19980531|19990531|  
RDF|7|PatientId^CX^20~PatientName^XPN^48~OrderControlCode^ID^2~ MedicationDispensed^CE^100~DispenseDate^TS^26~QuantityDispensed^NM^20~ OrderingProvider^XCN^120  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|525440345^Verapamil Hydrochloride 120 mg TAB^NDC |199805291115-0700|100|77^Hippocrates^Harold^H^III^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00182196901^VERAPAMIL HCL ER TAB 180MG ER^NDC |19980821-0700|100|77^Hippocrates^Harold^H^III^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00172409660^BACLOFEN 10MG TABS^NDC |199809221415-0700|10|88^Semmelweis^Samuel^^^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00054384163^THEOPHYLLINE 80MG/15ML SOLN^NDC|199810121145-0700|10|99^Lister^Lenora^^^DR^MD  
```  
  
 <span data-ttu-id="634e7-109">從範例中，您會看到 QPD 和 RDT 所定義的自訂/站台。</span><span class="sxs-lookup"><span data-stu-id="634e7-109">From the example, you see that QPD and RDT are custom/site defined.</span></span> <span data-ttu-id="634e7-110">HL7 規格會定義 QPD 和 RDT 區段，如下所示。</span><span class="sxs-lookup"><span data-stu-id="634e7-110">The HL7 specification defines QPD and RDT segments as follows.</span></span>  
  
## <a name="qpd---query-parameter-definition"></a><span data-ttu-id="634e7-111">QPD-查詢參數定義</span><span class="sxs-lookup"><span data-stu-id="634e7-111">QPD - Query Parameter Definition</span></span>  
 <span data-ttu-id="634e7-112">下表顯示如何 HL7 規格定義 QPD。</span><span class="sxs-lookup"><span data-stu-id="634e7-112">The following table shows how the HL7 specification defines QPD.</span></span>  
  
|<span data-ttu-id="634e7-113">SEQ</span><span class="sxs-lookup"><span data-stu-id="634e7-113">SEQ</span></span>|<span data-ttu-id="634e7-114">LEN</span><span class="sxs-lookup"><span data-stu-id="634e7-114">LEN</span></span>|<span data-ttu-id="634e7-115">DT</span><span class="sxs-lookup"><span data-stu-id="634e7-115">DT</span></span>|<span data-ttu-id="634e7-116">選擇加入</span><span class="sxs-lookup"><span data-stu-id="634e7-116">OPT</span></span>|<span data-ttu-id="634e7-117">RP / #</span><span class="sxs-lookup"><span data-stu-id="634e7-117">RP/#</span></span>|<span data-ttu-id="634e7-118">TBL #</span><span class="sxs-lookup"><span data-stu-id="634e7-118">TBL#</span></span>|<span data-ttu-id="634e7-119">項目 #</span><span class="sxs-lookup"><span data-stu-id="634e7-119">ITEM#</span></span>|<span data-ttu-id="634e7-120">項目名稱</span><span class="sxs-lookup"><span data-stu-id="634e7-120">ELEMENT NAME</span></span>|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|<span data-ttu-id="634e7-121">@shouldalert</span><span class="sxs-lookup"><span data-stu-id="634e7-121">1</span></span>|<span data-ttu-id="634e7-122">250</span><span class="sxs-lookup"><span data-stu-id="634e7-122">250</span></span>|<span data-ttu-id="634e7-123">CE</span><span class="sxs-lookup"><span data-stu-id="634e7-123">CE</span></span>|<span data-ttu-id="634e7-124">R</span><span class="sxs-lookup"><span data-stu-id="634e7-124">R</span></span>||<span data-ttu-id="634e7-125">0471</span><span class="sxs-lookup"><span data-stu-id="634e7-125">0471</span></span>|<span data-ttu-id="634e7-126">01375</span><span class="sxs-lookup"><span data-stu-id="634e7-126">01375</span></span>|<span data-ttu-id="634e7-127">訊息查詢名稱</span><span class="sxs-lookup"><span data-stu-id="634e7-127">Message Query Name</span></span>|  
|<span data-ttu-id="634e7-128">2</span><span class="sxs-lookup"><span data-stu-id="634e7-128">2</span></span>|<span data-ttu-id="634e7-129">32</span><span class="sxs-lookup"><span data-stu-id="634e7-129">32</span></span>|<span data-ttu-id="634e7-130">ST</span><span class="sxs-lookup"><span data-stu-id="634e7-130">ST</span></span>|<span data-ttu-id="634e7-131">c</span><span class="sxs-lookup"><span data-stu-id="634e7-131">C</span></span>|||<span data-ttu-id="634e7-132">00696</span><span class="sxs-lookup"><span data-stu-id="634e7-132">00696</span></span>|<span data-ttu-id="634e7-133">查詢標記</span><span class="sxs-lookup"><span data-stu-id="634e7-133">Query Tag</span></span>|  
|<span data-ttu-id="634e7-134">3-n</span><span class="sxs-lookup"><span data-stu-id="634e7-134">3-n</span></span>|<span data-ttu-id="634e7-135">256</span><span class="sxs-lookup"><span data-stu-id="634e7-135">256</span></span>|<span data-ttu-id="634e7-136">非固定</span><span class="sxs-lookup"><span data-stu-id="634e7-136">Varies</span></span>||||<span data-ttu-id="634e7-137">01435</span><span class="sxs-lookup"><span data-stu-id="634e7-137">01435</span></span>|<span data-ttu-id="634e7-138">在後續的欄位中的使用者參數</span><span class="sxs-lookup"><span data-stu-id="634e7-138">User parameters in successive fields</span></span>|  
  
## <a name="rdt---table-row-data"></a><span data-ttu-id="634e7-139">RDT-資料表資料列資料</span><span class="sxs-lookup"><span data-stu-id="634e7-139">RDT - Table Row Data</span></span>  
 <span data-ttu-id="634e7-140">下表顯示如何 HL7 規格定義 RDT。</span><span class="sxs-lookup"><span data-stu-id="634e7-140">The following table shows how the HL7 specification defines RDT.</span></span>  
  
|<span data-ttu-id="634e7-141">SEQ</span><span class="sxs-lookup"><span data-stu-id="634e7-141">SEQ</span></span>|<span data-ttu-id="634e7-142">LEN</span><span class="sxs-lookup"><span data-stu-id="634e7-142">LEN</span></span>|<span data-ttu-id="634e7-143">DT</span><span class="sxs-lookup"><span data-stu-id="634e7-143">DT</span></span>|<span data-ttu-id="634e7-144">選擇加入</span><span class="sxs-lookup"><span data-stu-id="634e7-144">OPT</span></span>|<span data-ttu-id="634e7-145">RP / #</span><span class="sxs-lookup"><span data-stu-id="634e7-145">RP/#</span></span>|<span data-ttu-id="634e7-146">TBL #</span><span class="sxs-lookup"><span data-stu-id="634e7-146">TBL#</span></span>|<span data-ttu-id="634e7-147">項目 #</span><span class="sxs-lookup"><span data-stu-id="634e7-147">ITEM#</span></span>|<span data-ttu-id="634e7-148">項目名稱</span><span class="sxs-lookup"><span data-stu-id="634e7-148">ELEMENT NAME</span></span>|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|<span data-ttu-id="634e7-149">1-n</span><span class="sxs-lookup"><span data-stu-id="634e7-149">1-n</span></span>|<span data-ttu-id="634e7-150">變數</span><span class="sxs-lookup"><span data-stu-id="634e7-150">Variable</span></span>|<span data-ttu-id="634e7-151">變數</span><span class="sxs-lookup"><span data-stu-id="634e7-151">Variable</span></span>|<span data-ttu-id="634e7-152">R</span><span class="sxs-lookup"><span data-stu-id="634e7-152">R</span></span>|||<span data-ttu-id="634e7-153">00703</span><span class="sxs-lookup"><span data-stu-id="634e7-153">00703</span></span>|<span data-ttu-id="634e7-154">資料行值</span><span class="sxs-lookup"><span data-stu-id="634e7-154">Column Value</span></span>|  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="634e7-155"> QPD 和 RDT 解譯可以重複的網站定義值。</span><span class="sxs-lookup"><span data-stu-id="634e7-155"> interprets QPD and RDT as site-defined values that can repeat.</span></span> <span data-ttu-id="634e7-156">由於[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不能解決問題的資料類型和其他詳細資料， [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] QPD.3 和 RDT.1 視為字串的結構描述中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="634e7-156">Since [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not fix the data types and other details, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] treats QPD.3 and RDT.1 as String data types in the schemas.</span></span> <span data-ttu-id="634e7-157">您可能要修改這些結構描述，根據您自己的站台條件。</span><span class="sxs-lookup"><span data-stu-id="634e7-157">You may have to modify these schemas depending on your own site conditions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="634e7-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="634e7-158">See Also</span></span>  
 [<span data-ttu-id="634e7-159">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="634e7-159">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)