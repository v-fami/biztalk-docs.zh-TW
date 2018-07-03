---
title: HL7 2.3.1 XML 資料夾和事件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- events, HL7 2.XML versions
- HL7, default sub-folders
- HL7, events
ms.assetid: b3598cc5-46d6-489a-84a7-266ee3c40276
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6bbe1d472f844d57c7770ec4ae425fc6aef44a20
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991727"
---
# <a name="hl7-231-xml-folders-and-events"></a><span data-ttu-id="2ecf3-102">HL7 2.3.1 XML 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="2ecf3-102">HL7 2.3.1 XML Folders and Events</span></span>
<span data-ttu-id="2ecf3-103">下表列出安裝精靈，XML 編碼訊息的 HL7 2.3.1 版資料夾內建立子資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ecf3-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.3.1 folder for XML-encoded messages.</span></span> <span data-ttu-id="2ecf3-104">這些子資料夾包含由 Microsoft BizTalk Accelerator for HL7 結構描述 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 來驗證、 剖析和序列化此資料表的事件資料行中列出的事件。</span><span class="sxs-lookup"><span data-stu-id="2ecf3-104">These subfolders contain the schemas used by Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="2ecf3-105">子資料夾名稱描述兩個結構描述支援的事件的類型。</span><span class="sxs-lookup"><span data-stu-id="2ecf3-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="2ecf3-106">子資料夾</span><span class="sxs-lookup"><span data-stu-id="2ecf3-106">Subfolder</span></span>|<span data-ttu-id="2ecf3-107">事件</span><span class="sxs-lookup"><span data-stu-id="2ecf3-107">Events</span></span>|  
|---------------|------------|  
|<span data-ttu-id="2ecf3-108">病患的系統管理</span><span class="sxs-lookup"><span data-stu-id="2ecf3-108">Patient Administration</span></span>|<span data-ttu-id="2ecf3-109">管理 A01 A51</span><span class="sxs-lookup"><span data-stu-id="2ecf3-109">A01-A51</span></span>|  
|<span data-ttu-id="2ecf3-110">訂單項目</span><span class="sxs-lookup"><span data-stu-id="2ecf3-110">Order Entry</span></span>|<span data-ttu-id="2ecf3-111">O01、 O02、 Q06、 R0R、 RAR、 RDR、 RER、 RGR、 V01 V04</span><span class="sxs-lookup"><span data-stu-id="2ecf3-111">O01,O02,Q06,R0R,RAR,RDR,RER,RGR, V01-V04</span></span>|  
|<span data-ttu-id="2ecf3-112">查詢</span><span class="sxs-lookup"><span data-stu-id="2ecf3-112">Query</span></span>|<span data-ttu-id="2ecf3-113">CNQ，Q01-Q03 Q05，Q07-Q09 R07，R08，R09</span><span class="sxs-lookup"><span data-stu-id="2ecf3-113">CNQ, Q01-Q03, Q05, Q07-Q09, R07,R08,R09</span></span>|  
|<span data-ttu-id="2ecf3-114">財務管理</span><span class="sxs-lookup"><span data-stu-id="2ecf3-114">Financial Management</span></span>|<span data-ttu-id="2ecf3-115">P01 P06</span><span class="sxs-lookup"><span data-stu-id="2ecf3-115">P01-P06</span></span>|  
|<span data-ttu-id="2ecf3-116">觀察報告</span><span class="sxs-lookup"><span data-stu-id="2ecf3-116">Observation Reporting</span></span>|<span data-ttu-id="2ecf3-117">C01 C12、 P06、 P07、 P09、 R01 如 R06、 W01、 W02</span><span class="sxs-lookup"><span data-stu-id="2ecf3-117">C01-C12,P06,P07,P09,R01-R06, W01,W02</span></span>|  
|<span data-ttu-id="2ecf3-118">主版檔案</span><span class="sxs-lookup"><span data-stu-id="2ecf3-118">Master Files</span></span>|<span data-ttu-id="2ecf3-119">M01 M11 MFA</span><span class="sxs-lookup"><span data-stu-id="2ecf3-119">M01-M11, MFA</span></span>|  
|<span data-ttu-id="2ecf3-120">醫療記錄/資訊管理</span><span class="sxs-lookup"><span data-stu-id="2ecf3-120">Medical Records/Information Management</span></span>|<span data-ttu-id="2ecf3-121">T01 T12</span><span class="sxs-lookup"><span data-stu-id="2ecf3-121">T01-T12</span></span>|  
|<span data-ttu-id="2ecf3-122">[排程]</span><span class="sxs-lookup"><span data-stu-id="2ecf3-122">Schedule</span></span>|<span data-ttu-id="2ecf3-123">S01 S26</span><span class="sxs-lookup"><span data-stu-id="2ecf3-123">S01-S26</span></span>|  
|<span data-ttu-id="2ecf3-124">病患的轉介</span><span class="sxs-lookup"><span data-stu-id="2ecf3-124">Patient Referral</span></span>|<span data-ttu-id="2ecf3-125">I01 I15</span><span class="sxs-lookup"><span data-stu-id="2ecf3-125">I01-I15</span></span>|  
|<span data-ttu-id="2ecf3-126">病患照護</span><span class="sxs-lookup"><span data-stu-id="2ecf3-126">Patient Care</span></span>|<span data-ttu-id="2ecf3-127">PC1 PCH，PCJ，PCK PCL</span><span class="sxs-lookup"><span data-stu-id="2ecf3-127">PC1-PCH, PCJ,PCK,PCL</span></span>|  
|<span data-ttu-id="2ecf3-128">網路管理</span><span class="sxs-lookup"><span data-stu-id="2ecf3-128">Network Management</span></span>|<span data-ttu-id="2ecf3-129">N01 N02</span><span class="sxs-lookup"><span data-stu-id="2ecf3-129">N01,N02</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ecf3-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ecf3-130">See Also</span></span>  
 [<span data-ttu-id="2ecf3-131">使用 HL7 2.XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="2ecf3-131">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)