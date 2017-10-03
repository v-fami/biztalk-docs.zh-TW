---
title: "使用 PIP 規格建立程序組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PIPs, PIP settings
- PIPs, PIP secifications
- process configuration, PIPs
- PIPs, process configuration
ms.assetid: 64f0f5fb-f880-4ef1-95d7-2575b8d0bcff
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 777f32e5a9e035f6009f5450eb48ae8286159f05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-pip-specification-to-create-a-process-configuration"></a><span data-ttu-id="79bdc-102">使用 PIP 規格建立程序組態</span><span class="sxs-lookup"><span data-stu-id="79bdc-102">Using the PIP Specification to Create a Process Configuration</span></span>
<span data-ttu-id="79bdc-103">從 RosettaNet 組織 (從 RosettaNet.org) 下載交易夥伴介面程序 (PIP) 後，下載封裝包含 PIP 規格文件。</span><span class="sxs-lookup"><span data-stu-id="79bdc-103">After you download a Partner Interface Process (PIP) from the RosettaNet organization (from RosettaNet.org), the download package includes a PIP specification document.</span></span> <span data-ttu-id="79bdc-104">此文件可指導您在 [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] 管理主控台中建立程序組態時，要使用哪些設定。</span><span class="sxs-lookup"><span data-stu-id="79bdc-104">This document contains guidance on what settings to use when you create a process configuration in the [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console.</span></span>  
  
## <a name="how-pip-settings-map-to-the-pip-specification"></a><span data-ttu-id="79bdc-105">PIP 設定如何對應至 PIP 規格</span><span class="sxs-lookup"><span data-stu-id="79bdc-105">How PIP Settings Map to the PIP Specification</span></span>  
 <span data-ttu-id="79bdc-106">下表描述 PIP 設定如何對應至 RosettaNet PIP 規格中的資訊。</span><span class="sxs-lookup"><span data-stu-id="79bdc-106">The following table describes how PIP settings map to information in the RosettaNet PIP specification.</span></span>  
  
|<span data-ttu-id="79bdc-107">程序組態設定</span><span class="sxs-lookup"><span data-stu-id="79bdc-107">Process Configuration setting</span></span>|<span data-ttu-id="79bdc-108">PIP 規格中的資訊</span><span class="sxs-lookup"><span data-stu-id="79bdc-108">Information in the PIP specification</span></span>|  
|-----------------------------------|------------------------------------------|  
|<span data-ttu-id="79bdc-109">程序代碼</span><span class="sxs-lookup"><span data-stu-id="79bdc-109">Process Code</span></span>|<span data-ttu-id="79bdc-110">標題頁上的子標題，例如，"PIP3A4"</span><span class="sxs-lookup"><span data-stu-id="79bdc-110">Subheading on the title page, for example, "PIP3A4"</span></span>|  
|<span data-ttu-id="79bdc-111">Version</span><span class="sxs-lookup"><span data-stu-id="79bdc-111">Version</span></span>|<span data-ttu-id="79bdc-112">標題頁上的 PIP「版本識別碼」子標題，例如，"02.02.00"</span><span class="sxs-lookup"><span data-stu-id="79bdc-112">PIP Version Identifier subheading on the title page, for example, "02.02.00"</span></span>|  
|<span data-ttu-id="79bdc-113">程序名稱</span><span class="sxs-lookup"><span data-stu-id="79bdc-113">Process name</span></span>|<span data-ttu-id="79bdc-114">標題頁上的子標題，例如，"Request Purchase Order"</span><span class="sxs-lookup"><span data-stu-id="79bdc-114">Subheading on the title page, for example, "Request Purchase Order"</span></span>|  
|<span data-ttu-id="79bdc-115">描述 (一般索引標籤)</span><span class="sxs-lookup"><span data-stu-id="79bdc-115">Description (General tab)</span></span>|<span data-ttu-id="79bdc-116">3.1 節，商務程序定義</span><span class="sxs-lookup"><span data-stu-id="79bdc-116">Section 3.1, Business Process Definition</span></span>|  
|<span data-ttu-id="79bdc-117">需要不可否認性</span><span class="sxs-lookup"><span data-stu-id="79bdc-117">Non-Repudiation Required</span></span>|<span data-ttu-id="79bdc-118">表 3-3：商務活動效能控制項</span><span class="sxs-lookup"><span data-stu-id="79bdc-118">Table 3-3: Business Activity Performance Controls</span></span>|  
|<span data-ttu-id="79bdc-119">通知時間 (秒)</span><span class="sxs-lookup"><span data-stu-id="79bdc-119">Time to Acknowledge (Seconds)</span></span>|<span data-ttu-id="79bdc-120">表 3-3：商務活動效能控制項</span><span class="sxs-lookup"><span data-stu-id="79bdc-120">Table 3-3: Business Activity Performance Controls</span></span>|  
|<span data-ttu-id="79bdc-121">需要授權？</span><span class="sxs-lookup"><span data-stu-id="79bdc-121">Is Authorization Required?</span></span>|<span data-ttu-id="79bdc-122">表 3-3：商務活動效能控制項</span><span class="sxs-lookup"><span data-stu-id="79bdc-122">Table 3-3: Business Activity Performance Controls</span></span>|  
|<span data-ttu-id="79bdc-123">需要持續的機密性</span><span class="sxs-lookup"><span data-stu-id="79bdc-123">Is Persistent Confidentiality Required</span></span>|<span data-ttu-id="79bdc-124">(在 PIP 規格中無參照)</span><span class="sxs-lookup"><span data-stu-id="79bdc-124">(No reference from the PIP specification)</span></span>|  
|<span data-ttu-id="79bdc-125">需要安全性傳輸？</span><span class="sxs-lookup"><span data-stu-id="79bdc-125">Is Secure Transport Required?</span></span>|<span data-ttu-id="79bdc-126">表 4-3：訊息交換控制項</span><span class="sxs-lookup"><span data-stu-id="79bdc-126">Table 4-3: Message Exchange Controls</span></span>|  
|<span data-ttu-id="79bdc-127">單向動作</span><span class="sxs-lookup"><span data-stu-id="79bdc-127">Is Single Action</span></span>|<span data-ttu-id="79bdc-128">4.3 節，商務交易對話規格</span><span class="sxs-lookup"><span data-stu-id="79bdc-128">Section 4.3, Business Transaction Dialog Specification</span></span>|  
|<span data-ttu-id="79bdc-129">來源與內容的不可否認性</span><span class="sxs-lookup"><span data-stu-id="79bdc-129">Non-Repudiation of Origin and Content</span></span>|<span data-ttu-id="79bdc-130">表 3-3：商務活動效能控制項</span><span class="sxs-lookup"><span data-stu-id="79bdc-130">Table 3-3: Business Activity Performance Controls</span></span>|  
|<span data-ttu-id="79bdc-131">重試計數</span><span class="sxs-lookup"><span data-stu-id="79bdc-131">Retry Count</span></span>|<span data-ttu-id="79bdc-132">表 3-3：商務活動效能控制項</span><span class="sxs-lookup"><span data-stu-id="79bdc-132">Table 3-3: Business Activity Performance Controls</span></span>|  
|<span data-ttu-id="79bdc-133">執行時間</span><span class="sxs-lookup"><span data-stu-id="79bdc-133">Time to Perform</span></span>|<span data-ttu-id="79bdc-134">表 3-3：商務活動效能控制項</span><span class="sxs-lookup"><span data-stu-id="79bdc-134">Table 3-3: Business Activity Performance Controls</span></span>|  
|<span data-ttu-id="79bdc-135">名稱</span><span class="sxs-lookup"><span data-stu-id="79bdc-135">Name</span></span>|<span data-ttu-id="79bdc-136">表 3-3：商務活動效能控制項 (活動名稱)</span><span class="sxs-lookup"><span data-stu-id="79bdc-136">Table 3-3: Business Activity Performance Controls (Activity Name)</span></span>|  
|<span data-ttu-id="79bdc-137">類型</span><span class="sxs-lookup"><span data-stu-id="79bdc-137">Type</span></span>|<span data-ttu-id="79bdc-138">(在 PIP 規格中無參照 - 供日後使用)</span><span class="sxs-lookup"><span data-stu-id="79bdc-138">(No reference from the PIP specification - for future use)</span></span>|  
|<span data-ttu-id="79bdc-139">描述 (啟動者與回應索引標籤)</span><span class="sxs-lookup"><span data-stu-id="79bdc-139">Description (Initiator and Response tabs)</span></span>|<span data-ttu-id="79bdc-140">表 3-4：PIP 商務文件</span><span class="sxs-lookup"><span data-stu-id="79bdc-140">Table 3-4: PIP Business Documents</span></span>|  
|<span data-ttu-id="79bdc-141">名稱 (啟動者與回應索引標籤)</span><span class="sxs-lookup"><span data-stu-id="79bdc-141">Name (Initiator and Response tabs)</span></span>|<span data-ttu-id="79bdc-142">表 3-4：PIP 商務文件</span><span class="sxs-lookup"><span data-stu-id="79bdc-142">Table 3-4: PIP Business Documents</span></span>|  
|<span data-ttu-id="79bdc-143">角色 (啟動者與回應索引標籤)</span><span class="sxs-lookup"><span data-stu-id="79bdc-143">Role (Initiator and Response tabs)</span></span>|<span data-ttu-id="79bdc-144">表 3-1：交易夥伴角色描述</span><span class="sxs-lookup"><span data-stu-id="79bdc-144">Table 3-1: Partner Role Descriptions</span></span>|  
|<span data-ttu-id="79bdc-145">角色描述 (啟動者與回應索引標籤)</span><span class="sxs-lookup"><span data-stu-id="79bdc-145">Role Description (Initiator and Response tabs)</span></span>|<span data-ttu-id="79bdc-146">表 3-1：交易夥伴角色描述</span><span class="sxs-lookup"><span data-stu-id="79bdc-146">Table 3-1: Partner Role Descriptions</span></span>|  
|<span data-ttu-id="79bdc-147">角色類型 (啟動者與回應索引標籤)</span><span class="sxs-lookup"><span data-stu-id="79bdc-147">Role Type (Initiator and Response tabs)</span></span>|<span data-ttu-id="79bdc-148">表 3-1：交易夥伴角色描述</span><span class="sxs-lookup"><span data-stu-id="79bdc-148">Table 3-1: Partner Role Descriptions</span></span>|  
|<span data-ttu-id="79bdc-149">服務</span><span class="sxs-lookup"><span data-stu-id="79bdc-149">Service</span></span>|<span data-ttu-id="79bdc-150">表 4-1：網路元件規格</span><span class="sxs-lookup"><span data-stu-id="79bdc-150">Table 4-1: Network Component Specification</span></span>|  
|<span data-ttu-id="79bdc-151">服務分類</span><span class="sxs-lookup"><span data-stu-id="79bdc-151">Service Classification</span></span>|<span data-ttu-id="79bdc-152">表 4-1：網路元件規格</span><span class="sxs-lookup"><span data-stu-id="79bdc-152">Table 4-1: Network Component Specification</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79bdc-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79bdc-153">See Also</span></span>  
 [<span data-ttu-id="79bdc-154">如何建立或編輯程序組態</span><span class="sxs-lookup"><span data-stu-id="79bdc-154">How to Create or Edit a Process Configuration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)