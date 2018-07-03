---
title: HL7 2.4 資料夾和事件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HL7, default sub-folders
- events, 2.X versions
- HL7, events
ms.assetid: c8855311-40c7-4338-ba07-5112c253fafd
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62747b5f1669026b3b1eaf7b2f48f87242947890
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992354"
---
# <a name="hl7-24-folders-and-events"></a><span data-ttu-id="f3a14-102">HL7 2.4 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="f3a14-102">HL7 2.4 Folders and Events</span></span>
<span data-ttu-id="f3a14-103">下表列出安裝精靈，HL7 編碼訊息的 HL7 2.4 版資料夾內建立子資料夾。</span><span class="sxs-lookup"><span data-stu-id="f3a14-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.4 folder for HL7-encoded messages.</span></span> <span data-ttu-id="f3a14-104">這些子資料夾包含由 Microsoft BizTalk Accelerator for HL7 結構描述 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 來驗證、 剖析和序列化此資料表的事件資料行中列出的事件。</span><span class="sxs-lookup"><span data-stu-id="f3a14-104">These subfolders contain the schemas used by Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="f3a14-105">子資料夾名稱描述兩個結構描述支援的事件的類型。</span><span class="sxs-lookup"><span data-stu-id="f3a14-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="f3a14-106">子資料夾</span><span class="sxs-lookup"><span data-stu-id="f3a14-106">Subfolder</span></span>|<span data-ttu-id="f3a14-107">事件</span><span class="sxs-lookup"><span data-stu-id="f3a14-107">Events</span></span>|  
|---------------|------------|  
|<span data-ttu-id="f3a14-108">病患的系統管理</span><span class="sxs-lookup"><span data-stu-id="f3a14-108">Patient Administration</span></span>|<span data-ttu-id="f3a14-109">管理 A01-K21-K24 A62 Q21 Q24</span><span class="sxs-lookup"><span data-stu-id="f3a14-109">A01-A62, K21-K24,Q21-Q24</span></span>|  
|<span data-ttu-id="f3a14-110">人員管理</span><span class="sxs-lookup"><span data-stu-id="f3a14-110">Personnel Management</span></span>|<span data-ttu-id="f3a14-111">版本 B01-K25，B06 Q25</span><span class="sxs-lookup"><span data-stu-id="f3a14-111">B01-B06, K25,Q25</span></span>|  
|<span data-ttu-id="f3a14-112">觀察報告</span><span class="sxs-lookup"><span data-stu-id="f3a14-112">Observation Reporting</span></span>|<span data-ttu-id="f3a14-113">C01-P07-P09 C12 R01-R04，R02 R21 W01 W02</span><span class="sxs-lookup"><span data-stu-id="f3a14-113">C01-C12, P07-P09, R01-R02,R04, R21, W01-W02</span></span>|  
|<span data-ttu-id="f3a14-114">病患的轉介</span><span class="sxs-lookup"><span data-stu-id="f3a14-114">Patient Referral</span></span>|<span data-ttu-id="f3a14-115">I01 I15</span><span class="sxs-lookup"><span data-stu-id="f3a14-115">I01-I15</span></span>|  
|<span data-ttu-id="f3a14-116">查詢</span><span class="sxs-lookup"><span data-stu-id="f3a14-116">Query</span></span>|<span data-ttu-id="f3a14-117">J01、 J02、 K11、 K13、 K15、 Q01 Q05、 Q07 Q09、 Q11、 Q13、 Q15 Q17、 R07 R09、 Z75 Z99</span><span class="sxs-lookup"><span data-stu-id="f3a14-117">J01,J02,K11,K13,K15,  Q01-Q05, Q07-Q09, Q11,Q13,Q15-Q17, R07-R09, Z75-Z99</span></span>|  
|<span data-ttu-id="f3a14-118">主版檔案</span><span class="sxs-lookup"><span data-stu-id="f3a14-118">Master Files</span></span>|<span data-ttu-id="f3a14-119">M01 M12 MFA</span><span class="sxs-lookup"><span data-stu-id="f3a14-119">M01-M12, MFA</span></span>|  
|<span data-ttu-id="f3a14-120">訂單項目</span><span class="sxs-lookup"><span data-stu-id="f3a14-120">Order Entry</span></span>|<span data-ttu-id="f3a14-121">O01 O22、 Q06、 Q26 Q30、 RAR、 RDR、 RER、 RGR、 ROR、 V01 V04、 Z73 Z74</span><span class="sxs-lookup"><span data-stu-id="f3a14-121">O01-O22, Q06, Q26-Q30, RAR,RDR,RER,RGR,ROR, V01-V04, Z73- Z74</span></span>|  
|<span data-ttu-id="f3a14-122">應用程式管理</span><span class="sxs-lookup"><span data-stu-id="f3a14-122">Application Management</span></span>|<span data-ttu-id="f3a14-123">N01 N02</span><span class="sxs-lookup"><span data-stu-id="f3a14-123">N01-N02</span></span>|  
|<span data-ttu-id="f3a14-124">財務管理</span><span class="sxs-lookup"><span data-stu-id="f3a14-124">Financial Management</span></span>|<span data-ttu-id="f3a14-125">P01 P06 P10</span><span class="sxs-lookup"><span data-stu-id="f3a14-125">P01-P06, P10</span></span>|  
|<span data-ttu-id="f3a14-126">病患照護</span><span class="sxs-lookup"><span data-stu-id="f3a14-126">Patient Care</span></span>|<span data-ttu-id="f3a14-127">PC1 PCH，PCJ PCL</span><span class="sxs-lookup"><span data-stu-id="f3a14-127">PC1-PCH, PCJ-PCL</span></span>|  
|<span data-ttu-id="f3a14-128">排程</span><span class="sxs-lookup"><span data-stu-id="f3a14-128">Scheduling</span></span>|<span data-ttu-id="f3a14-129">S01 S26</span><span class="sxs-lookup"><span data-stu-id="f3a14-129">S01-S26</span></span>|  
|<span data-ttu-id="f3a14-130">醫療記錄/資訊管理</span><span class="sxs-lookup"><span data-stu-id="f3a14-130">Medical Records/Information Management</span></span>|<span data-ttu-id="f3a14-131">T01 T12</span><span class="sxs-lookup"><span data-stu-id="f3a14-131">T01-T12</span></span>|  
|<span data-ttu-id="f3a14-132">臨床實驗室自動化</span><span class="sxs-lookup"><span data-stu-id="f3a14-132">Clinical Laboratory Automation</span></span>|<span data-ttu-id="f3a14-133">U01 U13</span><span class="sxs-lookup"><span data-stu-id="f3a14-133">U01-U13</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3a14-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3a14-134">See Also</span></span>  
 <span data-ttu-id="f3a14-135">[HL7 2.X 子資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="f3a14-135">[HL7 2.X Subfolders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span></span>  
 <span data-ttu-id="f3a14-136">[HL7 2.1 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="f3a14-136">[HL7 2.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="f3a14-137">[HL7 2.2 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="f3a14-137">[HL7 2.2 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span></span>  
 <span data-ttu-id="f3a14-138">[HL7 2.3 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="f3a14-138">[HL7 2.3 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span></span>  
 <span data-ttu-id="f3a14-139">[HL7 2.3.1 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="f3a14-139">[HL7 2.3.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span></span>  
 [<span data-ttu-id="f3a14-140">HL7 2.5 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="f3a14-140">HL7 2.5 Folders and Events</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-5-folders-and-events.md)