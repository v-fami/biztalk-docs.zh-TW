---
title: HL7 2.5 資料夾和事件 |Microsoft 文件
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
ms.openlocfilehash: cdb229e2f8adf58397babf637a696bc2437ab626
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204958"
---
# <a name="hl7-25-folders-and-events"></a><span data-ttu-id="dd79e-102">HL7 2.5 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="dd79e-102">HL7 2.5 Folders and Events</span></span>
<span data-ttu-id="dd79e-103">下表列出 HL7 編碼訊息的 HL7 2.5 版資料夾內的安裝程式精靈所建立的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd79e-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.5 folder for HL7-encoded messages.</span></span> <span data-ttu-id="dd79e-104">這些子資料夾包含使用的結構描述[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 來驗證、 剖析和序列化此資料表的事件資料行中列出的事件。</span><span class="sxs-lookup"><span data-stu-id="dd79e-104">These subfolders contain the schemas used by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="dd79e-105">子資料夾名稱會描述這些結構描述支援的事件類型。</span><span class="sxs-lookup"><span data-stu-id="dd79e-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="dd79e-106">子資料夾</span><span class="sxs-lookup"><span data-stu-id="dd79e-106">Subfolder</span></span>|<span data-ttu-id="dd79e-107">事件</span><span class="sxs-lookup"><span data-stu-id="dd79e-107">Events</span></span>|  
|---------------|------------|  
|<span data-ttu-id="dd79e-108">病患的系統管理</span><span class="sxs-lookup"><span data-stu-id="dd79e-108">Patient Administration</span></span>|<span data-ttu-id="dd79e-109">A01 A62，K21 K24，Q21 Q24</span><span class="sxs-lookup"><span data-stu-id="dd79e-109">A01-A62,K21-K24,Q21-Q24</span></span>|  
|<span data-ttu-id="dd79e-110">人員管理</span><span class="sxs-lookup"><span data-stu-id="dd79e-110">Personnel Management</span></span>|<span data-ttu-id="dd79e-111">B01 B08，K25，Q25</span><span class="sxs-lookup"><span data-stu-id="dd79e-111">B01-B08,K25,Q25</span></span>|  
|<span data-ttu-id="dd79e-112">觀察報告</span><span class="sxs-lookup"><span data-stu-id="dd79e-112">Observation Reporting</span></span>|<span data-ttu-id="dd79e-113">C01-C12,P07-P09,R01-R02,R04,R21-R24,R30-R32</span><span class="sxs-lookup"><span data-stu-id="dd79e-113">C01-C12,P07-P09,R01-R02,R04,R21-R24,R30-R32</span></span>|  
|<span data-ttu-id="dd79e-114">病患的轉介</span><span class="sxs-lookup"><span data-stu-id="dd79e-114">Patient Referral</span></span>|<span data-ttu-id="dd79e-115">I01 I15</span><span class="sxs-lookup"><span data-stu-id="dd79e-115">I01-I15</span></span>|  
|<span data-ttu-id="dd79e-116">查詢</span><span class="sxs-lookup"><span data-stu-id="dd79e-116">Query</span></span>|<span data-ttu-id="dd79e-117">J01、 J02、 K11、 K13、 K15、 Q01 Q05、 Q07 Q09、 Q11、 Q13、 Q15 Q17、 R07 R09、 Z75 Z99</span><span class="sxs-lookup"><span data-stu-id="dd79e-117">J01,J02,K11,K13,K15, Q01-Q05, Q07-Q09,Q11,Q13,Q15-Q17, R07-R09,Z75-Z99</span></span>|  
|<span data-ttu-id="dd79e-118">主版檔案</span><span class="sxs-lookup"><span data-stu-id="dd79e-118">Master Files</span></span>|<span data-ttu-id="dd79e-119">M01 M12</span><span class="sxs-lookup"><span data-stu-id="dd79e-119">M01-M12</span></span>|  
|<span data-ttu-id="dd79e-120">訂單項目</span><span class="sxs-lookup"><span data-stu-id="dd79e-120">Order Entry</span></span>|<span data-ttu-id="dd79e-121">O01 O36、 Q06、 Q26 Q31、 RAR、 RDR、 RER、 RGR、 ROR、 V01 V04、 Z73 Z74</span><span class="sxs-lookup"><span data-stu-id="dd79e-121">O01-O36,Q06,Q26-Q31,RAR,RDR,RER,RGR,ROR,V01-V04,Z73-Z74</span></span>|  
|<span data-ttu-id="dd79e-122">應用程式管理</span><span class="sxs-lookup"><span data-stu-id="dd79e-122">Application Management</span></span>|<span data-ttu-id="dd79e-123">N01 N02</span><span class="sxs-lookup"><span data-stu-id="dd79e-123">N01-N02</span></span>|  
|<span data-ttu-id="dd79e-124">財務管理</span><span class="sxs-lookup"><span data-stu-id="dd79e-124">Financial Management</span></span>|<span data-ttu-id="dd79e-125">P01 P03、 P05-06、 P10 P12</span><span class="sxs-lookup"><span data-stu-id="dd79e-125">P01-P03,P05-06,P10-P12</span></span>|  
|<span data-ttu-id="dd79e-126">病患照護</span><span class="sxs-lookup"><span data-stu-id="dd79e-126">Patient Care</span></span>|<span data-ttu-id="dd79e-127">PC1 PC9，PCA PCH，PCJ PCL</span><span class="sxs-lookup"><span data-stu-id="dd79e-127">PC1-PC9,PCA-PCH,PCJ,PCL</span></span>|  
|<span data-ttu-id="dd79e-128">排程</span><span class="sxs-lookup"><span data-stu-id="dd79e-128">Scheduling</span></span>|<span data-ttu-id="dd79e-129">S01 S26</span><span class="sxs-lookup"><span data-stu-id="dd79e-129">S01-S26</span></span>|  
|<span data-ttu-id="dd79e-130">醫療的記錄資訊管理</span><span class="sxs-lookup"><span data-stu-id="dd79e-130">Medical Records/Information Management</span></span>|<span data-ttu-id="dd79e-131">T01 T12</span><span class="sxs-lookup"><span data-stu-id="dd79e-131">T01-T12</span></span>|  
|<span data-ttu-id="dd79e-132">臨床實驗室自動化</span><span class="sxs-lookup"><span data-stu-id="dd79e-132">Clinical Laboratory Automation</span></span>|<span data-ttu-id="dd79e-133">U01 U13</span><span class="sxs-lookup"><span data-stu-id="dd79e-133">U01-U13</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd79e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd79e-134">See Also</span></span>  
 <span data-ttu-id="dd79e-135">[HL7 2.X 子資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="dd79e-135">[HL7 2.X Subfolders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span></span>  
 <span data-ttu-id="dd79e-136">[HL7 2.1 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="dd79e-136">[HL7 2.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="dd79e-137">[HL7 2.2 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="dd79e-137">[HL7 2.2 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span></span>  
 <span data-ttu-id="dd79e-138">[HL7 2.3 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="dd79e-138">[HL7 2.3 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span></span>  
 <span data-ttu-id="dd79e-139">[HL7 2.3.1 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="dd79e-139">[HL7 2.3.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="dd79e-140">[HL7 2.4 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="dd79e-140">[HL7 2.4 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span></span>  
 [<span data-ttu-id="dd79e-141">HL7 2.5 資料夾和事件 &#91; hl7 &#93;</span><span class="sxs-lookup"><span data-stu-id="dd79e-141">HL7 2.5 Folders and Events &#91;hl7&#93;</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-5-folders-and-events.md)