---
title: "單一登入的需求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 645c7b3f-f860-4c20-b5ca-a8fb93736344
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98d5164fa194f9a02314b897b267d9873879a9c0
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="51188-102">單一登入的需求</span><span class="sxs-lookup"><span data-stu-id="51188-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="51188-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 提供單一登入 (SSO) 支援。</span><span class="sxs-lookup"><span data-stu-id="51188-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) provides Single Sign-On (SSO) support.</span></span> <span data-ttu-id="51188-104">企業單一登入工具建立的分支機構應用程式代表一個伺服器系統 (例如 TIBCO EMS)。</span><span class="sxs-lookup"><span data-stu-id="51188-104">An affiliate application created by Enterprise Single Sign-On tools represents a server system such as TIBCO EMS.</span></span>  
  
 <span data-ttu-id="51188-105">若要使用「單一登入」，您需要：</span><span class="sxs-lookup"><span data-stu-id="51188-105">To use Single Sign-On, you must have:</span></span>  
  
-   <span data-ttu-id="51188-106">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="51188-106">Microsoft BizTalk Server</span></span>
  
-   <span data-ttu-id="51188-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="51188-107">Visual Studio</span></span>  
  
-   <span data-ttu-id="51188-108">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="51188-108">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="51188-109">支援 SSO 的伺服器系統</span><span class="sxs-lookup"><span data-stu-id="51188-109">A server system that supports SSO</span></span>  
  
 <span data-ttu-id="51188-110">外掛式主控件應設定為信任的驗證</span><span class="sxs-lookup"><span data-stu-id="51188-110">The isolated host should be configured as authentication trusted</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="51188-111">啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="51188-111">Enable SSO</span></span>  
  
1.  <span data-ttu-id="51188-112">在**傳輸屬性**視窗中，選取**是**如**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="51188-112">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="51188-113">指定傳輸屬性時，選取適當的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="51188-113">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
     <span data-ttu-id="51188-114">如需如何建立分支機構應用程式資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications5.md)。</span><span class="sxs-lookup"><span data-stu-id="51188-114">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="51188-115">執行工作之後使用 SSO，請記得要重設任何 Web 共用資料夾，以**不會共用**。</span><span class="sxs-lookup"><span data-stu-id="51188-115">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="51188-116">不使用該資料夾的應用程式將會更新，或如果資料夾共用，因為它會被視為使用中正確地解除安裝。</span><span class="sxs-lookup"><span data-stu-id="51188-116">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51188-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51188-117">See Also</span></span>  
 [<span data-ttu-id="51188-118">使用單一登入</span><span class="sxs-lookup"><span data-stu-id="51188-118">Using Single Sign-On</span></span>](../core/using-single-sign-on4.md)