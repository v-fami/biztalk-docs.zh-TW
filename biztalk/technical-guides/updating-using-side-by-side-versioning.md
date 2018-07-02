---
title: 更新使用並排顯示版本設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9721a091-98ec-4f0b-ad1f-6ca184956e7c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36be63c9cef6a016ea4ad34d98a2750be86491d5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974255"
---
# <a name="updating-using-side-by-side-versioning"></a><span data-ttu-id="72fa0-102">使用並排顯示的版本控制更新</span><span class="sxs-lookup"><span data-stu-id="72fa0-102">Updating Using Side-by-Side Versioning</span></span>
<span data-ttu-id="72fa0-103">如果您不能以排定停機時間，或有非常長時間執行的協調流程執行個體無法終止，可能必須使用--並存版本控制。</span><span class="sxs-lookup"><span data-stu-id="72fa0-103">If you are not able to schedule downtime, or have very long-running orchestration instances that cannot be terminated, side-by-side versioning may be required.</span></span> <span data-ttu-id="72fa0-104">在這種升級，相同的應用程式或應用程式成品的兩個版本會執行並排顯示。</span><span class="sxs-lookup"><span data-stu-id="72fa0-104">In this type of upgrade, two versions of the same application or application artifacts run side-by-side.</span></span> <span data-ttu-id="72fa0-105">.NET 執行階段原本就是可以相同名稱但不同版本的組件，以部署且正在執行，以及 BizTalk Server 也允許它。</span><span class="sxs-lookup"><span data-stu-id="72fa0-105">The .NET runtime inherently allows for same-named but differently versioned assemblies to be deployed and running, and BizTalk Server also allows it.</span></span>  
  
 <span data-ttu-id="72fa0-106">並排顯示的應用程式的版本控制時，您想要推出的主要應用程式升級以累加的方式，例如將它提供給商務合作夥伴的子集一開始，而不是所有合作夥伴一次。</span><span class="sxs-lookup"><span data-stu-id="72fa0-106">Side-by-side versioning of applications is useful when you want to roll out a major application upgrade incrementally, for example making it available to a subset of business partners initially, rather than to all partners at once.</span></span> <span data-ttu-id="72fa0-107">使用這種方式，可讓您繼續執行現有的應用程式來服務尚未使用新版本的使用者，直到您準備好完全轉入新版本為止。</span><span class="sxs-lookup"><span data-stu-id="72fa0-107">Using this approach allows you to continue running the existing application to service the users who are not yet using the new version until you are ready to completely cut over to the new version.</span></span>  
  
 <span data-ttu-id="72fa0-108">與建立組件版本不同，您並非以遞增版本號碼的方式建立應用程式版本。</span><span class="sxs-lookup"><span data-stu-id="72fa0-108">You do not create application versions in the same manner that you create assembly versions, by incrementing the version number.</span></span> <span data-ttu-id="72fa0-109">相反地，您會建立新的應用程式具有不同的名稱，從原始的應用程式，並填入應用程式成品的新版本。</span><span class="sxs-lookup"><span data-stu-id="72fa0-109">Instead, you create a new application that has a different name from the original application, and populate it with the new versions of the application artifacts.</span></span>  
  
 <span data-ttu-id="72fa0-110">因為有許多類型的成品 (例如，組件) 只能存在於 BizTalk 群組中的一個應用程式，所以您必須遞增已存在於群組內之任何組件的版本號碼，才可以將它們部署到新的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="72fa0-110">Because many types of artifacts, such as assemblies, can exist in only one application in a BizTalk group, you must increment the version number of any assemblies that already exist in the group before you can deploy them into the new application.</span></span>  
  
 <span data-ttu-id="72fa0-111">如需逐步更新應用程式或使用並排顯示版本設定的協調流程所需的工作，請參閱[檢查清單： 更新應用程式使用的並存版本控制](../technical-guides/checklist-updating-an-application-using-side-by-side-versioning.md)和[檢查清單： 更新使用並排顯示版本設定的協調流程](../technical-guides/checklist-updating-an-orchestration-using-side-by-side-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="72fa0-111">For a step-by-step list of tasks required to update an application or orchestration using side-by-side versioning, see [Checklist: Updating an Application Using Side-by-Side Versioning](../technical-guides/checklist-updating-an-application-using-side-by-side-versioning.md) and [Checklist: Updating an Orchestration Using Side-by-Side Versioning](../technical-guides/checklist-updating-an-orchestration-using-side-by-side-versioning.md).</span></span> <span data-ttu-id="72fa0-112">如需如何以並排顯示部署的應用程式的詳細指示，請參閱 「[如何部署執行的並行應用程式與現有版本的新版本](http://go.microsoft.com/fwlink/?LinkId=155143)(<http://go.microsoft.com/fwlink/?LinkId=155143>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="72fa0-112">For detailed instructions on how to have side-by-side deployment of applications, see "[How to Deploy a New Version of an Application to Run Side-by-side with an Existing Version](http://go.microsoft.com/fwlink/?LinkId=155143) (<http://go.microsoft.com/fwlink/?LinkId=155143>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72fa0-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="72fa0-113">In This Section</span></span>  
  
-   [<span data-ttu-id="72fa0-114">如何使用並存版本控制更新對應</span><span class="sxs-lookup"><span data-stu-id="72fa0-114">How to Update a Map Using Side-by-Side Versioning</span></span>](../technical-guides/how-to-update-a-map-using-side-by-side-versioning.md)  
  
-   [<span data-ttu-id="72fa0-115">如何使用並存版本控制更新管道</span><span class="sxs-lookup"><span data-stu-id="72fa0-115">How to Update a Pipeline Using Side-by-Side Versioning</span></span>](../technical-guides/how-to-update-a-pipeline-using-side-by-side-versioning.md)  
  
-   [<span data-ttu-id="72fa0-116">使用並存版本控制更新結構描述</span><span class="sxs-lookup"><span data-stu-id="72fa0-116">Updating a Schema Using Side-by-Side Versioning</span></span>](../technical-guides/updating-a-schema-using-side-by-side-versioning.md)