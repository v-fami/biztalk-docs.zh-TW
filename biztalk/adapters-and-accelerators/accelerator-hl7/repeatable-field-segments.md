---
title: 可重複的欄位區段 |Microsoft 文件
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
ms.openlocfilehash: a801e39fac0e0bdf0cfb9ee88811703fd1c4373d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206326"
---
# <a name="repeatable-field-segments"></a><span data-ttu-id="ce9ba-102">可重複的欄位區段</span><span class="sxs-lookup"><span data-stu-id="ce9ba-102">Repeatable Field Segments</span></span>
<span data-ttu-id="ce9ba-103">HL7 Access 資料庫中的區段資料表包含資料行區段 （ADD、 RDT 和 QPD） 的最後一個欄位， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 定義為可重複 (**Last_field_repeatable**  = **True**)。</span><span class="sxs-lookup"><span data-stu-id="ce9ba-103">The Segments table in the HL7 Access database contains a column for the last field of segments (ADD, RDT, and QPD) that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) defines as repeatable (**Last_field_repeatable** = **True**).</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="ce9ba-104">不支援新增。</span><span class="sxs-lookup"><span data-stu-id="ce9ba-104"> does not support ADD.</span></span> <span data-ttu-id="ce9ba-105">不過，RDT 和 QPD 出現查詢資料表，並以資料表值的回應。</span><span class="sxs-lookup"><span data-stu-id="ce9ba-105">However, both RDT and QPD are present to query tables and respond with table values.</span></span> <span data-ttu-id="ce9ba-106">下列範例將示範如何[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理這些資料行。</span><span class="sxs-lookup"><span data-stu-id="ce9ba-106">The following sample demonstrates how [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] handles these columns.</span></span>  
  
 <span data-ttu-id="ce9ba-107">用戶端送出下列查詢，並指出用戶端想立即回應，藉由設定**RCP-1-回應優先順序**至 「**我**":</span><span class="sxs-lookup"><span data-stu-id="ce9ba-107">A client submits the following query and indicates that the client wants an immediate response by setting **RCP-1-Response priority** to "**I**":</span></span>  
  
```  
MSH|^&~\|PCR|Gen Hosp|PIMS||199811201400-0800||QBP^Q42^QBP_Q13|ACK9901|P|2.4||||||||  
QPD|Q42^Tabular Dispense History^HL7nnn|Q0010|555444222111^^^MPI^MR| |19980531|19990531|  
RCP|I|999^RD|  
RDF|3|PatientList^ST^20~PatientName^XPN^48~MedicationDispensed^ST^40~RXD.3^TS^26  
```  
  
 <span data-ttu-id="ce9ba-108">伺服器會回應一分鐘之後出現下列訊息：</span><span class="sxs-lookup"><span data-stu-id="ce9ba-108">The server responds one minute later with the following message:</span></span>  
  
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
  
 <span data-ttu-id="ce9ba-109">此範例中，從您看到 QPD 和 RDT 所定義的自訂/站台。</span><span class="sxs-lookup"><span data-stu-id="ce9ba-109">From the example, you see that QPD and RDT are custom/site defined.</span></span> <span data-ttu-id="ce9ba-110">HL7 規格會定義 QPD 和 RDT 區段，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ce9ba-110">The HL7 specification defines QPD and RDT segments as follows.</span></span>  
  
## <a name="qpd---query-parameter-definition"></a><span data-ttu-id="ce9ba-111">QPD-查詢參數定義</span><span class="sxs-lookup"><span data-stu-id="ce9ba-111">QPD - Query Parameter Definition</span></span>  
 <span data-ttu-id="ce9ba-112">下表顯示如何 HL7 規格定義 QPD。</span><span class="sxs-lookup"><span data-stu-id="ce9ba-112">The following table shows how the HL7 specification defines QPD.</span></span>  
  
|<span data-ttu-id="ce9ba-113">SEQ</span><span class="sxs-lookup"><span data-stu-id="ce9ba-113">SEQ</span></span>|<span data-ttu-id="ce9ba-114">LEN</span><span class="sxs-lookup"><span data-stu-id="ce9ba-114">LEN</span></span>|<span data-ttu-id="ce9ba-115">DT</span><span class="sxs-lookup"><span data-stu-id="ce9ba-115">DT</span></span>|<span data-ttu-id="ce9ba-116">選擇加入</span><span class="sxs-lookup"><span data-stu-id="ce9ba-116">OPT</span></span>|<span data-ttu-id="ce9ba-117">RP / #</span><span class="sxs-lookup"><span data-stu-id="ce9ba-117">RP/#</span></span>|<span data-ttu-id="ce9ba-118">TBL #</span><span class="sxs-lookup"><span data-stu-id="ce9ba-118">TBL#</span></span>|<span data-ttu-id="ce9ba-119">項目 #</span><span class="sxs-lookup"><span data-stu-id="ce9ba-119">ITEM#</span></span>|<span data-ttu-id="ce9ba-120">項目名稱</span><span class="sxs-lookup"><span data-stu-id="ce9ba-120">ELEMENT NAME</span></span>|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|<span data-ttu-id="ce9ba-121">1</span><span class="sxs-lookup"><span data-stu-id="ce9ba-121">1</span></span>|<span data-ttu-id="ce9ba-122">250</span><span class="sxs-lookup"><span data-stu-id="ce9ba-122">250</span></span>|<span data-ttu-id="ce9ba-123">CE</span><span class="sxs-lookup"><span data-stu-id="ce9ba-123">CE</span></span>|<span data-ttu-id="ce9ba-124">R</span><span class="sxs-lookup"><span data-stu-id="ce9ba-124">R</span></span>||<span data-ttu-id="ce9ba-125">0471</span><span class="sxs-lookup"><span data-stu-id="ce9ba-125">0471</span></span>|<span data-ttu-id="ce9ba-126">01375</span><span class="sxs-lookup"><span data-stu-id="ce9ba-126">01375</span></span>|<span data-ttu-id="ce9ba-127">訊息查詢名稱</span><span class="sxs-lookup"><span data-stu-id="ce9ba-127">Message Query Name</span></span>|  
|<span data-ttu-id="ce9ba-128">2</span><span class="sxs-lookup"><span data-stu-id="ce9ba-128">2</span></span>|<span data-ttu-id="ce9ba-129">32</span><span class="sxs-lookup"><span data-stu-id="ce9ba-129">32</span></span>|<span data-ttu-id="ce9ba-130">ST</span><span class="sxs-lookup"><span data-stu-id="ce9ba-130">ST</span></span>|<span data-ttu-id="ce9ba-131">C</span><span class="sxs-lookup"><span data-stu-id="ce9ba-131">C</span></span>|||<span data-ttu-id="ce9ba-132">00696</span><span class="sxs-lookup"><span data-stu-id="ce9ba-132">00696</span></span>|<span data-ttu-id="ce9ba-133">查詢標記</span><span class="sxs-lookup"><span data-stu-id="ce9ba-133">Query Tag</span></span>|  
|<span data-ttu-id="ce9ba-134">3-n</span><span class="sxs-lookup"><span data-stu-id="ce9ba-134">3-n</span></span>|<span data-ttu-id="ce9ba-135">256</span><span class="sxs-lookup"><span data-stu-id="ce9ba-135">256</span></span>|<span data-ttu-id="ce9ba-136">非固定</span><span class="sxs-lookup"><span data-stu-id="ce9ba-136">Varies</span></span>||||<span data-ttu-id="ce9ba-137">01435</span><span class="sxs-lookup"><span data-stu-id="ce9ba-137">01435</span></span>|<span data-ttu-id="ce9ba-138">使用者在後續的欄位中的參數</span><span class="sxs-lookup"><span data-stu-id="ce9ba-138">User parameters in successive fields</span></span>|  
  
## <a name="rdt---table-row-data"></a><span data-ttu-id="ce9ba-139">RDT-資料表的資料列資料</span><span class="sxs-lookup"><span data-stu-id="ce9ba-139">RDT - Table Row Data</span></span>  
 <span data-ttu-id="ce9ba-140">下表顯示如何 HL7 規格定義 RDT。</span><span class="sxs-lookup"><span data-stu-id="ce9ba-140">The following table shows how the HL7 specification defines RDT.</span></span>  
  
|<span data-ttu-id="ce9ba-141">SEQ</span><span class="sxs-lookup"><span data-stu-id="ce9ba-141">SEQ</span></span>|<span data-ttu-id="ce9ba-142">LEN</span><span class="sxs-lookup"><span data-stu-id="ce9ba-142">LEN</span></span>|<span data-ttu-id="ce9ba-143">DT</span><span class="sxs-lookup"><span data-stu-id="ce9ba-143">DT</span></span>|<span data-ttu-id="ce9ba-144">選擇加入</span><span class="sxs-lookup"><span data-stu-id="ce9ba-144">OPT</span></span>|<span data-ttu-id="ce9ba-145">RP / #</span><span class="sxs-lookup"><span data-stu-id="ce9ba-145">RP/#</span></span>|<span data-ttu-id="ce9ba-146">TBL #</span><span class="sxs-lookup"><span data-stu-id="ce9ba-146">TBL#</span></span>|<span data-ttu-id="ce9ba-147">項目 #</span><span class="sxs-lookup"><span data-stu-id="ce9ba-147">ITEM#</span></span>|<span data-ttu-id="ce9ba-148">項目名稱</span><span class="sxs-lookup"><span data-stu-id="ce9ba-148">ELEMENT NAME</span></span>|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|<span data-ttu-id="ce9ba-149">1-n</span><span class="sxs-lookup"><span data-stu-id="ce9ba-149">1-n</span></span>|<span data-ttu-id="ce9ba-150">變數</span><span class="sxs-lookup"><span data-stu-id="ce9ba-150">Variable</span></span>|<span data-ttu-id="ce9ba-151">變數</span><span class="sxs-lookup"><span data-stu-id="ce9ba-151">Variable</span></span>|<span data-ttu-id="ce9ba-152">R</span><span class="sxs-lookup"><span data-stu-id="ce9ba-152">R</span></span>|||<span data-ttu-id="ce9ba-153">00703</span><span class="sxs-lookup"><span data-stu-id="ce9ba-153">00703</span></span>|<span data-ttu-id="ce9ba-154">資料行值</span><span class="sxs-lookup"><span data-stu-id="ce9ba-154">Column Value</span></span>|  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="ce9ba-155">解譯 QPD 和 RDT 做為可重複的站台定義值。</span><span class="sxs-lookup"><span data-stu-id="ce9ba-155"> interprets QPD and RDT as site-defined values that can repeat.</span></span> <span data-ttu-id="ce9ba-156">因為[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不能解決問題的資料類型和其他詳細資料， [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] QPD.3 和 RDT.1 視為字串的結構描述中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ce9ba-156">Since [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not fix the data types and other details, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] treats QPD.3 and RDT.1 as String data types in the schemas.</span></span> <span data-ttu-id="ce9ba-157">您可能必須修改這些結構描述，依據您的站台的條件。</span><span class="sxs-lookup"><span data-stu-id="ce9ba-157">You may have to modify these schemas depending on your own site conditions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9ba-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce9ba-158">See Also</span></span>  
 [<span data-ttu-id="ce9ba-159">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="ce9ba-159">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)