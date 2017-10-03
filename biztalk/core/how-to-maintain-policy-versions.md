---
title: "如何維護原則版本 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, publishing
- publishing policies
- updating, policies
- versioning, policies
- policies, versioning
- policies, updating
ms.assetid: 6e35b2bd-1ecd-45ea-aff3-4ad2437568a4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09c73b3575ec484ab611fccac920cef6d96d3800
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-maintain-policy-versions"></a><span data-ttu-id="1230f-102">如何維護原則版本</span><span class="sxs-lookup"><span data-stu-id="1230f-102">How to Maintain Policy Versions</span></span>
<span data-ttu-id="1230f-103">將規則新增至原則版本後，可以將版本儲存至規則存放區以供進一步開發之用，或是您可以將它發佈以建立定義正確且不變，可加以部署以用於以規則為基礎的應用程式中的規則集。</span><span class="sxs-lookup"><span data-stu-id="1230f-103">After you add rules to a version of your policy, you can save the version to the rule store for further development, or you can publish it to create a well-defined, immutable set of rules that can be deployed for use in a rule-based application.</span></span>  
  
 <span data-ttu-id="1230f-104">本主題包含下列工作的程序：</span><span class="sxs-lookup"><span data-stu-id="1230f-104">This topic contains procedures for the following tasks:</span></span>  
  
-   <span data-ttu-id="1230f-105">建立空的原則新版本</span><span class="sxs-lookup"><span data-stu-id="1230f-105">To create an empty new version of a policy</span></span>  
  
-   <span data-ttu-id="1230f-106">儲存原則版本</span><span class="sxs-lookup"><span data-stu-id="1230f-106">To save a policy version</span></span>  
  
-   <span data-ttu-id="1230f-107">發佈原則版本</span><span class="sxs-lookup"><span data-stu-id="1230f-107">To publish a policy version</span></span>  
  
-   <span data-ttu-id="1230f-108">建立更新的原則版本</span><span class="sxs-lookup"><span data-stu-id="1230f-108">To create an updated version of a policy</span></span>  
  
-   <span data-ttu-id="1230f-109">更新原則以使用更新的組件</span><span class="sxs-lookup"><span data-stu-id="1230f-109">To update a policy to use an updated assembly</span></span>  
  
### <a name="to-create-an-empty-new-version-of-a-policy"></a><span data-ttu-id="1230f-110">建立空的原則新版本</span><span class="sxs-lookup"><span data-stu-id="1230f-110">To create an empty new version of a policy</span></span>  
  
-   <span data-ttu-id="1230f-111">以滑鼠右鍵按一下 [原則] 資料夾，然後按一下**新增版本**。</span><span class="sxs-lookup"><span data-stu-id="1230f-111">Right-click the policy folder, and then click **Add New Version**.</span></span>  
  
### <a name="to-save-a-policy-version"></a><span data-ttu-id="1230f-112">儲存原則版本</span><span class="sxs-lookup"><span data-stu-id="1230f-112">To save a policy version</span></span>  
  
-   <span data-ttu-id="1230f-113">以滑鼠右鍵按一下原則版本，然後**儲存**。</span><span class="sxs-lookup"><span data-stu-id="1230f-113">Right-click the policy version, and then click **Save**.</span></span>  
  
### <a name="to-publish-a-policy-version"></a><span data-ttu-id="1230f-114">發佈原則版本</span><span class="sxs-lookup"><span data-stu-id="1230f-114">To publish a policy version</span></span>  
  
-   <span data-ttu-id="1230f-115">以滑鼠右鍵按一下原則版本，然後**發行**。</span><span class="sxs-lookup"><span data-stu-id="1230f-115">Right-click the policy version, and then click **Publish**.</span></span>  
  
### <a name="to-create-an-updated-version-of-a-policy"></a><span data-ttu-id="1230f-116">建立更新的原則版本</span><span class="sxs-lookup"><span data-stu-id="1230f-116">To create an updated version of a policy</span></span>  
  
1.  <span data-ttu-id="1230f-117">以滑鼠右鍵按一下現有的原則版本，然後按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="1230f-117">Right-click an existing policy version, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="1230f-118">以滑鼠右鍵按一下 [原則] 資料夾，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="1230f-118">Right-click the policy folder, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="1230f-119">具有與複製版本相同項目的新版本已建立。</span><span class="sxs-lookup"><span data-stu-id="1230f-119">A new version is created, with the same elements as the copied version.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1230f-120">若原則使用 .NET 組件且組件已更新，則應該將原則繫結至較新版本的組件。</span><span class="sxs-lookup"><span data-stu-id="1230f-120">If your policy uses a .NET assembly, and the assembly is updated, you should bind your policy to the newer version of the assembly.</span></span>  
  
### <a name="to-update-a-policy-to-use-an-updated-assembly"></a><span data-ttu-id="1230f-121">更新原則以使用更新的組件</span><span class="sxs-lookup"><span data-stu-id="1230f-121">To update a policy to use an updated assembly</span></span>  
  
1.  <span data-ttu-id="1230f-122">按一下**啟動**，指向 **系統管理工具**，指向  **.NET Framework 組態**，然後按一下 **設定的組件**.</span><span class="sxs-lookup"><span data-stu-id="1230f-122">Click **Start**, point to **Administrative Tools**, point to **.NET Framework Configuration**, and then click **Configured Assemblies**.</span></span>  
  
2.  <span data-ttu-id="1230f-123">移至屬性的目標組件，然後按一下**繫結原則** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1230f-123">Go to properties for the target assembly and click the **Binding Policy** tab.</span></span>  
  
3.  <span data-ttu-id="1230f-124">在全域組件快取中，將版本號碼變更為較新的版本。</span><span class="sxs-lookup"><span data-stu-id="1230f-124">In the global assembly cache, change the version number to the newer version.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1230f-125">原則使用的所有組件應該會新增至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="1230f-125">All assemblies used by policies should be added to the global assembly cache.</span></span>