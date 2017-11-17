---
title: "HL7 2.4 XML 資料夾和事件 |Microsoft 文件"
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
ms.assetid: bc6c5d75-66c7-4269-bfb9-59cab5999a73
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10c9445a1d5c7978b526fd0347dc6defa3214640
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-24-xml-folders-and-events"></a><span data-ttu-id="d2dad-102">HL7 2.4 XML 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="d2dad-102">HL7 2.4 XML Folders and Events</span></span>
<span data-ttu-id="d2dad-103">下表列出安裝精靈的 XML 編碼訊息的 HL7 2.4 版資料夾內所建立的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="d2dad-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.4 folder for XML-encoded messages.</span></span> <span data-ttu-id="d2dad-104">這些子資料夾包含使用的結構描述[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 來驗證、 剖析和序列化此資料表的事件資料行中列出的事件。</span><span class="sxs-lookup"><span data-stu-id="d2dad-104">These subfolders contain the schemas used by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="d2dad-105">子資料夾名稱會描述這些結構描述支援的事件類型。</span><span class="sxs-lookup"><span data-stu-id="d2dad-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="d2dad-106">子資料夾</span><span class="sxs-lookup"><span data-stu-id="d2dad-106">Sub folder</span></span>|<span data-ttu-id="d2dad-107">事件</span><span class="sxs-lookup"><span data-stu-id="d2dad-107">Events</span></span>|  
|----------------|------------|  
|<span data-ttu-id="d2dad-108">病患的系統管理</span><span class="sxs-lookup"><span data-stu-id="d2dad-108">Patient Administration</span></span>|<span data-ttu-id="d2dad-109">A01 A62、 K21、 K22、 K23、 K24、 Q21 Q24</span><span class="sxs-lookup"><span data-stu-id="d2dad-109">A01-A62, K21,K22,K23,K24,Q21-Q24</span></span>|  
|<span data-ttu-id="d2dad-110">訂單項目</span><span class="sxs-lookup"><span data-stu-id="d2dad-110">Order Entry</span></span>|<span data-ttu-id="d2dad-111">O01 O22、 Q06、 Q26 Q30、 RAR、 RDR、 RER、 RGR、 ROR、 V01 V04、 Z73、 Z74</span><span class="sxs-lookup"><span data-stu-id="d2dad-111">O01-O22, Q06, Q26-Q30, RAR,RDR,RER,RGR,ROR, V01-V04, Z73, Z74</span></span>|  
|<span data-ttu-id="d2dad-112">查詢</span><span class="sxs-lookup"><span data-stu-id="d2dad-112">Query</span></span>|<span data-ttu-id="d2dad-113">J01、 J02、 K11、 K13、 K15、 Q01 Q05、 Q07 Q09、 Q11、 Q13、 Q15 Q17、 R07 R09、 Z75 Z99</span><span class="sxs-lookup"><span data-stu-id="d2dad-113">J01,J02,K11,K13,K15, Q01-Q05, Q07-Q09, Q11,Q13,Q15-Q17, R07-R09, Z75-Z99</span></span>|  
|<span data-ttu-id="d2dad-114">財務管理</span><span class="sxs-lookup"><span data-stu-id="d2dad-114">Financial Management</span></span>|<span data-ttu-id="d2dad-115">P01 ~ P06、 P10</span><span class="sxs-lookup"><span data-stu-id="d2dad-115">P01~P06, P10</span></span>|  
|<span data-ttu-id="d2dad-116">觀察報告</span><span class="sxs-lookup"><span data-stu-id="d2dad-116">Observation Reporting</span></span>|<span data-ttu-id="d2dad-117">C01 C12、 P07、 P08、 P09、 R01、 R02、 R04、 R21、 W01、 W02</span><span class="sxs-lookup"><span data-stu-id="d2dad-117">C01-C12, P07,P08,P09, R01,R02,R04, R21, W01, W02</span></span>|  
|<span data-ttu-id="d2dad-118">主版檔案</span><span class="sxs-lookup"><span data-stu-id="d2dad-118">Master Files</span></span>|<span data-ttu-id="d2dad-119">M01 M12 MFA</span><span class="sxs-lookup"><span data-stu-id="d2dad-119">M01-M12, MFA</span></span>|  
|<span data-ttu-id="d2dad-120">醫療的記錄資訊管理</span><span class="sxs-lookup"><span data-stu-id="d2dad-120">Medical Records/Information Management</span></span>|<span data-ttu-id="d2dad-121">T01 T12</span><span class="sxs-lookup"><span data-stu-id="d2dad-121">T01-T12</span></span>|  
|<span data-ttu-id="d2dad-122">排程</span><span class="sxs-lookup"><span data-stu-id="d2dad-122">Scheduling</span></span>|<span data-ttu-id="d2dad-123">S01 S26</span><span class="sxs-lookup"><span data-stu-id="d2dad-123">S01-S26</span></span>|  
|<span data-ttu-id="d2dad-124">病患的轉介</span><span class="sxs-lookup"><span data-stu-id="d2dad-124">Patient Referral</span></span>|<span data-ttu-id="d2dad-125">I01 I15</span><span class="sxs-lookup"><span data-stu-id="d2dad-125">I01-I15</span></span>|  
|<span data-ttu-id="d2dad-126">病患照護</span><span class="sxs-lookup"><span data-stu-id="d2dad-126">Patient Care</span></span>|<span data-ttu-id="d2dad-127">PC1-PCJ，PCK，PCL PCH</span><span class="sxs-lookup"><span data-stu-id="d2dad-127">PC1-PCH, PCJ,PCK,PCL</span></span>|  
|<span data-ttu-id="d2dad-128">臨床實驗室自動化</span><span class="sxs-lookup"><span data-stu-id="d2dad-128">Clinical Laboratory Automation</span></span>|<span data-ttu-id="d2dad-129">U01 U13</span><span class="sxs-lookup"><span data-stu-id="d2dad-129">U01-U13</span></span>|  
|<span data-ttu-id="d2dad-130">應用程式管理</span><span class="sxs-lookup"><span data-stu-id="d2dad-130">Application Management</span></span>|<span data-ttu-id="d2dad-131">N01 N02</span><span class="sxs-lookup"><span data-stu-id="d2dad-131">N01,N02</span></span>|  
|<span data-ttu-id="d2dad-132">人員管理</span><span class="sxs-lookup"><span data-stu-id="d2dad-132">Personnel Management</span></span>|<span data-ttu-id="d2dad-133">B01 B06，K25，Q25</span><span class="sxs-lookup"><span data-stu-id="d2dad-133">B01-B06, K25,Q25</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2dad-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2dad-134">See Also</span></span>  
 [<span data-ttu-id="d2dad-135">使用 HL7 2.XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="d2dad-135">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)