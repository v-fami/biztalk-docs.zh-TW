---
title: 使用 [原則總管] |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, Policy Explorer
- policies, Policy Explorer
- business rules, Policy Explorer
- Policy Explorer [Business Rule Composer]
ms.assetid: 249b1b72-ba84-4695-ba2b-16f081710b20
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66b88618f10bf204701e6fcd68d7d95007966c50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288342"
---
# <a name="using-policy-explorer"></a><span data-ttu-id="b45e8-102">使用 [原則總管]</span><span class="sxs-lookup"><span data-stu-id="b45e8-102">Using Policy Explorer</span></span>
<span data-ttu-id="b45e8-103">您可以使用 [原則總管] 管理規則存放區中的原則和規則。</span><span class="sxs-lookup"><span data-stu-id="b45e8-103">You can use the Policy Explorer to manage policies and rules in the rule store.</span></span> <span data-ttu-id="b45e8-104">您可以建立、修改和刪除原則及規則，也可以測試、發佈、部署和解除部署原則。</span><span class="sxs-lookup"><span data-stu-id="b45e8-104">You can create, modify, and delete policies and rules, and you can test, publish, deploy, and undeploy policies.</span></span>  
  
 <span data-ttu-id="b45e8-105">下表描述在開發新原則和新規則時，在 [原則總管] 中可以使用的命令。</span><span class="sxs-lookup"><span data-stu-id="b45e8-105">The following table describes the commands within the Policy Explorer that can be used in the process of developing new policies and rules.</span></span>  
  
