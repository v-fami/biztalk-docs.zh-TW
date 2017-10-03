---
title: "如何部署或解除部署原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [policies], undeploying
- deploying, policies
- policies, deploying
- managing [policies], deploying
- policies, undeploying
- undeploying, policies
ms.assetid: 9d26d4fe-9673-4baa-9927-02efda56b7a4
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4913dbfa6f3d027d5540234b5af9370eb69f67a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-or-undeploy-a-policy"></a><span data-ttu-id="02ae2-102">如何部署或解除部署原則</span><span class="sxs-lookup"><span data-stu-id="02ae2-102">How to Deploy or Undeploy a Policy</span></span>
<span data-ttu-id="02ae2-103">本主題描述如何使用 [BizTalk Server 管理] 主控台，以手動方式部署或解除部署原則。</span><span class="sxs-lookup"><span data-stu-id="02ae2-103">This topic describes how to use the BizTalk Server Administration console to deploy or undeploy a policy manually.</span></span> <span data-ttu-id="02ae2-104">此外，啟動應用程式會自動部署它所包含的原則，而停止應用程式則會自動解除部署它的原則。</span><span class="sxs-lookup"><span data-stu-id="02ae2-104">In addition, starting an application automatically deploys any policies it contains, and stopping an application automatically undeploys its policies.</span></span> <span data-ttu-id="02ae2-105">部署原則會在使用它的應用程式中生效；</span><span class="sxs-lookup"><span data-stu-id="02ae2-105">Deploying a policy puts it into effect in the application that uses it.</span></span> <span data-ttu-id="02ae2-106">解除部署原則會讓它成為非使用中，所以此原則在 BizTalk 群組中使用它的任何應用程式內都不再有任何作用。</span><span class="sxs-lookup"><span data-stu-id="02ae2-106">Undeploying a policy makes it inactive so that it no longer functions in any application that uses it in the BizTalk group.</span></span>  
  
 <span data-ttu-id="02ae2-107">當部署或解除部署原則時，請牢記下列要點：</span><span class="sxs-lookup"><span data-stu-id="02ae2-107">When deploying or undeploying a policy, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="02ae2-108">在能夠部署原則之前，該原則必須存在於 BizTalk 群組的「規則引擎」資料庫中。</span><span class="sxs-lookup"><span data-stu-id="02ae2-108">Before you can deploy a policy, it must exist in the Rule Engine database for the BizTalk group.</span></span> <span data-ttu-id="02ae2-109">如果您匯入包含原則的應用程式，原則會自動匯入 「 規則引擎 」 資料庫，或者您可以明確地原則匯入到 「 規則引擎 」 資料庫使用管理主控台或 BTSTask，中所述[如何匯入原則](../core/how-to-import-a-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="02ae2-109">If you import an application that contains a policy, the policy is automatically imported into the Rule Engine database, or you can explicitly import a policy into the Rule Engine database by using the administration console or BTSTask, as described in [How to Import a Policy](../core/how-to-import-a-policy.md).</span></span> <span data-ttu-id="02ae2-110">或者，您可以將原則加入至 「 規則引擎 」 資料庫使用 「 規則引擎部署精靈 」 中所述[如何部署和解除部署原則和詞彙](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)。</span><span class="sxs-lookup"><span data-stu-id="02ae2-110">Alternatively, you can add a policy to the Rule Engine database by using the Rule Engine Deployment Wizard, as described in [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).</span></span>  
  
-   <span data-ttu-id="02ae2-111">您可以部署原則之前，必須將它發行，如中所述[如何發佈原則](../core/how-to-publish-a-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="02ae2-111">Before you can deploy a policy, it must be published, as described in [How to Publish a Policy](../core/how-to-publish-a-policy.md).</span></span>  
  
-   <span data-ttu-id="02ae2-112">已部署的原則便無法加以修改。</span><span class="sxs-lookup"><span data-stu-id="02ae2-112">A deployed policy cannot be modified.</span></span> <span data-ttu-id="02ae2-113">如果您想要修改已部署的原則，必須先將它解除部署。</span><span class="sxs-lookup"><span data-stu-id="02ae2-113">If you want to modify a deployed policy, you must first undeploy it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="02ae2-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="02ae2-114">Prerequisites</span></span>  
 <span data-ttu-id="02ae2-115">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="02ae2-115">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="02ae2-116">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="02ae2-116">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-deploy-or-undeploy-a-policy"></a><span data-ttu-id="02ae2-117">若要部署或解除部署原則</span><span class="sxs-lookup"><span data-stu-id="02ae2-117">To deploy or undeploy a policy</span></span>  
  
1.  <span data-ttu-id="02ae2-118">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="02ae2-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="02ae2-119">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開包含您要部署或解除部署，然後展開 原則的 BizTalk 群組**\<所有成品 >**。</span><span class="sxs-lookup"><span data-stu-id="02ae2-119">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the policy that you want to deploy or undeploy, and then expand **\<All Artifacts>**.</span></span>  
  
3.  <span data-ttu-id="02ae2-120">按一下**原則**，以滑鼠右鍵按一下原則，然後按一下**部署**或**解除部署**。</span><span class="sxs-lookup"><span data-stu-id="02ae2-120">Click **Policies**, right-click the policy, and then click **Deploy** or **Undeploy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ae2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02ae2-121">See Also</span></span>  
 <span data-ttu-id="02ae2-122">[管理原則](../core/managing-policies.md) </span><span class="sxs-lookup"><span data-stu-id="02ae2-122">[Managing Policies](../core/managing-policies.md) </span></span>  
 [<span data-ttu-id="02ae2-123">如何啟動和停止 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="02ae2-123">How to Start and Stop a BizTalk Application</span></span>](../core/how-to-start-and-stop-a-biztalk-application.md)