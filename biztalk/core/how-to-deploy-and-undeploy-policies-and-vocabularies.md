---
title: 如何部署和解除部署原則和詞彙 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, policies
- policies, deploying
- deploying, vocabularies
- policies, undeploying
- vocabularies, deploying
ms.assetid: 9a7e3310-54b7-482c-8210-b4b11fde4c49
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a2c6200f41a4b473175528ac6d2c8ee75c17894
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013063"
---
# <a name="how-to-deploy-and-undeploy-policies-and-vocabularies"></a><span data-ttu-id="2bdc6-102">如何部署和解除部署原則與詞彙</span><span class="sxs-lookup"><span data-stu-id="2bdc6-102">How to Deploy and Undeploy Policies and Vocabularies</span></span>
<span data-ttu-id="2bdc6-103">您可以使用「規則引擎部署精靈」以部署或解除部署原則。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-103">You can use the Rule Engine Deployment Wizard to deploy or undeploy a policy.</span></span>  
  
 <span data-ttu-id="2bdc6-104">當您在「規則引擎部署精靈」中嘗試部署時，下拉式清單中只會顯示已發佈的原則版本。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-104">In the Rule Engine Deployment Wizard, when you try to deploy, only published policy versions are shown in the drop-down list.</span></span> <span data-ttu-id="2bdc6-105">當您嘗試解除部署時，只部署的原則版本會顯示在下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-105">When you try to undeploy, only deployed policy versions are shown in the drop-down list.</span></span>  
  
### <a name="to-deploy-or-undeploy-a-policy"></a><span data-ttu-id="2bdc6-106">若要部署或解除部署原則</span><span class="sxs-lookup"><span data-stu-id="2bdc6-106">To deploy or undeploy a policy</span></span>  
  
1. <span data-ttu-id="2bdc6-107">按一下 **開始**，指向**Program Files**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**商務規則引擎部署精靈**。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-107">Click **Start**, point to **Program Files**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rules Engine Deployment Wizard**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="2bdc6-108">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-108">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="2bdc6-109">若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-109">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2. <span data-ttu-id="2bdc6-110">在 [**規則引擎部署精靈**歡迎頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-110">On the **Rules Engine Deployment Wizard** welcome page, click **Next**.</span></span>  
  
3. <span data-ttu-id="2bdc6-111">選取 [**部署原則**或是**解除部署原則**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-111">Select either **Deploy Policy** or **Undeploy Policy**, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="2bdc6-112">從下拉式清單中，選取可用的 SQL Server 電腦和資料庫，然後**下一步**。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-112">From the drop-down lists, select an available SQL Server computer and database, and then click **Next**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="2bdc6-113">您只能將規則部署至所設定的規則存放資料庫。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-113">You can only deploy to the rule store database that you are configured against.</span></span> <span data-ttu-id="2bdc6-114">嘗試部署至其他資料庫，將會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-114">An attempt to deploy to a different DB will give an error.</span></span>  
  
5. <span data-ttu-id="2bdc6-115">從下拉式清單中，選取原則，然後**下一步**。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-115">From the drop-down list, select a policy, and then click **Next**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="2bdc6-116">當您嘗試部署時，下拉式清單中只會顯示已發佈的原則版本。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-116">When you try to deploy, only published policy versions are shown in the drop-down list.</span></span> <span data-ttu-id="2bdc6-117">當您嘗試解除部署時，只部署的原則版本會顯示在下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-117">When you try to undeploy, only deployed policy versions are shown in the drop-down list.</span></span>  
  
6. <span data-ttu-id="2bdc6-118">檢閱伺服器、 資料庫和原則資訊，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-118">Review the server, database, and policy information, and then click **Next**.</span></span>  
  
7. <span data-ttu-id="2bdc6-119">監看部署或解除部署的進度。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-119">Watch the progress of the deployment or undeployment.</span></span> <span data-ttu-id="2bdc6-120">完成後，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-120">When it is finished, click **Next**.</span></span>  
  
8. <span data-ttu-id="2bdc6-121">檢閱部署或解除部署的完成狀態，然後按**完成**。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-121">Review the completion status of the deployment or undeployment, and then click **Finish**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2bdc6-122">您也可以部署或解除部署原則版本從 「 商務規則編輯器 」 中的以滑鼠右鍵按一下原則版本，然後按一下**Deploy**或是**Undeploy**。</span><span class="sxs-lookup"><span data-stu-id="2bdc6-122">You can also deploy or undeploy a policy version from within the Business Rule Composer by right-clicking the policy version and then clicking **Deploy** or **Undeploy**.</span></span>