|<span data-ttu-id="b45e8-106">使用</span><span class="sxs-lookup"><span data-stu-id="b45e8-106">Use this</span></span>|<span data-ttu-id="b45e8-107">動作</span><span class="sxs-lookup"><span data-stu-id="b45e8-107">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="b45e8-108">**新增原則**</span><span class="sxs-lookup"><span data-stu-id="b45e8-108">**Add New Policy**</span></span>|<span data-ttu-id="b45e8-109">建立新原則 (規則集)。</span><span class="sxs-lookup"><span data-stu-id="b45e8-109">Create a new policy (rule set).</span></span>|  
|<span data-ttu-id="b45e8-110">**加入新的版本**</span><span class="sxs-lookup"><span data-stu-id="b45e8-110">**Add New Version**</span></span>|<span data-ttu-id="b45e8-111">建立選取原則的新空白版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-111">Create a new empty version of the selected policy.</span></span> <span data-ttu-id="b45e8-112">您可以複製其他版本的規則貼到新版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-112">You can copy rules from other versions and paste them into the new version.</span></span>|  
|<span data-ttu-id="b45e8-113">**複製 （原則版本）**</span><span class="sxs-lookup"><span data-stu-id="b45e8-113">**Copy (Policy Version)**</span></span>|<span data-ttu-id="b45e8-114">將選取的原則版本貼到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="b45e8-114">Copy the selected policy version to the Clipboard.</span></span>|  
|<span data-ttu-id="b45e8-115">**複製 （規則）**</span><span class="sxs-lookup"><span data-stu-id="b45e8-115">**Copy (Rule)**</span></span>|<span data-ttu-id="b45e8-116">將選取的規則貼到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="b45e8-116">Copy the selected rule to the Clipboard.</span></span>|  
|<span data-ttu-id="b45e8-117">**剪下 （規則）**</span><span class="sxs-lookup"><span data-stu-id="b45e8-117">**Cut (Rule)**</span></span>|<span data-ttu-id="b45e8-118">將選取的規則貼到剪貼簿，並刪除該規則。</span><span class="sxs-lookup"><span data-stu-id="b45e8-118">Copy the selected rule to the Clipboard and delete it.</span></span>|  
|<span data-ttu-id="b45e8-119">**貼上 （原則版本）**</span><span class="sxs-lookup"><span data-stu-id="b45e8-119">**Paste (Policy Version)**</span></span>|<span data-ttu-id="b45e8-120">將原則版本及其內容貼到選取的原則。</span><span class="sxs-lookup"><span data-stu-id="b45e8-120">Paste a policy version and its contents into a selected policy.</span></span>|  
|<span data-ttu-id="b45e8-121">**貼上 （規則）**</span><span class="sxs-lookup"><span data-stu-id="b45e8-121">**Paste (Rule)**</span></span>|<span data-ttu-id="b45e8-122">將規則貼到選取的原則版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-122">Paste a rule into the selected policy version.</span></span>|  
|<span data-ttu-id="b45e8-123">**刪除 （原則版本）**</span><span class="sxs-lookup"><span data-stu-id="b45e8-123">**Delete (Policy Version)**</span></span>|<span data-ttu-id="b45e8-124">刪除選取的原則版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-124">Delete the selected policy version.</span></span>|  
|<span data-ttu-id="b45e8-125">**刪除 （規則）**</span><span class="sxs-lookup"><span data-stu-id="b45e8-125">**Delete (Rule)**</span></span>|<span data-ttu-id="b45e8-126">刪除選取的規則。</span><span class="sxs-lookup"><span data-stu-id="b45e8-126">Delete the selected rule.</span></span>|  
|<span data-ttu-id="b45e8-127">**Delete**</span><span class="sxs-lookup"><span data-stu-id="b45e8-127">**Delete**</span></span>|<span data-ttu-id="b45e8-128">刪除選取的原則及其所有版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-128">Delete the selected policy and all its versions.</span></span>|  
|<span data-ttu-id="b45e8-129">**加入新的規則**</span><span class="sxs-lookup"><span data-stu-id="b45e8-129">**Add New Rule**</span></span>|<span data-ttu-id="b45e8-130">在選取的原則版本中建立新規則。</span><span class="sxs-lookup"><span data-stu-id="b45e8-130">Create a new rule in the selected policy version.</span></span>|  
|<span data-ttu-id="b45e8-131">**儲存**</span><span class="sxs-lookup"><span data-stu-id="b45e8-131">**Save**</span></span>|<span data-ttu-id="b45e8-132">儲存對選取版本及其規則所作的變更。</span><span class="sxs-lookup"><span data-stu-id="b45e8-132">Save any changes made to the selected version and its rules.</span></span>|  
|<span data-ttu-id="b45e8-133">**發行**</span><span class="sxs-lookup"><span data-stu-id="b45e8-133">**Publish**</span></span>|<span data-ttu-id="b45e8-134">發佈選取的原則版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-134">Publish the selected policy version.</span></span> <span data-ttu-id="b45e8-135">請注意，您無法直接修改已發佈的版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-135">Note that you cannot directly modify a published version.</span></span> <span data-ttu-id="b45e8-136">您可以將已發佈的版本複製並貼到原則的新版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-136">You can copy and paste it to a new version on the policy.</span></span>|  
|<span data-ttu-id="b45e8-137">**重新載入**</span><span class="sxs-lookup"><span data-stu-id="b45e8-137">**Reload**</span></span>|<span data-ttu-id="b45e8-138">重新載入選取的原則版本及其規則，可以選擇是否捨棄對該版本目前所做的變更，並從規則存放區還原其內容。</span><span class="sxs-lookup"><span data-stu-id="b45e8-138">Reload the selected policy version and its rules, with the option to discard any current changes made in that version and restore the contents from the rule store.</span></span>|  
|<span data-ttu-id="b45e8-139">**部署**</span><span class="sxs-lookup"><span data-stu-id="b45e8-139">**Deploy**</span></span>|<span data-ttu-id="b45e8-140">部署已發佈的原則版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-140">Deploy a published policy version.</span></span> <span data-ttu-id="b45e8-141">您必須部署原則版本才能讓以規則為基礎的應用程式使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-141">You must deploy a policy version to make it available to rule-based applications.</span></span>|  
|<span data-ttu-id="b45e8-142">**解除部署**</span><span class="sxs-lookup"><span data-stu-id="b45e8-142">**Undeploy**</span></span>|<span data-ttu-id="b45e8-143">解除部署原則版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-143">Undeploy a policy version.</span></span> <span data-ttu-id="b45e8-144">解除部署版本後，以規則為基礎的應用程式就無法再使用此版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-144">After a version is undeployed, it is no longer available to rule-based applications.</span></span>|  
|<span data-ttu-id="b45e8-145">**測試原則**</span><span class="sxs-lookup"><span data-stu-id="b45e8-145">**Test Policy**</span></span>|<span data-ttu-id="b45e8-146">在部署之前先測試選取的原則版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-146">Test the selected policy version before deployment.</span></span>|  
  
## <a name="properties-window"></a><span data-ttu-id="b45e8-147">屬性視窗</span><span class="sxs-lookup"><span data-stu-id="b45e8-147">Properties window</span></span>  
 <span data-ttu-id="b45e8-148">下表說明原則版本的屬性。</span><span class="sxs-lookup"><span data-stu-id="b45e8-148">The following table describes the properties for a policy version.</span></span>  
  
