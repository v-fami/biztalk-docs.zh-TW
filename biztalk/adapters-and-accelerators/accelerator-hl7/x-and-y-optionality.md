---
title: '&#39;X&#39;和&#39;Y&#39;選擇性 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- segments, Y optionality
- segments, SegmentDataElements table
- SegmentDataElements table
- segments, X optionality
ms.assetid: 8a59b407-95a2-45ba-a8d6-db4154c91d7b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aed5b87216bd2d8e127ff032e3773b3f740835c9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981519"
---
# <a name="39x39-and-39y39-optionality"></a><span data-ttu-id="82604-102">&#39;X&#39;和&#39;Y&#39;選用性</span><span class="sxs-lookup"><span data-stu-id="82604-102">&#39;X&#39; and &#39;Y&#39; Optionality</span></span>
<span data-ttu-id="82604-103">HL7 Access 資料庫中的 SegmentDataElements 資料表包含數個資料的項目 （欄位） 已設為**Req/Opt = X**，這表示 HL7 標準不會將這個欄位關聯與此觸發程序事件，如中所示下表。</span><span class="sxs-lookup"><span data-stu-id="82604-103">The SegmentDataElements table in the HL7 Access database contains several Data Items (fields) that have been set as **Req/Opt = X**, meaning that the HL7 standard does not associate this field with this trigger event, as shown in the following table.</span></span>  
  
