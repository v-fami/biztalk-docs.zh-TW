---
title: HL7 2.5 資料夾和事件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 662ef767-5504-4ff5-8820-994e9cf674ea
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66bcd4c6dd5acbe8a6d2f649e387da8177c9618c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992799"
---
# <a name="hl7-25-folders-and-events"></a><span data-ttu-id="ed042-102">HL7 2.5 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="ed042-102">HL7 2.5 Folders and Events</span></span>
<span data-ttu-id="ed042-103">下表列出安裝精靈，HL7 編碼訊息的 HL7 2.5 版資料夾內建立子資料夾。</span><span class="sxs-lookup"><span data-stu-id="ed042-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.5 folder for HL7-encoded messages.</span></span> <span data-ttu-id="ed042-104">這些子資料夾包含由 Microsoft BizTalk Accelerator for HL7 結構描述 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 來驗證、 剖析和序列化此資料表的事件資料行中列出的事件。</span><span class="sxs-lookup"><span data-stu-id="ed042-104">These subfolders contain the schemas used by Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="ed042-105">子資料夾名稱描述兩個結構描述支援的事件的類型。</span><span class="sxs-lookup"><span data-stu-id="ed042-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="ed042-106">子資料夾</span><span class="sxs-lookup"><span data-stu-id="ed042-106">Subfolder</span></span>|<span data-ttu-id="ed042-107">事件</span><span class="sxs-lookup"><span data-stu-id="ed042-107">Events</span></span>|  
|---------------|------------|  
|<span data-ttu-id="ed042-108">病患的系統管理</span><span class="sxs-lookup"><span data-stu-id="ed042-108">Patient Administration</span></span>|<span data-ttu-id="ed042-109">管理 A01-K21-K24 A62 Q21 Q24</span><span class="sxs-lookup"><span data-stu-id="ed042-109">A01-A62,K21-K24,Q21-Q24</span></span>|  
|<span data-ttu-id="ed042-110">人員管理</span><span class="sxs-lookup"><span data-stu-id="ed042-110">Personnel Management</span></span>|<span data-ttu-id="ed042-111">版本 B01-K25，B08 Q25</span><span class="sxs-lookup"><span data-stu-id="ed042-111">B01-B08,K25,Q25</span></span>|  
|<span data-ttu-id="ed042-112">觀察報告</span><span class="sxs-lookup"><span data-stu-id="ed042-112">Observation Reporting</span></span>|<span data-ttu-id="ed042-113">C01-C12,P07-P09,R01-R02,R04,R21-R24,R30-R32</span><span class="sxs-lookup"><span data-stu-id="ed042-113">C01-C12,P07-P09,R01-R02,R04,R21-R24,R30-R32</span></span>|  
|<span data-ttu-id="ed042-114">病患的轉介</span><span class="sxs-lookup"><span data-stu-id="ed042-114">Patient Referral</span></span>|<span data-ttu-id="ed042-115">I01 I15</span><span class="sxs-lookup"><span data-stu-id="ed042-115">I01-I15</span></span>|  
|<span data-ttu-id="ed042-116">查詢</span><span class="sxs-lookup"><span data-stu-id="ed042-116">Query</span></span>|<span data-ttu-id="ed042-117">J01、 J02、 K11、 K13、 K15、 Q01 Q05、 Q07 Q09、 Q11、 Q13、 Q15 Q17、 R07 R09、 Z75 Z99</span><span class="sxs-lookup"><span data-stu-id="ed042-117">J01,J02,K11,K13,K15, Q01-Q05, Q07-Q09,Q11,Q13,Q15-Q17, R07-R09,Z75-Z99</span></span>|  
|<span data-ttu-id="ed042-118">主版檔案</span><span class="sxs-lookup"><span data-stu-id="ed042-118">Master Files</span></span>|<span data-ttu-id="ed042-119">M01 M12</span><span class="sxs-lookup"><span data-stu-id="ed042-119">M01-M12</span></span>|  
|<span data-ttu-id="ed042-120">訂單項目</span><span class="sxs-lookup"><span data-stu-id="ed042-120">Order Entry</span></span>|<span data-ttu-id="ed042-121">O01 O36、 Q06、 Q26 Q31、 RAR、 RDR、 RER、 RGR、 ROR、 V01 V04、 Z73 Z74</span><span class="sxs-lookup"><span data-stu-id="ed042-121">O01-O36,Q06,Q26-Q31,RAR,RDR,RER,RGR,ROR,V01-V04,Z73-Z74</span></span>|  
|<span data-ttu-id="ed042-122">應用程式管理</span><span class="sxs-lookup"><span data-stu-id="ed042-122">Application Management</span></span>|<span data-ttu-id="ed042-123">N01 N02</span><span class="sxs-lookup"><span data-stu-id="ed042-123">N01-N02</span></span>|  
|<span data-ttu-id="ed042-124">財務管理</span><span class="sxs-lookup"><span data-stu-id="ed042-124">Financial Management</span></span>|<span data-ttu-id="ed042-125">P01 P03、 P05-06、 P10 P12</span><span class="sxs-lookup"><span data-stu-id="ed042-125">P01-P03,P05-06,P10-P12</span></span>|  
|<span data-ttu-id="ed042-126">病患照護</span><span class="sxs-lookup"><span data-stu-id="ed042-126">Patient Care</span></span>|<span data-ttu-id="ed042-127">PC1 PC9，PCA PCH，PCJ PCL</span><span class="sxs-lookup"><span data-stu-id="ed042-127">PC1-PC9,PCA-PCH,PCJ,PCL</span></span>|  
|<span data-ttu-id="ed042-128">排程</span><span class="sxs-lookup"><span data-stu-id="ed042-128">Scheduling</span></span>|<span data-ttu-id="ed042-129">S01 S26</span><span class="sxs-lookup"><span data-stu-id="ed042-129">S01-S26</span></span>|  
|<span data-ttu-id="ed042-130">醫療記錄/資訊管理</span><span class="sxs-lookup"><span data-stu-id="ed042-130">Medical Records/Information Management</span></span>|<span data-ttu-id="ed042-131">T01 T12</span><span class="sxs-lookup"><span data-stu-id="ed042-131">T01-T12</span></span>|  
|<span data-ttu-id="ed042-132">臨床實驗室自動化</span><span class="sxs-lookup"><span data-stu-id="ed042-132">Clinical Laboratory Automation</span></span>|<span data-ttu-id="ed042-133">U01 U13</span><span class="sxs-lookup"><span data-stu-id="ed042-133">U01-U13</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed042-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed042-134">See Also</span></span>  
 <span data-ttu-id="ed042-135">[HL7 2.X 子資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="ed042-135">[HL7 2.X Subfolders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span></span>  
 <span data-ttu-id="ed042-136">[HL7 2.1 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="ed042-136">[HL7 2.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="ed042-137">[HL7 2.2 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="ed042-137">[HL7 2.2 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span></span>  
 <span data-ttu-id="ed042-138">[HL7 2.3 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="ed042-138">[HL7 2.3 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span></span>  
 <span data-ttu-id="ed042-139">[HL7 2.3.1 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="ed042-139">[HL7 2.3.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="ed042-140">[HL7 2.4 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="ed042-140">[HL7 2.4 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span></span>  
 [<span data-ttu-id="ed042-141">HL7 2.5 資料夾和事件&#91;hl7&#93;</span><span class="sxs-lookup"><span data-stu-id="ed042-141">HL7 2.5 Folders and Events &#91;hl7&#93;</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-5-folders-and-events.md)