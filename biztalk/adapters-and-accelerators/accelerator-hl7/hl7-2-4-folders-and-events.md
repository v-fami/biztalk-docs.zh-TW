---
title: HL7 2.4 資料夾和事件 |Microsoft 文件
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
ms.openlocfilehash: 9196b0b69eb3730de8ad3ef383a1cde8564e5002
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204774"
---
# <a name="hl7-24-folders-and-events"></a><span data-ttu-id="54c99-102">HL7 2.4 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="54c99-102">HL7 2.4 Folders and Events</span></span>
<span data-ttu-id="54c99-103">下表列出 HL7 編碼訊息的 HL7 2.4 版資料夾內的安裝程式精靈所建立的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="54c99-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.4 folder for HL7-encoded messages.</span></span> <span data-ttu-id="54c99-104">這些子資料夾包含使用的結構描述[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 來驗證、 剖析和序列化此資料表的事件資料行中列出的事件。</span><span class="sxs-lookup"><span data-stu-id="54c99-104">These subfolders contain the schemas used by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="54c99-105">子資料夾名稱會描述這些結構描述支援的事件類型。</span><span class="sxs-lookup"><span data-stu-id="54c99-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="54c99-106">子資料夾</span><span class="sxs-lookup"><span data-stu-id="54c99-106">Subfolder</span></span>|<span data-ttu-id="54c99-107">事件</span><span class="sxs-lookup"><span data-stu-id="54c99-107">Events</span></span>|  
|---------------|------------|  
|<span data-ttu-id="54c99-108">病患的系統管理</span><span class="sxs-lookup"><span data-stu-id="54c99-108">Patient Administration</span></span>|<span data-ttu-id="54c99-109">A01 A62，K21 K24，Q21 Q24</span><span class="sxs-lookup"><span data-stu-id="54c99-109">A01-A62, K21-K24,Q21-Q24</span></span>|  
|<span data-ttu-id="54c99-110">人員管理</span><span class="sxs-lookup"><span data-stu-id="54c99-110">Personnel Management</span></span>|<span data-ttu-id="54c99-111">B01 B06，K25，Q25</span><span class="sxs-lookup"><span data-stu-id="54c99-111">B01-B06, K25,Q25</span></span>|  
|<span data-ttu-id="54c99-112">觀察報告</span><span class="sxs-lookup"><span data-stu-id="54c99-112">Observation Reporting</span></span>|<span data-ttu-id="54c99-113">C01 C12，P07 P09，R01 R02，R04，R21 W01 W02</span><span class="sxs-lookup"><span data-stu-id="54c99-113">C01-C12, P07-P09, R01-R02,R04, R21, W01-W02</span></span>|  
|<span data-ttu-id="54c99-114">病患的轉介</span><span class="sxs-lookup"><span data-stu-id="54c99-114">Patient Referral</span></span>|<span data-ttu-id="54c99-115">I01 I15</span><span class="sxs-lookup"><span data-stu-id="54c99-115">I01-I15</span></span>|  
|<span data-ttu-id="54c99-116">查詢</span><span class="sxs-lookup"><span data-stu-id="54c99-116">Query</span></span>|<span data-ttu-id="54c99-117">J01、 J02、 K11、 K13、 K15、 Q01 Q05、 Q07 Q09、 Q11、 Q13、 Q15 Q17、 R07 R09、 Z75 Z99</span><span class="sxs-lookup"><span data-stu-id="54c99-117">J01,J02,K11,K13,K15,  Q01-Q05, Q07-Q09, Q11,Q13,Q15-Q17, R07-R09, Z75-Z99</span></span>|  
|<span data-ttu-id="54c99-118">主版檔案</span><span class="sxs-lookup"><span data-stu-id="54c99-118">Master Files</span></span>|<span data-ttu-id="54c99-119">M01 M12 MFA</span><span class="sxs-lookup"><span data-stu-id="54c99-119">M01-M12, MFA</span></span>|  
|<span data-ttu-id="54c99-120">訂單項目</span><span class="sxs-lookup"><span data-stu-id="54c99-120">Order Entry</span></span>|<span data-ttu-id="54c99-121">O01 O22、 Q06、 Q26 Q30、 RAR、 RDR、 RER、 RGR、 ROR、 V01 V04、 Z73 Z74</span><span class="sxs-lookup"><span data-stu-id="54c99-121">O01-O22, Q06, Q26-Q30, RAR,RDR,RER,RGR,ROR, V01-V04, Z73- Z74</span></span>|  
|<span data-ttu-id="54c99-122">應用程式管理</span><span class="sxs-lookup"><span data-stu-id="54c99-122">Application Management</span></span>|<span data-ttu-id="54c99-123">N01 N02</span><span class="sxs-lookup"><span data-stu-id="54c99-123">N01-N02</span></span>|  
|<span data-ttu-id="54c99-124">財務管理</span><span class="sxs-lookup"><span data-stu-id="54c99-124">Financial Management</span></span>|<span data-ttu-id="54c99-125">P01 P06 P10</span><span class="sxs-lookup"><span data-stu-id="54c99-125">P01-P06, P10</span></span>|  
|<span data-ttu-id="54c99-126">病患照護</span><span class="sxs-lookup"><span data-stu-id="54c99-126">Patient Care</span></span>|<span data-ttu-id="54c99-127">PC1-PCJ PCL PCH</span><span class="sxs-lookup"><span data-stu-id="54c99-127">PC1-PCH, PCJ-PCL</span></span>|  
|<span data-ttu-id="54c99-128">排程</span><span class="sxs-lookup"><span data-stu-id="54c99-128">Scheduling</span></span>|<span data-ttu-id="54c99-129">S01 S26</span><span class="sxs-lookup"><span data-stu-id="54c99-129">S01-S26</span></span>|  
|<span data-ttu-id="54c99-130">醫療的記錄資訊管理</span><span class="sxs-lookup"><span data-stu-id="54c99-130">Medical Records/Information Management</span></span>|<span data-ttu-id="54c99-131">T01 T12</span><span class="sxs-lookup"><span data-stu-id="54c99-131">T01-T12</span></span>|  
|<span data-ttu-id="54c99-132">臨床實驗室自動化</span><span class="sxs-lookup"><span data-stu-id="54c99-132">Clinical Laboratory Automation</span></span>|<span data-ttu-id="54c99-133">U01 U13</span><span class="sxs-lookup"><span data-stu-id="54c99-133">U01-U13</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54c99-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54c99-134">See Also</span></span>  
 <span data-ttu-id="54c99-135">[HL7 2.X 子資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="54c99-135">[HL7 2.X Subfolders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span></span>  
 <span data-ttu-id="54c99-136">[HL7 2.1 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="54c99-136">[HL7 2.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="54c99-137">[HL7 2.2 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="54c99-137">[HL7 2.2 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span></span>  
 <span data-ttu-id="54c99-138">[HL7 2.3 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="54c99-138">[HL7 2.3 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span></span>  
 <span data-ttu-id="54c99-139">[HL7 2.3.1 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="54c99-139">[HL7 2.3.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span></span>  
 [<span data-ttu-id="54c99-140">HL7 2.5 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="54c99-140">HL7 2.5 Folders and Events</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-5-folders-and-events.md)