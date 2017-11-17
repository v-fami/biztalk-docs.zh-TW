---
title: "如何發佈原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, publishing
- managing [policies], publishing
- publishing, policies
ms.assetid: 730c57a7-526f-40ca-8610-88216558e375
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a64c4764459eecd0d1a4fceedf7a7e8e61159503
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-publish-a-policy"></a><span data-ttu-id="39f0c-102">如何發佈原則</span><span class="sxs-lookup"><span data-stu-id="39f0c-102">How to Publish a Policy</span></span>
<span data-ttu-id="39f0c-103">本主題說明如何使用 BizTalk Server 管理主控台，在 BizTalk 群組中發佈原則。</span><span class="sxs-lookup"><span data-stu-id="39f0c-103">This topic describes how to use the BizTalk Server Administration console to publish a policy in a BizTalk group.</span></span> <span data-ttu-id="39f0c-104">發佈原則使其可新增至 BizTalk 應用程式中所述[如何新增原則至應用程式](../core/how-to-add-a-policy-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="39f0c-104">Publishing a policy makes it available to add to a BizTalk application, as described in [How to Add a Policy to an Application](../core/how-to-add-a-policy-to-an-application.md).</span></span>  
  
 <span data-ttu-id="39f0c-105">在發佈原則之前，該原則必須存在於 BizTalk 群組的「規則引擎資料庫」中。</span><span class="sxs-lookup"><span data-stu-id="39f0c-105">Before you can publish a policy, it must exist in the Rule Engine database for the BizTalk group.</span></span> <span data-ttu-id="39f0c-106">有三個方式可將原則匯入「規則引擎資料庫」：</span><span class="sxs-lookup"><span data-stu-id="39f0c-106">There are three ways to import a policy into the Rule Engine database:</span></span>  
  
-   <span data-ttu-id="39f0c-107">您可以匯入包含原則的應用程式。</span><span class="sxs-lookup"><span data-stu-id="39f0c-107">You can import an application that contains a policy.</span></span> <span data-ttu-id="39f0c-108">完成時就會將原則自動匯入「規則引擎資料庫」。</span><span class="sxs-lookup"><span data-stu-id="39f0c-108">When you do this, the policy is automatically imported into the Rule Engine database.</span></span>  
  
-   <span data-ttu-id="39f0c-109">您可以明確地原則匯入到 「 規則引擎 」 資料庫使用管理主控台或 BTSTask 中, 所述[如何匯入原則](../core/how-to-import-a-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="39f0c-109">You can explicitly import a policy into the Rule Engine database by using the administration console or BTSTask, as described in [How to Import a Policy](../core/how-to-import-a-policy.md).</span></span>  
  
-   <span data-ttu-id="39f0c-110">您可以將原則加入至 「 規則引擎 」 資料庫使用 「 規則引擎部署精靈 」 中所述[如何部署和解除部署原則和詞彙](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)。</span><span class="sxs-lookup"><span data-stu-id="39f0c-110">You can add a policy to the Rule Engine database by using the Rule Engine Deployment Wizard, as described in [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39f0c-111">雖然已發佈的原則可由另一個匯入的原則覆寫，但若指定這個選項，將無法覆寫已發佈的詞彙。</span><span class="sxs-lookup"><span data-stu-id="39f0c-111">While a published policy can be overwritten by another policy that you import, should you specify this option, a published vocabulary can never be overwritten.</span></span> <span data-ttu-id="39f0c-112">若要更新已發佈的詞彙，您必須將它從「規則引擎資料庫」移除，然後匯入新版本。</span><span class="sxs-lookup"><span data-stu-id="39f0c-112">To update a published vocabulary, you must remove it from the Rule Engine database and then import the new version.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="39f0c-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="39f0c-113">Prerequisites</span></span>  
 <span data-ttu-id="39f0c-114">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="39f0c-114">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="39f0c-115">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="39f0c-115">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-publish-a-policy"></a><span data-ttu-id="39f0c-116">若要發佈原則</span><span class="sxs-lookup"><span data-stu-id="39f0c-116">To publish a policy</span></span>  
  
1.  <span data-ttu-id="39f0c-117">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="39f0c-117">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="39f0c-118">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開 BizTalk 群組包含原則發佈，請展開**應用程式**，然後展開**\<所有成品 >**。</span><span class="sxs-lookup"><span data-stu-id="39f0c-118">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the policy to publish, expand **Applications**, and then expand **\<All Artifacts>**.</span></span>  
  
3.  <span data-ttu-id="39f0c-119">按一下**原則**，以滑鼠右鍵按一下原則，然後按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="39f0c-119">Click **Policies**, right-click the policy, and then click **Publish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="39f0c-120">若要發佈原則，原則所參考的任何組件必須安裝在全域組件快取 (GAC) 的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦然後再開啟**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="39f0c-120">In order to publish a policy, any assemblies that are referenced by the policy must be installed in the Global Assembly Cache (GAC) of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer before you open **BizTalk Server Administration**.</span></span> <span data-ttu-id="39f0c-121">當**BizTalk Server 管理**已開啟，它會維護安裝至 GAC 的組件快取。</span><span class="sxs-lookup"><span data-stu-id="39f0c-121">When **BizTalk Server Administration** is opened, it maintains a cache of the assemblies that are installed into the GAC.</span></span> <span data-ttu-id="39f0c-122">此快取才會更新**BizTalk Server 管理**已關閉並重新開啟。</span><span class="sxs-lookup"><span data-stu-id="39f0c-122">This cache is not updated until **BizTalk Server Administration** is closed and reopened.</span></span> <span data-ttu-id="39f0c-123">如果您嘗試發佈原則，而且發行集失敗，因為參考的組件未安裝在 GAC，您必須先關閉**BizTalk Server 管理**，參考的組件安裝到 GAC 中，開啟**BizTalk Server 管理**，然後發佈原則。</span><span class="sxs-lookup"><span data-stu-id="39f0c-123">If you attempt to publish a policy and publication fails because a referenced assembly is not installed in the GAC you must close **BizTalk Server Administration**, install the referenced assembly into the GAC, open **BizTalk Server Administration**, and then publish the policy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f0c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39f0c-124">See Also</span></span>  
 [<span data-ttu-id="39f0c-125">管理原則</span><span class="sxs-lookup"><span data-stu-id="39f0c-125">Managing Policies</span></span>](../core/managing-policies.md)