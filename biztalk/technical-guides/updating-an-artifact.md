---
title: 更新成品 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 40feab57-4286-4bdf-8f52-25d02b3fa60c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f32efa6195013d77ee368c0678a9ca67afb4e6e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980039"
---
# <a name="updating-an-artifact"></a><span data-ttu-id="8f0cf-102">更新成品</span><span class="sxs-lookup"><span data-stu-id="8f0cf-102">Updating an Artifact</span></span>
<span data-ttu-id="8f0cf-103">在兩個或多個 BizTalk 應用程式中成品之間的相依性可以有大幅影響應用程式部署和維護。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-103">Dependencies between artifacts in two or more BizTalk applications can have a significant effect on application deployment and maintenance.</span></span> <span data-ttu-id="8f0cf-104">成品相依於另一個需要使用該成品才能正常運作時，例如協調流程，需要使用特定的管線才能正確傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-104">An artifact is dependent on another when it needs to use that artifact in order to function properly, for example an orchestration that needs to use a specific pipeline in order to transmit messages correctly.</span></span>  
  
 <span data-ttu-id="8f0cf-105">若要更新應用程式中的成品，您必須先解除部署，以及依賴它的任何成品。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-105">To update an artifact in an application, you must first undeploy it, along with any artifacts that depend on it.</span></span> <span data-ttu-id="8f0cf-106">當具有相依性的成品存在於相同的應用程式中時，BizTalk Server 會自動針對更新和相依的成品處理解除部署和重新部署工作。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-106">When artifacts that have dependencies exist in the same application, BizTalk Server automatically handles the undeployment and redeployment tasks for the updated and dependent artifacts.</span></span> <span data-ttu-id="8f0cf-107">但是，當具有相依性的成品存在於其他應用程式中時，就不是這個情況。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-107">When artifacts that have dependencies exist in different applications, however, this is not the case.</span></span> <span data-ttu-id="8f0cf-108">如果您想要更新某個應用程式中的成品，另一個應用程式中的成品具有相依性它，您必須解除部署，並重新部署相依的成品，如下所示手動：</span><span class="sxs-lookup"><span data-stu-id="8f0cf-108">If you want to update an artifact in one application, and an artifact in another application has a dependency on it, you must undeploy and redeploy the dependent artifact manually as follows:</span></span>  
  
1. <span data-ttu-id="8f0cf-109">停止、取消登錄和解除繫結此相依成品。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-109">Stop, unenlist, and unbind the dependent artifact.</span></span>  
  
2. <span data-ttu-id="8f0cf-110">更新它所相依的成品。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-110">Update the artifact on which it depends.</span></span>  
  
3. <span data-ttu-id="8f0cf-111">繫結、登錄和啟動此相依成品。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-111">Bind, enlist, and start the dependent artifact.</span></span>  
  
   <span data-ttu-id="8f0cf-112">若要避免需要執行手動步驟來更新其他成品所相依，您可以嘗試要在具有相依性的所有成品都一起在相同的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-112">To avoid the need to perform manual steps to update an artifact on which other artifacts depend, you can try to keep all artifacts with dependencies together in the same application.</span></span> <span data-ttu-id="8f0cf-113">這不一定可行的不過，因為大多數類型的成品必須是唯一的 BizTalk 群組中。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-113">This is not always possible, however, because most types of artifacts must be unique in a BizTalk group.</span></span> <span data-ttu-id="8f0cf-114">您不能在相同群組的兩個不同應用程式中有相同的成品，即使當這兩個應用程式包含的成品相依於相同的成品時，也是如此。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-114">You cannot have the same artifact in two different applications in the same group, even if both applications contain artifacts that depend on the same artifact.</span></span> <span data-ttu-id="8f0cf-115">唯一的成品的問題的相關資訊，請參閱[成品，必須是唯一的應用程式或群組](http://go.microsoft.com/fwlink/?LinkId=155141)(<http://go.microsoft.com/fwlink/?LinkId=155141>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-115">For more information about the issue of unique artifacts, see [Artifacts That Must Be Unique in an Application or Group](http://go.microsoft.com/fwlink/?LinkId=155141) (<http://go.microsoft.com/fwlink/?LinkId=155141>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
   <span data-ttu-id="8f0cf-116">您可以將所需的成品新增至一個應用程式，然後再新增該應用程式中包含相依於它的成品的其他任何應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-116">You can add the needed artifact to one application and then add a reference to that application from any other applications containing artifacts that depend on it.</span></span> <span data-ttu-id="8f0cf-117">當您加入應用程式的參考時，該應用程式中的成品可以使用它所參考之應用程式中的任何成品。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-117">When you add a reference to an application, artifacts in the application can use any artifacts in the application that it references.</span></span> <span data-ttu-id="8f0cf-118">如需新增參考的指示，請參閱[如何加入另一個應用程式的參考](http://go.microsoft.com/fwlink/?LinkID=155011)(<http://go.microsoft.com/fwlink/?LinkID=155011>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-118">For instructions on adding a reference, see [How to Add a Reference to Another Application](http://go.microsoft.com/fwlink/?LinkID=155011) (<http://go.microsoft.com/fwlink/?LinkID=155011>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
   <span data-ttu-id="8f0cf-119">更新成品在 BizTalk 應用程式中的工作的檢查清單，請參閱 <<c0> [ 檢查清單： 更新 BizTalk 應用程式中的成品](http://go.microsoft.com/fwlink/?LinkId=155647)(<http://go.microsoft.com/fwlink/?LinkId=155647>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="8f0cf-119">For a checklist of tasks for updating artifacts in a BizTalk application, see [Checklist: Update the Artifacts in a BizTalk Application](http://go.microsoft.com/fwlink/?LinkId=155647) (<http://go.microsoft.com/fwlink/?LinkId=155647>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f0cf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f0cf-120">See Also</span></span>  
 [<span data-ttu-id="8f0cf-121">更新應用程式和成品</span><span class="sxs-lookup"><span data-stu-id="8f0cf-121">Updating Applications and Artifacts</span></span>](../technical-guides/updating-applications-and-artifacts.md)