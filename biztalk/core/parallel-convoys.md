---
title: "平行群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Parallel Task shape [Orchestration Designer], concurrent receive tasks
- messages, convoys
- correlation sets, concurrent receive tasks
- correlation sets, Parallel Task shape [Orchestration Designer]
- orchestrations, messages
- messages, correlating to orchestrations
ms.assetid: 036aa8c0-f49c-47f0-ac1e-6c667bca3811
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c6993aa3c5dd47cb5b554dd8ab2080020ebb80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="parallel-convoys"></a><span data-ttu-id="7ec18-102">平行群組</span><span class="sxs-lookup"><span data-stu-id="7ec18-102">Parallel Convoys</span></span>
<span data-ttu-id="7ec18-103">平行群組可讓多個單一訊息聯結在一起，以達成所需的結果。</span><span class="sxs-lookup"><span data-stu-id="7ec18-103">A parallel convoy enables multiple single messages to join together to achieve a required result.</span></span> <span data-ttu-id="7ec18-104">一組相關的訊息會依任何順序抵達，但 BizTalk Server 必須收到所有的訊息，才能開始處理。</span><span class="sxs-lookup"><span data-stu-id="7ec18-104">The set of related messages can arrive in any order, but BizTalk Server must receive all of them before starting the process.</span></span>  
  
 <span data-ttu-id="7ec18-105">例如，當醫院接受新病患時，醫院會要求病患提供多項資訊，包括保險資訊、過去就醫記錄和連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="7ec18-105">For example, when a hospital admits a new patient, the hospital requires several pieces of information from the patient, including insurance information, past medical history, and contact information.</span></span> <span data-ttu-id="7ec18-106">有幾種不同的人會收集此資訊，包括保險專員、護士和服務台人員。</span><span class="sxs-lookup"><span data-stu-id="7ec18-106">Several different people collect this information, including an insurance specialist, a nurse, and a receptionist.</span></span> <span data-ttu-id="7ec18-107">有數個不同系統會處理此資訊。</span><span class="sxs-lookup"><span data-stu-id="7ec18-107">Several different systems process this information.</span></span> <span data-ttu-id="7ec18-108">收集和提交此資訊的工作不保證一定會按照正常的順序進行。</span><span class="sxs-lookup"><span data-stu-id="7ec18-108">The order in which collection and submission of this information occurs is not guaranteed.</span></span> <span data-ttu-id="7ec18-109">例如，資訊收集者可能忙著招呼其他病患、醫療記錄部門的動作可能落後預定時間，或者保險系統可能運作不正常。</span><span class="sxs-lookup"><span data-stu-id="7ec18-109">For example, information collectors may be busy with other patients, the medical records department may be behind in their schedule, or the insurance system may not be functioning correctly.</span></span> <span data-ttu-id="7ec18-110">我們必須在病患的就醫期間內，有系統地組織病患的這些資訊。</span><span class="sxs-lookup"><span data-stu-id="7ec18-110">Assembling this information for the patient in an organized manner must occur throughout the time the patient spends at the hospital.</span></span> <span data-ttu-id="7ec18-111">如此才能保證病患受到妥善的醫療照顧，而且收到正確的帳單。</span><span class="sxs-lookup"><span data-stu-id="7ec18-111">This guarantees that the patient receives appropriate care and accurate billing.</span></span>  
  
 <span data-ttu-id="7ec18-112">上述的案例便是需要平行群組訊息處理的商務案例。</span><span class="sxs-lookup"><span data-stu-id="7ec18-112">The preceding scenario is an example of a business scenario that requires parallel convoy message processing.</span></span> <span data-ttu-id="7ec18-113">商務需求會衍生出一種規定，迫使醫院必須在收到三種不同訊息之後，才接受病患。</span><span class="sxs-lookup"><span data-stu-id="7ec18-113">The business requirements dictate the receipt of three different types of messages before admitting the patient into the hospital.</span></span> <span data-ttu-id="7ec18-114">這三種訊息即是「保險」、「病歷」和「病患」訊息。</span><span class="sxs-lookup"><span data-stu-id="7ec18-114">These three messages are the Insurance, History, and Patient messages.</span></span> <span data-ttu-id="7ec18-115">這些屬於病患的任何一則訊息都可能是最先抵達的訊息，因此會產生競爭條件。</span><span class="sxs-lookup"><span data-stu-id="7ec18-115">Any one of these messages can be the first message to arrive for the patient, and this creates a race condition.</span></span> <span data-ttu-id="7ec18-116">若要解決這個問題，請三個**接收**圖形放進**平行動作**形狀和每個接收標示為 Activate = True。</span><span class="sxs-lookup"><span data-stu-id="7ec18-116">To resolve this issue, three **Receive** shapes are put into a **Parallel Actions** shape and each receive is marked as Activate = True.</span></span> <span data-ttu-id="7ec18-117">這讓三個訊息中的任何一個都可以啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="7ec18-117">This enables any one of the three messages to start the orchestration.</span></span> <span data-ttu-id="7ec18-118">協調流程執行個體會等到另外兩個訊息抵達之後，再繼續執行進一步的處理。</span><span class="sxs-lookup"><span data-stu-id="7ec18-118">The orchestration instance waits until the other two messages arrive before proceeding to further processing.</span></span>  
  
## <a name="implementing-parallel-convoys"></a><span data-ttu-id="7ec18-119">實作平行群組</span><span class="sxs-lookup"><span data-stu-id="7ec18-119">Implementing Parallel Convoys</span></span>  
 <span data-ttu-id="7ec18-120">您可以使用 BizTalk Server 中的「平行相互關聯的接收」傳訊設計模式來實作平行群組。</span><span class="sxs-lookup"><span data-stu-id="7ec18-120">You can implement parallel convoys by using the "parallel correlated receives" messaging design pattern in BizTalk Server.</span></span> <span data-ttu-id="7ec18-121">平行相互關聯接收相互關聯接收陳述式中的兩個或多個分支**平行動作**圖形。</span><span class="sxs-lookup"><span data-stu-id="7ec18-121">Parallel correlated receives are correlated receive statements in two or more branches of a **Parallel Actions** shape.</span></span> <span data-ttu-id="7ec18-122">如果會在一項以上的平行工作中初始化相互關聯，則每個相互關聯接收也必須初始化一組完全相同的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7ec18-122">If a correlation is initialized in more than one parallel task, each correlated receive must initialize exactly the same set of correlations.</span></span> <span data-ttu-id="7ec18-123">這項工作會接收相互關聯的訊息會先執行實際的初始化、 和中的其他工作上執行驗證**平行動作**協調流程中的圖形。</span><span class="sxs-lookup"><span data-stu-id="7ec18-123">The first such task that receives a correlated message performs the actual initialization, and validation is performed on the other tasks in the **Parallel Actions** shape in orchestration.</span></span>  
  
 <span data-ttu-id="7ec18-124">平行群組實作的範例，請參閱 SDK 範例 「 平行群組 」，在[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="7ec18-124">For an example of parallel convoy implementation, see the SDK sample "Parallel Convoy" at [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec18-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ec18-125">See Also</span></span>  
 <span data-ttu-id="7ec18-126">[使用群組實例](../core/working-with-convoy-scenarios.md) </span><span class="sxs-lookup"><span data-stu-id="7ec18-126">[Working with Convoy Scenarios](../core/working-with-convoy-scenarios.md) </span></span>  
 [<span data-ttu-id="7ec18-127">循序群組</span><span class="sxs-lookup"><span data-stu-id="7ec18-127">Sequential Convoys</span></span>](../core/sequential-convoys.md)