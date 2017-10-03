---
title: "HL7 2.3 資料夾和事件 |Microsoft 文件"
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
ms.assetid: 555a8620-a714-4102-80ba-1424d60387bf
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a396fca582defb8601bdda23280f92d0acbd90be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-23-folders-and-events"></a><span data-ttu-id="3d841-102">HL7 2.3 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="3d841-102">HL7 2.3 Folders and Events</span></span>
<span data-ttu-id="3d841-103">下表列出 HL7 編碼訊息的 HL7 版本 2.3 資料夾內的安裝程式精靈所建立的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="3d841-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.3 folder for HL7-encoded messages.</span></span> <span data-ttu-id="3d841-104">這些子資料夾包含使用的結構描述[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 來驗證、 剖析和序列化此資料表的事件資料行中列出的事件。</span><span class="sxs-lookup"><span data-stu-id="3d841-104">These subfolders contain the schemas used by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="3d841-105">子資料夾名稱會描述這些結構描述支援的事件類型。</span><span class="sxs-lookup"><span data-stu-id="3d841-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="3d841-106">子資料夾</span><span class="sxs-lookup"><span data-stu-id="3d841-106">Subfolder</span></span>|<span data-ttu-id="3d841-107">事件</span><span class="sxs-lookup"><span data-stu-id="3d841-107">Events</span></span>|  
|---------------|------------|  
|<span data-ttu-id="3d841-108">病患的系統管理</span><span class="sxs-lookup"><span data-stu-id="3d841-108">Patient Administration</span></span>|<span data-ttu-id="3d841-109">A01 A51</span><span class="sxs-lookup"><span data-stu-id="3d841-109">A01-A51</span></span>|  
|<span data-ttu-id="3d841-110">觀察報告</span><span class="sxs-lookup"><span data-stu-id="3d841-110">Observation Reporting</span></span>|<span data-ttu-id="3d841-111">C01 C12，P07 P09，R01 R06，W01 W02</span><span class="sxs-lookup"><span data-stu-id="3d841-111">C01-C12, P07-P09, R01-R06, W01-W02</span></span>|  
|<span data-ttu-id="3d841-112">病患的轉介</span><span class="sxs-lookup"><span data-stu-id="3d841-112">Patient Referral</span></span>|<span data-ttu-id="3d841-113">I01 I15</span><span class="sxs-lookup"><span data-stu-id="3d841-113">I01-I15</span></span>|  
|<span data-ttu-id="3d841-114">主要檔案</span><span class="sxs-lookup"><span data-stu-id="3d841-114">Master File</span></span>|<span data-ttu-id="3d841-115">M01 M11</span><span class="sxs-lookup"><span data-stu-id="3d841-115">M01-M11</span></span>|  
|<span data-ttu-id="3d841-116">訂單項目</span><span class="sxs-lookup"><span data-stu-id="3d841-116">Order Entry</span></span>|<span data-ttu-id="3d841-117">O01 O02、 Q06、 RAR、 RDR、 RER、 RGR、 ROR、 V01 V04</span><span class="sxs-lookup"><span data-stu-id="3d841-117">O01-O02,Q06, RAR,RDR,RER,RGR,ROR, V01-V04</span></span>|  
|<span data-ttu-id="3d841-118">財務管理</span><span class="sxs-lookup"><span data-stu-id="3d841-118">Financial Management</span></span>|<span data-ttu-id="3d841-119">P01 P06</span><span class="sxs-lookup"><span data-stu-id="3d841-119">P01-P06</span></span>|  
|<span data-ttu-id="3d841-120">病患照護</span><span class="sxs-lookup"><span data-stu-id="3d841-120">Patient Care</span></span>|<span data-ttu-id="3d841-121">PC1-PCJ PCL PCH</span><span class="sxs-lookup"><span data-stu-id="3d841-121">PC1-PCH, PCJ-PCL</span></span>|  
|<span data-ttu-id="3d841-122">查詢</span><span class="sxs-lookup"><span data-stu-id="3d841-122">Query</span></span>|<span data-ttu-id="3d841-123">CNQ，Q01 Q03，Q05</span><span class="sxs-lookup"><span data-stu-id="3d841-123">CNQ, Q01-Q03, Q05</span></span>|  
|<span data-ttu-id="3d841-124">排程</span><span class="sxs-lookup"><span data-stu-id="3d841-124">Scheduling</span></span>|<span data-ttu-id="3d841-125">S01 S26</span><span class="sxs-lookup"><span data-stu-id="3d841-125">S01-S26</span></span>|  
|<span data-ttu-id="3d841-126">醫療記錄與資訊管理</span><span class="sxs-lookup"><span data-stu-id="3d841-126">Medical Records and Information Management</span></span>|<span data-ttu-id="3d841-127">T01 T12</span><span class="sxs-lookup"><span data-stu-id="3d841-127">T01-T12</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d841-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d841-128">See Also</span></span>  
 <span data-ttu-id="3d841-129">[HL7 2.X 子資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="3d841-129">[HL7 2.X Subfolders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span></span>  
 <span data-ttu-id="3d841-130">[HL7 2.1 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="3d841-130">[HL7 2.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="3d841-131">[HL7 2.2 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="3d841-131">[HL7 2.2 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span></span>  
 <span data-ttu-id="3d841-132">[HL7 2.3.1 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="3d841-132">[HL7 2.3.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="3d841-133">[HL7 2.4 資料夾和事件](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="3d841-133">[HL7 2.4 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span></span>  
 [<span data-ttu-id="3d841-134">HL7 2.5 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="3d841-134">HL7 2.5 Folders and Events</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-5-folders-and-events.md)