|<span data-ttu-id="82604-104">區段</span><span class="sxs-lookup"><span data-stu-id="82604-104">Segment</span></span>|<span data-ttu-id="82604-105">版本</span><span class="sxs-lookup"><span data-stu-id="82604-105">Version</span></span>|<span data-ttu-id="82604-106">章節</span><span class="sxs-lookup"><span data-stu-id="82604-106">Chapter</span></span>|<span data-ttu-id="82604-107">資料項目</span><span class="sxs-lookup"><span data-stu-id="82604-107">Data Item</span></span>|<span data-ttu-id="82604-108">必要 /</span><span class="sxs-lookup"><span data-stu-id="82604-108">Required/</span></span><br /><br /> <span data-ttu-id="82604-109">選擇性</span><span class="sxs-lookup"><span data-stu-id="82604-109">Optional</span></span>|<span data-ttu-id="82604-110">報表</span><span class="sxs-lookup"><span data-stu-id="82604-110">Report</span></span>|<span data-ttu-id="82604-111">Number</span><span class="sxs-lookup"><span data-stu-id="82604-111">Number</span></span>|<span data-ttu-id="82604-112">HTML 標準</span><span class="sxs-lookup"><span data-stu-id="82604-112">HTML Standard</span></span>|  
|-------------|-------------|-------------|---------------|-----------------------------|------------|------------|-------------------|  
|<span data-ttu-id="82604-113">OBX</span><span class="sxs-lookup"><span data-stu-id="82604-113">OBX</span></span>|<span data-ttu-id="82604-114">2.4</span><span class="sxs-lookup"><span data-stu-id="82604-114">2.4</span></span>|<span data-ttu-id="82604-115">7.4.2.9</span><span class="sxs-lookup"><span data-stu-id="82604-115">7.4.2.9</span></span>|<span data-ttu-id="82604-116">00577</span><span class="sxs-lookup"><span data-stu-id="82604-116">00577</span></span>|<span data-ttu-id="82604-117">X</span><span class="sxs-lookup"><span data-stu-id="82604-117">X</span></span>|<span data-ttu-id="82604-118">Y</span><span class="sxs-lookup"><span data-stu-id="82604-118">Y</span></span>|<span data-ttu-id="82604-119">5</span><span class="sxs-lookup"><span data-stu-id="82604-119">5</span></span>|<span data-ttu-id="82604-120">ch07.htm#Heading113</span><span class="sxs-lookup"><span data-stu-id="82604-120">ch07.htm#Heading113</span></span>|  
|<span data-ttu-id="82604-121">OBX</span><span class="sxs-lookup"><span data-stu-id="82604-121">OBX</span></span>|<span data-ttu-id="82604-122">2.4</span><span class="sxs-lookup"><span data-stu-id="82604-122">2.4</span></span>|<span data-ttu-id="82604-123">7.4.2.8</span><span class="sxs-lookup"><span data-stu-id="82604-123">7.4.2.8</span></span>|<span data-ttu-id="82604-124">00576</span><span class="sxs-lookup"><span data-stu-id="82604-124">00576</span></span>|<span data-ttu-id="82604-125">X</span><span class="sxs-lookup"><span data-stu-id="82604-125">X</span></span>||<span data-ttu-id="82604-126">0</span><span class="sxs-lookup"><span data-stu-id="82604-126">0</span></span>|<span data-ttu-id="82604-127">ch07.htm#Heading112</span><span class="sxs-lookup"><span data-stu-id="82604-127">ch07.htm#Heading112</span></span>|  
|<span data-ttu-id="82604-128">OBX</span><span class="sxs-lookup"><span data-stu-id="82604-128">OBX</span></span>|<span data-ttu-id="82604-129">2.4</span><span class="sxs-lookup"><span data-stu-id="82604-129">2.4</span></span>|<span data-ttu-id="82604-130">7.4.2.6</span><span class="sxs-lookup"><span data-stu-id="82604-130">7.4.2.6</span></span>|<span data-ttu-id="82604-131">00574</span><span class="sxs-lookup"><span data-stu-id="82604-131">00574</span></span>|<span data-ttu-id="82604-132">X</span><span class="sxs-lookup"><span data-stu-id="82604-132">X</span></span>||<span data-ttu-id="82604-133">0</span><span class="sxs-lookup"><span data-stu-id="82604-133">0</span></span>|<span data-ttu-id="82604-134">ch07.htm#Heading107</span><span class="sxs-lookup"><span data-stu-id="82604-134">ch07.htm#Heading107</span></span>|  
|<span data-ttu-id="82604-135">OBX</span><span class="sxs-lookup"><span data-stu-id="82604-135">OBX</span></span>|<span data-ttu-id="82604-136">2.4</span><span class="sxs-lookup"><span data-stu-id="82604-136">2.4</span></span>|<span data-ttu-id="82604-137">7.4.2.17</span><span class="sxs-lookup"><span data-stu-id="82604-137">7.4.2.17</span></span>|<span data-ttu-id="82604-138">00936</span><span class="sxs-lookup"><span data-stu-id="82604-138">00936</span></span>|<span data-ttu-id="82604-139">X</span><span class="sxs-lookup"><span data-stu-id="82604-139">X</span></span>|<span data-ttu-id="82604-140">Y</span><span class="sxs-lookup"><span data-stu-id="82604-140">Y</span></span>|<span data-ttu-id="82604-141">0</span><span class="sxs-lookup"><span data-stu-id="82604-141">0</span></span>|<span data-ttu-id="82604-142">ch07.htm#Heading121</span><span class="sxs-lookup"><span data-stu-id="82604-142">ch07.htm#Heading121</span></span>|  
  
 <span data-ttu-id="82604-143">由於 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]不會指定觸發程序事件，您決定哪些必要/選用的規則，或應該是選用性。</span><span class="sxs-lookup"><span data-stu-id="82604-143">Since Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] does not specify trigger events, you decide what the required/optional rules, or optionality should be.</span></span> <span data-ttu-id="82604-144">根據本機站台的條件，您可能決定強制執行選擇性的規則。</span><span class="sxs-lookup"><span data-stu-id="82604-144">Based on local site conditions, you may decide to enforce optionality rules.</span></span> <span data-ttu-id="82604-145">根據預設，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]提供 23 欄位列為"X"做為選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="82604-145">By default, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] provides the 23 fields listed as "X" as optional fields.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82604-146">值"Y"是中的錯誤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="82604-146">Value "Y" is an error in the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Access database.</span></span> [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]<span data-ttu-id="82604-147"> 假設所有的值**Y**並**空白**是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="82604-147"> assumes that all the values of **Y** and **Blank** are optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82604-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82604-148">See Also</span></span>  
 [<span data-ttu-id="82604-149">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="82604-149">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)