---
title: "HL7 2.3.1 資料夾和事件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HL7, default sub-folders
- events, 2.X versions
- HL7, events
ms.assetid: 5cab1b7e-fdce-4b4b-bbd6-1da67fcf6a74
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad51a024348c12c4097af29419698ced7c9c0c85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-231-folders-and-events"></a><span data-ttu-id="65589-102">HL7 2.3.1 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="65589-102">HL7 2.3.1 Folders and Events</span></span>
<span data-ttu-id="65589-103">下表列出 HL7 編碼訊息的 HL7 版本 2.3.1 資料夾內的安裝程式精靈所建立的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="65589-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.3.1 folder for HL7-encoded messages.</span></span> <span data-ttu-id="65589-104">這些子資料夾包含使用的結構描述[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 來驗證、 剖析和序列化此資料表的事件資料行中列出的事件。</span><span class="sxs-lookup"><span data-stu-id="65589-104">These subfolders contain the schemas used by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="65589-105">子資料夾名稱會描述這些結構描述支援的事件類型。</span><span class="sxs-lookup"><span data-stu-id="65589-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="65589-106">子資料夾</span><span class="sxs-lookup"><span data-stu-id="65589-106">Subfolder</span></span>|<span data-ttu-id="65589-107">事件</span><span class="sxs-lookup"><span data-stu-id="65589-107">Events</span></span>|  
|---------------|------------|  
|<span data-ttu-id="65589-108">病患的系統管理</span><span class="sxs-lookup"><span data-stu-id="65589-108">Patient Administration</span></span>|<span data-ttu-id="65589-109">A01 A51</span><span class="sxs-lookup"><span data-stu-id="65589-109">A01-A51</span></span>|  
|<span data-ttu-id="65589-110">觀察報告</span><span class="sxs-lookup"><span data-stu-id="65589-110">Observation Reporting</span></span>|<span data-ttu-id="65589-111">C01 C12，P06 P09，R01 R06，W01 W02</span><span class="sxs-lookup"><span data-stu-id="65589-111">C01-C12,P06-P09,R01-R06, W01-W02</span></span>|  
|<span data-ttu-id="65589-112">病患的轉介</span><span class="sxs-lookup"><span data-stu-id="65589-112">Patient Referral</span></span>|<span data-ttu-id="65589-113">I01 I15</span><span class="sxs-lookup"><span data-stu-id="65589-113">I01-I15</span></span>|  
|<span data-ttu-id="65589-114">主版檔案</span><span class="sxs-lookup"><span data-stu-id="65589-114">Master Files</span></span>|<span data-ttu-id="65589-115">M01 M11 MFA</span><span class="sxs-lookup"><span data-stu-id="65589-115">M01-M11, MFA</span></span>|  
|<span data-ttu-id="65589-116">訂單項目</span><span class="sxs-lookup"><span data-stu-id="65589-116">Order Entry</span></span>|<span data-ttu-id="65589-117">O01 O02、 Q06、 R0R、 RAR、 RDR、 RER、 RGR、 V01 V04</span><span class="sxs-lookup"><span data-stu-id="65589-117">O01-O02,Q06,R0R,RAR,RDR,RER,RGR, V01-V04</span></span>|  
|<span data-ttu-id="65589-118">財務管理</span><span class="sxs-lookup"><span data-stu-id="65589-118">Financial Management</span></span>|<span data-ttu-id="65589-119">P01 P06</span><span class="sxs-lookup"><span data-stu-id="65589-119">P01-P06</span></span>|  
|<span data-ttu-id="65589-120">病患照護</span><span class="sxs-lookup"><span data-stu-id="65589-120">Patient Care</span></span>|<span data-ttu-id="65589-121">PC1-PCJ PCL PCH</span><span class="sxs-lookup"><span data-stu-id="65589-121">PC1-PCH, PCJ-PCL</span></span>|  
|<span data-ttu-id="65589-122">查詢</span><span class="sxs-lookup"><span data-stu-id="65589-122">Query</span></span>|<span data-ttu-id="65589-123">CNQ，Q01 Q05，Q07 Q09，R07 R09</span><span class="sxs-lookup"><span data-stu-id="65589-123">CNQ, Q01-Q05, Q07-Q09, R07-R09</span></span>|  
|<span data-ttu-id="65589-124">排程</span><span class="sxs-lookup"><span data-stu-id="65589-124">Schedule</span></span>|<span data-ttu-id="65589-125">S01 S26</span><span class="sxs-lookup"><span data-stu-id="65589-125">S01-S26</span></span>|  
|<span data-ttu-id="65589-126">醫療的記錄資訊管理</span><span class="sxs-lookup"><span data-stu-id="65589-126">Medical Records/Information Management</span></span>|<span data-ttu-id="65589-127">T01 T12</span><span class="sxs-lookup"><span data-stu-id="65589-127">T01-T12</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65589-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65589-128">See Also</span></span>  
 <span data-ttu-id="65589-129">[HL7 2.X 子資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="65589-129">[HL7 2.X Subfolders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span></span>  
 <span data-ttu-id="65589-130">[HL7 2.1 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="65589-130">[HL7 2.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="65589-131">[HL7 2.2 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="65589-131">[HL7 2.2 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span></span>  
 <span data-ttu-id="65589-132">[HL7 2.3 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="65589-132">[HL7 2.3 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span></span>  
 <span data-ttu-id="65589-133">[HL7 2.4 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="65589-133">[HL7 2.4 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span></span>  
 [<span data-ttu-id="65589-134">HL7 2.5 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="65589-134">HL7 2.5 Folders and Events</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-5-folders-and-events.md)