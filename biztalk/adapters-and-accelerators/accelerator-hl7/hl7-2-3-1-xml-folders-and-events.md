---
title: "HL7 2.3.1 XML 資料夾和事件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events, HL7 2.XML versions
- HL7, default sub-folders
- HL7, events
ms.assetid: b3598cc5-46d6-489a-84a7-266ee3c40276
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79b25e0563f404d0f8b0600829398729a6c80e65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-231-xml-folders-and-events"></a><span data-ttu-id="43870-102">HL7 2.3.1 XML 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="43870-102">HL7 2.3.1 XML Folders and Events</span></span>
<span data-ttu-id="43870-103">下表列出安裝精靈的 XML 編碼訊息的 HL7 版本 2.3.1 資料夾內所建立的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="43870-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.3.1 folder for XML-encoded messages.</span></span> <span data-ttu-id="43870-104">這些子資料夾包含使用的結構描述[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 來驗證、 剖析和序列化此資料表的事件資料行中列出的事件。</span><span class="sxs-lookup"><span data-stu-id="43870-104">These subfolders contain the schemas used by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="43870-105">子資料夾名稱會描述這些結構描述支援的事件類型。</span><span class="sxs-lookup"><span data-stu-id="43870-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="43870-106">子資料夾</span><span class="sxs-lookup"><span data-stu-id="43870-106">Subfolder</span></span>|<span data-ttu-id="43870-107">事件</span><span class="sxs-lookup"><span data-stu-id="43870-107">Events</span></span>|  
|---------------|------------|  
|<span data-ttu-id="43870-108">病患的系統管理</span><span class="sxs-lookup"><span data-stu-id="43870-108">Patient Administration</span></span>|<span data-ttu-id="43870-109">A01 A51</span><span class="sxs-lookup"><span data-stu-id="43870-109">A01-A51</span></span>|  
|<span data-ttu-id="43870-110">訂單項目</span><span class="sxs-lookup"><span data-stu-id="43870-110">Order Entry</span></span>|<span data-ttu-id="43870-111">O01、 O02、 Q06、 R0R、 RAR、 RDR、 RER、 RGR、 V01 V04</span><span class="sxs-lookup"><span data-stu-id="43870-111">O01,O02,Q06,R0R,RAR,RDR,RER,RGR, V01-V04</span></span>|  
|<span data-ttu-id="43870-112">查詢</span><span class="sxs-lookup"><span data-stu-id="43870-112">Query</span></span>|<span data-ttu-id="43870-113">CNQ，Q01 Q03，Q05，Q07 Q09，R07，R08，R09</span><span class="sxs-lookup"><span data-stu-id="43870-113">CNQ, Q01-Q03, Q05, Q07-Q09, R07,R08,R09</span></span>|  
|<span data-ttu-id="43870-114">財務管理</span><span class="sxs-lookup"><span data-stu-id="43870-114">Financial Management</span></span>|<span data-ttu-id="43870-115">P01 P06</span><span class="sxs-lookup"><span data-stu-id="43870-115">P01-P06</span></span>|  
|<span data-ttu-id="43870-116">觀察報告</span><span class="sxs-lookup"><span data-stu-id="43870-116">Observation Reporting</span></span>|<span data-ttu-id="43870-117">C01 C12、 P06、 P07、 P09、 R01 R06 W01、 W02</span><span class="sxs-lookup"><span data-stu-id="43870-117">C01-C12,P06,P07,P09,R01-R06, W01,W02</span></span>|  
|<span data-ttu-id="43870-118">主版檔案</span><span class="sxs-lookup"><span data-stu-id="43870-118">Master Files</span></span>|<span data-ttu-id="43870-119">M01 M11 MFA</span><span class="sxs-lookup"><span data-stu-id="43870-119">M01-M11, MFA</span></span>|  
|<span data-ttu-id="43870-120">醫療的記錄資訊管理</span><span class="sxs-lookup"><span data-stu-id="43870-120">Medical Records/Information Management</span></span>|<span data-ttu-id="43870-121">T01 T12</span><span class="sxs-lookup"><span data-stu-id="43870-121">T01-T12</span></span>|  
|<span data-ttu-id="43870-122">排程</span><span class="sxs-lookup"><span data-stu-id="43870-122">Schedule</span></span>|<span data-ttu-id="43870-123">S01 S26</span><span class="sxs-lookup"><span data-stu-id="43870-123">S01-S26</span></span>|  
|<span data-ttu-id="43870-124">病患的轉介</span><span class="sxs-lookup"><span data-stu-id="43870-124">Patient Referral</span></span>|<span data-ttu-id="43870-125">I01 I15</span><span class="sxs-lookup"><span data-stu-id="43870-125">I01-I15</span></span>|  
|<span data-ttu-id="43870-126">病患照護</span><span class="sxs-lookup"><span data-stu-id="43870-126">Patient Care</span></span>|<span data-ttu-id="43870-127">PC1-PCJ，PCK，PCL PCH</span><span class="sxs-lookup"><span data-stu-id="43870-127">PC1-PCH, PCJ,PCK,PCL</span></span>|  
|<span data-ttu-id="43870-128">網路管理</span><span class="sxs-lookup"><span data-stu-id="43870-128">Network Management</span></span>|<span data-ttu-id="43870-129">N01 N02</span><span class="sxs-lookup"><span data-stu-id="43870-129">N01,N02</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43870-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43870-130">See Also</span></span>  
 [<span data-ttu-id="43870-131">使用 HL7 2.XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="43870-131">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)