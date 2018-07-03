---
title: HL7 2.4 XML 資料夾和事件 |Microsoft Docs
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
ms.assetid: bc6c5d75-66c7-4269-bfb9-59cab5999a73
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e7665a5101f5b49abd9ba087bd07cf799384c2a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993287"
---
# <a name="hl7-24-xml-folders-and-events"></a><span data-ttu-id="54417-102">HL7 2.4 XML 資料夾和事件</span><span class="sxs-lookup"><span data-stu-id="54417-102">HL7 2.4 XML Folders and Events</span></span>
<span data-ttu-id="54417-103">下表列出安裝精靈，XML 編碼訊息的 HL7 2.4 版資料夾內建立子資料夾。</span><span class="sxs-lookup"><span data-stu-id="54417-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.4 folder for XML-encoded messages.</span></span> <span data-ttu-id="54417-104">這些子資料夾包含由 Microsoft BizTalk Accelerator for HL7 結構描述 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 來驗證、 剖析和序列化此資料表的事件資料行中列出的事件。</span><span class="sxs-lookup"><span data-stu-id="54417-104">These subfolders contain the schemas used by Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="54417-105">子資料夾名稱描述兩個結構描述支援的事件的類型。</span><span class="sxs-lookup"><span data-stu-id="54417-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="54417-106">子資料夾</span><span class="sxs-lookup"><span data-stu-id="54417-106">Sub folder</span></span>|<span data-ttu-id="54417-107">事件</span><span class="sxs-lookup"><span data-stu-id="54417-107">Events</span></span>|  
|----------------|------------|  
|<span data-ttu-id="54417-108">病患的系統管理</span><span class="sxs-lookup"><span data-stu-id="54417-108">Patient Administration</span></span>|<span data-ttu-id="54417-109">管理 A01 A62、 K21、 K22、 K23、 K24、 Q21 Q24</span><span class="sxs-lookup"><span data-stu-id="54417-109">A01-A62, K21,K22,K23,K24,Q21-Q24</span></span>|  
|<span data-ttu-id="54417-110">訂單項目</span><span class="sxs-lookup"><span data-stu-id="54417-110">Order Entry</span></span>|<span data-ttu-id="54417-111">O01 O22、 Q06、 Q26 Q30、 RAR、 RDR、 RER、 RGR、 ROR、 V01 V04、 Z73、 Z74</span><span class="sxs-lookup"><span data-stu-id="54417-111">O01-O22, Q06, Q26-Q30, RAR,RDR,RER,RGR,ROR, V01-V04, Z73, Z74</span></span>|  
|<span data-ttu-id="54417-112">查詢</span><span class="sxs-lookup"><span data-stu-id="54417-112">Query</span></span>|<span data-ttu-id="54417-113">J01、 J02、 K11、 K13、 K15、 Q01 Q05、 Q07 Q09、 Q11、 Q13、 Q15 Q17、 R07 R09、 Z75 Z99</span><span class="sxs-lookup"><span data-stu-id="54417-113">J01,J02,K11,K13,K15, Q01-Q05, Q07-Q09, Q11,Q13,Q15-Q17, R07-R09, Z75-Z99</span></span>|  
|<span data-ttu-id="54417-114">財務管理</span><span class="sxs-lookup"><span data-stu-id="54417-114">Financial Management</span></span>|<span data-ttu-id="54417-115">P01 ~ P06、 P10</span><span class="sxs-lookup"><span data-stu-id="54417-115">P01~P06, P10</span></span>|  
|<span data-ttu-id="54417-116">觀察報告</span><span class="sxs-lookup"><span data-stu-id="54417-116">Observation Reporting</span></span>|<span data-ttu-id="54417-117">C01 C12、 P07、 P08、 P09、 R01、 R02、 R04、 R21、 W01、 W02</span><span class="sxs-lookup"><span data-stu-id="54417-117">C01-C12, P07,P08,P09, R01,R02,R04, R21, W01, W02</span></span>|  
|<span data-ttu-id="54417-118">主版檔案</span><span class="sxs-lookup"><span data-stu-id="54417-118">Master Files</span></span>|<span data-ttu-id="54417-119">M01 M12 MFA</span><span class="sxs-lookup"><span data-stu-id="54417-119">M01-M12, MFA</span></span>|  
|<span data-ttu-id="54417-120">醫療記錄/資訊管理</span><span class="sxs-lookup"><span data-stu-id="54417-120">Medical Records/Information Management</span></span>|<span data-ttu-id="54417-121">T01 T12</span><span class="sxs-lookup"><span data-stu-id="54417-121">T01-T12</span></span>|  
|<span data-ttu-id="54417-122">排程</span><span class="sxs-lookup"><span data-stu-id="54417-122">Scheduling</span></span>|<span data-ttu-id="54417-123">S01 S26</span><span class="sxs-lookup"><span data-stu-id="54417-123">S01-S26</span></span>|  
|<span data-ttu-id="54417-124">病患的轉介</span><span class="sxs-lookup"><span data-stu-id="54417-124">Patient Referral</span></span>|<span data-ttu-id="54417-125">I01 I15</span><span class="sxs-lookup"><span data-stu-id="54417-125">I01-I15</span></span>|  
|<span data-ttu-id="54417-126">病患照護</span><span class="sxs-lookup"><span data-stu-id="54417-126">Patient Care</span></span>|<span data-ttu-id="54417-127">PC1 PCH，PCJ，PCK PCL</span><span class="sxs-lookup"><span data-stu-id="54417-127">PC1-PCH, PCJ,PCK,PCL</span></span>|  
|<span data-ttu-id="54417-128">臨床實驗室自動化</span><span class="sxs-lookup"><span data-stu-id="54417-128">Clinical Laboratory Automation</span></span>|<span data-ttu-id="54417-129">U01 U13</span><span class="sxs-lookup"><span data-stu-id="54417-129">U01-U13</span></span>|  
|<span data-ttu-id="54417-130">應用程式管理</span><span class="sxs-lookup"><span data-stu-id="54417-130">Application Management</span></span>|<span data-ttu-id="54417-131">N01 N02</span><span class="sxs-lookup"><span data-stu-id="54417-131">N01,N02</span></span>|  
|<span data-ttu-id="54417-132">人員管理</span><span class="sxs-lookup"><span data-stu-id="54417-132">Personnel Management</span></span>|<span data-ttu-id="54417-133">版本 B01-K25，B06 Q25</span><span class="sxs-lookup"><span data-stu-id="54417-133">B01-B06, K25,Q25</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54417-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54417-134">See Also</span></span>  
 [<span data-ttu-id="54417-135">使用 HL7 2.XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="54417-135">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)