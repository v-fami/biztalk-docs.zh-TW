---
title: 版本控制商務程序管理解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- versioning, process management solutions
- process management solution tutorial, modifying
- process management solution tutorial, versioning
- processing, stages
- process management solution tutorial, processing stages
ms.assetid: 501b2162-821f-44e1-87c0-8628cc5bd9c3
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af8afd3666a35b827ff25b243c1bfb4c81262273
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288646"
---
# <a name="versioning-the-business-process-management-solution"></a><span data-ttu-id="7d1c9-102">版本控制商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="7d1c9-102">Versioning the Business Process Management Solution</span></span>
<span data-ttu-id="7d1c9-103">商務程序管理解決方案的設計目的是讓您可在需要時取代階段。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-103">The Business Process Management solution is designed so that you can replace stages if necessary.</span></span> <span data-ttu-id="7d1c9-104">此設計也提供更容易管理結構描述版本的方法。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-104">The design also provides for an easier method of versioning schemas.</span></span>  
  
 <span data-ttu-id="7d1c9-105">如需將商務程序分成階段資訊，請參閱[商務程序管理解決方案中的部分設計原則](../core/some-design-principles-in-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-105">For information about dividing a business process into stages, see [Some Design Principles in the Business Process Management Solution](../core/some-design-principles-in-the-business-process-management-solution.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d1c9-106">解決方案的項目會與訊息結構高度相依。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-106">Elements of the solution are highly dependent on the message structures.</span></span> <span data-ttu-id="7d1c9-107">變更訊息結構需要大幅變更協調流程。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-107">Changing message structures requires substantial changes to the orchestrations.</span></span>  
  
 <span data-ttu-id="7d1c9-108">如需有關更新中已部署的方案和編寫指令碼的指導方針來處理更新的組件的一般指示，請參閱[更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-108">For general directions about updating assemblies in a deployed solution and guidelines for writing scripts to handle the update, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md).</span></span>  
  
## <a name="adding-replacing-or-removing-stages"></a><span data-ttu-id="7d1c9-109">新增、取代或移除階段</span><span class="sxs-lookup"><span data-stu-id="7d1c9-109">Adding, Replacing, or Removing Stages</span></span>  
 <span data-ttu-id="7d1c9-110">訂單處理階段協調流程包含兩種類型的程式碼： 實作商務程序和提供的基礎結構，讓它可以在方案中運作的程式碼的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-110">The order processing stage orchestrations contain two kinds of code: code that implements the business process and code that provides the infrastructure so that it can operate in the solution.</span></span> <span data-ttu-id="7d1c9-111">在這兩個階段協調流程**CableOrder1**和**CableOrder2**，商務程序程式碼會在 「 群組 」 圖形內標示為 「 商務處理 」。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-111">In both of the stage orchestrations, **CableOrder1** and **CableOrder2**, the business process code is inside a group shape labeled "Business Processing."</span></span>  
  
 <span data-ttu-id="7d1c9-112">最容易建立新階段的方法是複製其中一個階段，以您的程式碼取代「商務處理」群組中的程式碼，並使基礎結構程式碼保持不變。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-112">The easiest way to create a new stage is to copy one of the stages, replace the code in the "Business Processing" group with your code, and leave the infrastructure code intact.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d1c9-113">**CableOrder2**協調流程有兩個 「 商務處理 」 群組，第二個 「 更新歷程記錄傳送 」 圖形周圍。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-113">The **CableOrder2** orchestration has two "Business Processing" groups, the second around the Update History Send shape.</span></span> <span data-ttu-id="7d1c9-114">「傳送」圖形是有效傳送範圍的一部分。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-114">The Send shape is part of an efficient send scope.</span></span> <span data-ttu-id="7d1c9-115">(如需詳細資訊，請參閱 < 改善效能與巢狀範圍 」 中的[OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)。)由於「群組」圖形無法與範圍圖形的一部分重疊，因此會標示第二個群組，以指出它是商務程序程式碼的一部分。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-115">(For more information, see "Improving Performance with Nested Scopes" in [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md).) Because a Group shape cannot overlap part of a scope shape, the second group is labeled to indicate it is part of the business process code.</span></span>  
  
 <span data-ttu-id="7d1c9-116">您必須將新協調流程上的篩選條件運算式設定成它在順序中的號碼。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-116">You must set the filter expression on the new orchestration to its number in the sequence.</span></span> <span data-ttu-id="7d1c9-117">**OrderManager**假設階段號碼以 1 開始，並增加一個 （1、 2、 3 …） 的每個下列階段。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-117">The **OrderManager** assumes stage numbers begin with one and increase by one for each following stage (1, 2, 3 …).</span></span> <span data-ttu-id="7d1c9-118">若要篩選第三個階段，您需要將篩選條件運算式設定如下：</span><span class="sxs-lookup"><span data-stu-id="7d1c9-118">To filter for a third stage, you would set the filter expression to the following:</span></span>  
  
 `(Microsoft.Samples.BizTalk.SouthridgeVidoe.Schemas.Stage == 3)`  
  
 <span data-ttu-id="7d1c9-119">解決方案會使用 BAM API 來追蹤解決方案中的事件，包括訂單處理階段。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-119">The solution uses the BAM API to track events in the solution, including the order processing stages.</span></span> <span data-ttu-id="7d1c9-120">第一個階段會啟動 BAM 活動，最後一個階段會結束它。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-120">The first stage starts the BAM activity; the final stage ends it.</span></span> <span data-ttu-id="7d1c9-121">若有例外狀況，解決方案中的處理常式會結束相關的 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-121">If there exceptions, the handlers in the solution end the BAM activities involved.</span></span> <span data-ttu-id="7d1c9-122">BAM 會將不連續的作業有效地重新組合成連續的檢視以進行監控。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-122">BAM effectively re-assembles the discontinuous operations into a continuous view for monitoring.</span></span>  
  
## <a name="changing-configuration"></a><span data-ttu-id="7d1c9-123">變更組態</span><span class="sxs-lookup"><span data-stu-id="7d1c9-123">Changing Configuration</span></span>  
 <span data-ttu-id="7d1c9-124">若您的變更會增加或減少階段數目，則必須變更儲存在「企業單一登入」(SSO) 密碼存放區中的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-124">If your changes increase or decrease the number of stages, you must change the configuration information stored in the Enterprise Single Sign-On (SSO) secret store.</span></span>  
  
 <span data-ttu-id="7d1c9-125">如果您尚未部署應用程式，您可以修改的組態設定**TotalStages** CreateSouthridgeVideoApplication.cmd 指令碼檔案中。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-125">If you haven't deployed the application, you can modify the configuration setting for **TotalStages** in the CreateSouthridgeVideoApplication.cmd script file.</span></span> <span data-ttu-id="7d1c9-126">當指令碼於部署期間執行時，值將會變更。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-126">The value will change when the script is run during deployment.</span></span>  
  
 <span data-ttu-id="7d1c9-127">若您已部署應用程式，則可以執行 SDK\Common\SsoApplicationConfig 資料夾中的命令列公用程式 BTSScnSSOApplicationConfig 以變更值。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-127">If you have already deployed the application, you can change value by running a command line utility, BTSScnSSOApplicationConfig, in the SDK\Common\SsoApplicationConfig folder.</span></span> <span data-ttu-id="7d1c9-128">若要將階段總數設定為 3，需要使用下列的命令列：</span><span class="sxs-lookup"><span data-stu-id="7d1c9-128">To set the total number of stages to three, you'd use the following command line:</span></span>  
  
 `BTSScnSSOApplicationConfig -set SouthRidgeVideo.CableOrder ConfigProperties TotalStages 3`  
  
 <span data-ttu-id="7d1c9-129">因為解決方案會快取組態值，所以您必須等到重新整理間隔過去，新值才會生效。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-129">Because the solution caches the configuration values, you must wait until the  refresh interval passes for the new value to take effect.</span></span>  
  
## <a name="versioning-schemas"></a><span data-ttu-id="7d1c9-130">管理結構描述版本</span><span class="sxs-lookup"><span data-stu-id="7d1c9-130">Versioning Schemas</span></span>  
 <span data-ttu-id="7d1c9-131">BizTalk 會從最新版本包含它的組件的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-131">BizTalk takes a schema from the most recent version of the assembly containing it.</span></span> <span data-ttu-id="7d1c9-132">這表示若您建立結構描述的新版本，則它會完全取代結構描述的所有先前版本。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-132">This means that if you create a new version of a schema it completely replaces all previous versions of the schema.</span></span> <span data-ttu-id="7d1c9-133">這在交易期間很短時是可行的。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-133">This works well when transactions are short-lived.</span></span> <span data-ttu-id="7d1c9-134">不過，在商務程序管理解決方案中的交易期間較長： 訂單可能需要一年才能完成。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-134">However, transactions in the Business Process Management solution are long-lived: an order may take up to a year to complete.</span></span>  
  
 <span data-ttu-id="7d1c9-135">為了同時使用某個結構描述的多個版本，解決方案中的每個結構描述會在其命名空間中包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-135">To allow for the possibility of using multiple versions of a schema being in use, each schema in the solution includes a version number in its namespace.</span></span> <span data-ttu-id="7d1c9-136">例如，Order 結構描述的命名空間如下所示：</span><span class="sxs-lookup"><span data-stu-id="7d1c9-136">For example, the namespace for the Order schema is as follows:</span></span>  
  
```  
http://Microsoft.Samples.BizTalk.SouthridgeVideo.Schemas.Order.v1  
```  
  
 <span data-ttu-id="7d1c9-137">因為命名空間會識別結構描述，而且版本號碼的包含使得命名空間在結構描述中是唯一，所以新結構描述將可與較舊的版本區別。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-137">Because the namespace identifies the schema and inclusion of the version number makes the namespace unique to the schema, the new schema will be distinct from the older version.</span></span> <span data-ttu-id="7d1c9-138">因此，可以不取代舊的結構描述，即可使用新的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7d1c9-138">Thus, a new schema can be used without supplanting the old schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1c9-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d1c9-139">See Also</span></span>  
 [<span data-ttu-id="7d1c9-140">開發商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="7d1c9-140">Developing a Business Process Management Solution</span></span>](../core/developing-a-business-process-management-solution.md)