|<span data-ttu-id="b45e8-149">屬性</span><span class="sxs-lookup"><span data-stu-id="b45e8-149">Property</span></span>|<span data-ttu-id="b45e8-150">值</span><span class="sxs-lookup"><span data-stu-id="b45e8-150">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="b45e8-151">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b45e8-151">**Name**</span></span>|<span data-ttu-id="b45e8-152">此原則的名稱。</span><span class="sxs-lookup"><span data-stu-id="b45e8-152">Name of the policy.</span></span><br /><br /> <span data-ttu-id="b45e8-153">您只可以變更此值變更**名稱**原則 （而非原則版本） 的屬性。</span><span class="sxs-lookup"><span data-stu-id="b45e8-153">You can only change this value by changing the **Name** property of the policy (not policy version).</span></span>|  
|<span data-ttu-id="b45e8-154">**事實擷取器**</span><span class="sxs-lookup"><span data-stu-id="b45e8-154">**Fact Retriever**</span></span>|<span data-ttu-id="b45e8-155">原則版本之事實擷取器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b45e8-155">Information about the fact retriever for the policy version.</span></span>|  
|<span data-ttu-id="b45e8-156">**最大執行迴圈深度**</span><span class="sxs-lookup"><span data-stu-id="b45e8-156">**Maximum Execution Loop Depth**</span></span>|<span data-ttu-id="b45e8-157">在擲回執行迴圈例外狀況之前，正向鏈結演算法的最大深度。</span><span class="sxs-lookup"><span data-stu-id="b45e8-157">Maximum depth of the forward-chaining algorithm before an execution loop exception is thrown.</span></span><br /><br /> <span data-ttu-id="b45e8-158">預設迴圈計數是 65536。</span><span class="sxs-lookup"><span data-stu-id="b45e8-158">The default loop count is 65536.</span></span>|  
|<span data-ttu-id="b45e8-159">**轉譯持續時間**</span><span class="sxs-lookup"><span data-stu-id="b45e8-159">**Translation Duration**</span></span>|<span data-ttu-id="b45e8-160">在擲回轉譯時間逾時例外狀況之前，轉譯規則的最大時間量。</span><span class="sxs-lookup"><span data-stu-id="b45e8-160">Maximum amount of time to translate the rules before a translation time-out exception is thrown.</span></span><br /><br /> <span data-ttu-id="b45e8-161">預設值為 60000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="b45e8-161">The default is 60000 milliseconds.</span></span>|  
|<span data-ttu-id="b45e8-162">**轉譯器**</span><span class="sxs-lookup"><span data-stu-id="b45e8-162">**Translator**</span></span>|<span data-ttu-id="b45e8-163">用於轉譯規則之轉譯程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b45e8-163">Information about the translator used to translate the rules.</span></span>|  
|<span data-ttu-id="b45e8-164">**目前的版本**</span><span class="sxs-lookup"><span data-stu-id="b45e8-164">**Current Version**</span></span>|<span data-ttu-id="b45e8-165">「原則總管」中目前選取的原則版本。</span><span class="sxs-lookup"><span data-stu-id="b45e8-165">The version of policy currently selected in the Policy Explorer.</span></span>|  
|<span data-ttu-id="b45e8-166">**版本描述**</span><span class="sxs-lookup"><span data-stu-id="b45e8-166">**Version Description**</span></span>|<span data-ttu-id="b45e8-167">目前版本的描述。</span><span class="sxs-lookup"><span data-stu-id="b45e8-167">The description of the current version.</span></span>|  
  
 <span data-ttu-id="b45e8-168">下表說明規則的屬性。</span><span class="sxs-lookup"><span data-stu-id="b45e8-168">The following table describes the properties for a rule.</span></span>  
  
|<span data-ttu-id="b45e8-169">屬性</span><span class="sxs-lookup"><span data-stu-id="b45e8-169">Property</span></span>|<span data-ttu-id="b45e8-170">值</span><span class="sxs-lookup"><span data-stu-id="b45e8-170">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="b45e8-171">**作用中**</span><span class="sxs-lookup"><span data-stu-id="b45e8-171">**Active**</span></span>|<span data-ttu-id="b45e8-172">指示規則為啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="b45e8-172">Indicates whether the rule is enabled or disabled</span></span>|  
|<span data-ttu-id="b45e8-173">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b45e8-173">**Name**</span></span>|<span data-ttu-id="b45e8-174">規則的名稱。</span><span class="sxs-lookup"><span data-stu-id="b45e8-174">Name of the rule.</span></span>|  
|<span data-ttu-id="b45e8-175">**優先權**</span><span class="sxs-lookup"><span data-stu-id="b45e8-175">**Priority**</span></span>|<span data-ttu-id="b45e8-176">原則中的規則優先順序。</span><span class="sxs-lookup"><span data-stu-id="b45e8-176">Priority of the rule within the policy.</span></span> <span data-ttu-id="b45e8-177">指數越高，規則優先順序越高。</span><span class="sxs-lookup"><span data-stu-id="b45e8-177">The higher the index, the higher the rule priority.</span></span> <span data-ttu-id="b45e8-178">會先引發優先順序較高的動作。</span><span class="sxs-lookup"><span data-stu-id="b45e8-178">Actions of a higher priority rule will fire first.</span></span><br /><br /> <span data-ttu-id="b45e8-179">預設值是 0，它代表中優先順序。</span><span class="sxs-lookup"><span data-stu-id="b45e8-179">The default is 0 and represents the middle priority.</span></span>|