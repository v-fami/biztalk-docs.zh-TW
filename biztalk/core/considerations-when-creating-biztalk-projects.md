---
title: "建立 BizTalk 專案時的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, size
- map type name
- projects, naming conventions
- projects, planning
ms.assetid: f6c3dc71-105f-46af-9e6e-9a4c3b982d8c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e9d05e07465d834f587f79d50f04bec18a89506
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-creating-biztalk-projects"></a><span data-ttu-id="be60d-102">建立 BizTalk 專案時的考量</span><span class="sxs-lookup"><span data-stu-id="be60d-102">Considerations When Creating BizTalk Projects</span></span>
<span data-ttu-id="be60d-103">本節提供使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立 BizTalk 專案時應考量的資訊。</span><span class="sxs-lookup"><span data-stu-id="be60d-103">This section provides information that you should take into consideration when creating BizTalk projects using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="avoid-compilation-errors-caused-by-projects-that-are-too-large"></a><span data-ttu-id="be60d-104">避免專案太大所造成的編譯錯誤</span><span class="sxs-lookup"><span data-stu-id="be60d-104">Avoid compilation errors caused by projects that are too large</span></span>  
 <span data-ttu-id="be60d-105">若專案產生一個大於 75MB 的組件，則 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 編譯器無法成功編譯專案。</span><span class="sxs-lookup"><span data-stu-id="be60d-105">The [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] compiler will not successfully compile a project if it would result in an assembly larger than 75 megabytes.</span></span> <span data-ttu-id="be60d-106">當編譯器到達大小限制，它就會發出嚴重錯誤 CS0013 「 中繼資料寫入檔案非預期的錯誤\<檔名 >"暫止。</span><span class="sxs-lookup"><span data-stu-id="be60d-106">When the compiler reaches a size constraint it will emit fatal error CS0013 "Unexpected error writing metadata to file \<filename>" and halt.</span></span>  
  
 <span data-ttu-id="be60d-107">若要避免此問題，建議您，除非絕對必要，否則專案不要超過 10MB。</span><span class="sxs-lookup"><span data-stu-id="be60d-107">To avoid this problem, we recommend that projects not exceed 10 megabytes unless absolutely necessary.</span></span> <span data-ttu-id="be60d-108">為什麼？</span><span class="sxs-lookup"><span data-stu-id="be60d-108">Why?</span></span>  
  
-   <span data-ttu-id="be60d-109">較小的專案比較容易部署，因為其中的部署步驟較少。</span><span class="sxs-lookup"><span data-stu-id="be60d-109">Smaller projects are potentially simpler to deploy because there are fewer deployment steps.</span></span> <span data-ttu-id="be60d-110">專案愈小，其步驟更有可能緊密相關 -- 管理交易夥伴折扣或處理 RFP。</span><span class="sxs-lookup"><span data-stu-id="be60d-110">And with smaller projects the steps are more likely to be closely related -- managing trading partner discounts or handling RFPs.</span></span>  
  
-   <span data-ttu-id="be60d-111">使用較小的專案比較容易隔離錯誤、部署問題以及其他問題。</span><span class="sxs-lookup"><span data-stu-id="be60d-111">It is easier to isolate bugs, deployment issues, and other problems when using smaller projects.</span></span> <span data-ttu-id="be60d-112">在具有 140 個結構描述與許多自訂對應及指令碼的專案中尋找錯誤，比在只具有 10 個結構描述與少數自訂對應及指令碼的專案中尋找錯誤更為困難。</span><span class="sxs-lookup"><span data-stu-id="be60d-112">Finding a bug in a project with 140 schemas and many custom maps and scripts will be more difficult than finding one in a project with only 10 schemas and a few custom maps and scripts.</span></span>  
  
-   <span data-ttu-id="be60d-113">將大型專案分隔成較小的專案可降低複雜性。</span><span class="sxs-lookup"><span data-stu-id="be60d-113">Separating a large project into smaller projects can reduce complexity.</span></span> <span data-ttu-id="be60d-114">較小的專案較易於管理。</span><span class="sxs-lookup"><span data-stu-id="be60d-114">The smaller projects are more manageable.</span></span>  
  
-   <span data-ttu-id="be60d-115">較小的專案編譯較快速。</span><span class="sxs-lookup"><span data-stu-id="be60d-115">Smaller projects compile faster.</span></span>  
  
-   <span data-ttu-id="be60d-116">將具有許多不相關結構描述的大型專案分割成具有強烈相關結構描述的較小型專案可產生更好的效能。</span><span class="sxs-lookup"><span data-stu-id="be60d-116">Splitting a large project with many unrelated schemas into smaller projects with strongly related schemas may result in better performance.</span></span> <span data-ttu-id="be60d-117">這是因為每次僅載入其中一些組件。</span><span class="sxs-lookup"><span data-stu-id="be60d-117">This is because only some of the assemblies will be loaded at a time.</span></span>  
  
## <a name="avoid-using-the-project-name-as-the-map-type-name"></a><span data-ttu-id="be60d-118">避免使用專案名稱作為對應類型名稱</span><span class="sxs-lookup"><span data-stu-id="be60d-118">Avoid using the Project Name as the Map Type Name</span></span>  
 <span data-ttu-id="be60d-119">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 新增對應到 BizTalk 專案時，請勿使用專案名稱做為類型名稱。</span><span class="sxs-lookup"><span data-stu-id="be60d-119">When adding a new map to a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] do not use the project name as the type name.</span></span> <span data-ttu-id="be60d-120">如果您這樣做，編譯器會產生類似的一或多個錯誤 」 的型別名稱\<名稱 >' 不存在於型別 」。</span><span class="sxs-lookup"><span data-stu-id="be60d-120">If you do, the compiler will generate one or more errors similar to "The type name \<name>' does not exist in the type".</span></span>  
  
 <span data-ttu-id="be60d-121">若要在 BizTalk 專案中變更對應的類型名稱，按一下 [方案總管] 窗格中的對應，然後在 [屬性] 窗格中查驗類型名稱屬性。</span><span class="sxs-lookup"><span data-stu-id="be60d-121">To change the type name for a map from within a BizTalk project, click the map in the Solution Explorer pane, then verify the type name property in the Properties pane.</span></span> <span data-ttu-id="be60d-122">若是相同，則需要加以修改，確定變更所有依賴它的組態。</span><span class="sxs-lookup"><span data-stu-id="be60d-122">If it is the same, you need to modify it making sure to change any configurations that rely on it.</span></span>  
  
## <a name="visual-studio-team-system-support"></a><span data-ttu-id="be60d-123">Visual Studio Team System 支援</span><span class="sxs-lookup"><span data-stu-id="be60d-123">Visual Studio Team System Support</span></span>  
 <span data-ttu-id="be60d-124">中的 BizTalk 專案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]不是直接執行支援的所有功能[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]Team System。</span><span class="sxs-lookup"><span data-stu-id="be60d-124">BizTalk projects in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] do not directly support all features of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Team System.</span></span> <span data-ttu-id="be60d-125">[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 支援 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Team System 的原始檔控制功能。</span><span class="sxs-lookup"><span data-stu-id="be60d-125">The source control features of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Team System are supported for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span> <span data-ttu-id="be60d-126">Visual SourceSafe 亦完全支援 BizTalk 專案成品的追蹤和版本管理。</span><span class="sxs-lookup"><span data-stu-id="be60d-126">Visual SourceSafe is also fully supported for the tracking and versioning of BizTalk project artifacts.</span></span>