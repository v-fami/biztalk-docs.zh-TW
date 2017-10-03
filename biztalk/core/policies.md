---
title: "原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Engine, policies
- policies, about policies
- policies, deploying
- policies, Business Rules Engine
- policies
- business rules, policies
- policies, versioning
- policies, testing
- policies, creating
- policies, updating
ms.assetid: 2e0ae081-938d-4e2a-947e-1c0ecfebb4b8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd05d6cf67d89ee811cac45ac3950697db74f59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="policies"></a><span data-ttu-id="3db40-102">原則</span><span class="sxs-lookup"><span data-stu-id="3db40-102">Policies</span></span>
<span data-ttu-id="3db40-103">「原則」 (Policy) 是規則的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="3db40-103">A policy is a logical grouping of rules.</span></span> <span data-ttu-id="3db40-104">您可以編輯原則的版本、儲存它、藉由將它套用到事實來測試，以及當您對結果感到滿意時，將它發佈和部署到生產環境。</span><span class="sxs-lookup"><span data-stu-id="3db40-104">You compose a version of a policy, save it, test it by applying it to facts, and, when you are satisfied with the results, publish it and deploy it to a production environment.</span></span>  
  
## <a name="policy-composition"></a><span data-ttu-id="3db40-105">原則撰寫</span><span class="sxs-lookup"><span data-stu-id="3db40-105">Policy Composition</span></span>  
 <span data-ttu-id="3db40-106">您可以藉由建構來自事實與定義的規則，在商務規則編輯器中編輯原則。</span><span class="sxs-lookup"><span data-stu-id="3db40-106">You can compose policies in the Business Rule Composer by constructing rules from facts and definitions.</span></span> <span data-ttu-id="3db40-107">原則可以包含任意的大量規則集合，但是一般而言，您會從規則編輯原則，而那些規則會與使用原則之應用程式內容中的特定商務網域有關。</span><span class="sxs-lookup"><span data-stu-id="3db40-107">A policy can contain an arbitrarily large set of rules, but typically you compose a policy from rules that pertain to a specific business domain within the context of the application that will be using the policy.</span></span>  
  
## <a name="policy-testing"></a><span data-ttu-id="3db40-108">原則測試</span><span class="sxs-lookup"><span data-stu-id="3db40-108">Policy Testing</span></span>  
 <span data-ttu-id="3db40-109">將原則發佈和部署在生產環境之前，您可以先有效地執行原則的測試。</span><span class="sxs-lookup"><span data-stu-id="3db40-109">You can effectively perform a test run of your policy before it is published and deployed in a production environment.</span></span> <span data-ttu-id="3db40-110">商務規則編輯器允許您提供事實的執行個體給原則、執行該原則，以及檢視其輸出。</span><span class="sxs-lookup"><span data-stu-id="3db40-110">The Business Rule Composer allows you to supply instances of facts to a policy, run the policy, and view its output.</span></span> <span data-ttu-id="3db40-111">輸出會包含事實活動、規則執行、條件評估，以及對議程的更新。</span><span class="sxs-lookup"><span data-stu-id="3db40-111">The output includes fact activity, rule execution, condition evaluation, and updates to the agenda.</span></span>  
  
## <a name="policy-versions"></a><span data-ttu-id="3db40-112">原則版本</span><span class="sxs-lookup"><span data-stu-id="3db40-112">Policy Versions</span></span>  
 <span data-ttu-id="3db40-113">在定義原則中的所有規則之後，您可以發佈原則版本。</span><span class="sxs-lookup"><span data-stu-id="3db40-113">After you have defined all the rules in your policy, you can publish the policy version.</span></span> <span data-ttu-id="3db40-114">在此方式中，原則會被鎖定，且其行為是妥善定義的。</span><span class="sxs-lookup"><span data-stu-id="3db40-114">In this way the policy is locked down, and its behavior is well-defined.</span></span>  
  
 <span data-ttu-id="3db40-115">指定的原則版本可用於您商務環境中的一組指定情況下，當那些情況變更時，會以另一個版本來取代。</span><span class="sxs-lookup"><span data-stu-id="3db40-115">A given policy version can be used under a given set of circumstances in your business environment, and replaced by another version when those circumstances change.</span></span> <span data-ttu-id="3db40-116">此外，新版本與舊版本可以同時由不同的應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="3db40-116">Also, both new and old versions can be used simultaneously by different applications.</span></span>  
  
## <a name="policy-deployment"></a><span data-ttu-id="3db40-117">原則部署</span><span class="sxs-lookup"><span data-stu-id="3db40-117">Policy Deployment</span></span>  
 <span data-ttu-id="3db40-118">當您的原則已經準備在生產環境中執行時，您可以部署它，使其可為裝載應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="3db40-118">When your policy is ready to be run in a production environment, you can deploy it to make it available to a hosting application.</span></span>  
  
## <a name="dynamic-policy-updates"></a><span data-ttu-id="3db40-119">動態原則更新</span><span class="sxs-lookup"><span data-stu-id="3db40-119">Dynamic Policy Updates</span></span>  
 <span data-ttu-id="3db40-120">動態原則更新允許您獨立修改執行中商務程序的原則。</span><span class="sxs-lookup"><span data-stu-id="3db40-120">Dynamic policy updates allow you to modify policies independently of a running business process.</span></span> <span data-ttu-id="3db40-121">您可以建立和部署原則的更新版本，裝載應用程式幾乎會即時併入該項更新。</span><span class="sxs-lookup"><span data-stu-id="3db40-121">You can create and deploy an updated version of the policy, and the hosting application can incorporate the update in near real time.</span></span> <span data-ttu-id="3db40-122">此更新不會要求您變更任何的程式碼，因此，您可以避免重新開發與重新部署應用程式的負擔。</span><span class="sxs-lookup"><span data-stu-id="3db40-122">This update does not require you to change any code, and thus you can avoid the overhead of redeveloping and redeploying the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db40-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3db40-123">See Also</span></span>  
 [<span data-ttu-id="3db40-124">商務規則引擎</span><span class="sxs-lookup"><span data-stu-id="3db40-124">Business Rules Engine</span></span>](../core/business-rules-engine.md)