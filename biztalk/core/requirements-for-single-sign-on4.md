---
title: "TIBCO EMS 配接器的 SSO 需求 |Microsoft 文件"
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
ms.openlocfilehash: 805d14e056da665f8828ce0244f28ed9adc40ff4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="e0af4-102">單一登入的需求</span><span class="sxs-lookup"><span data-stu-id="e0af4-102">Requirements for Single Sign-On</span></span>

## <a name="overview"></a><span data-ttu-id="e0af4-103">概觀</span><span class="sxs-lookup"><span data-stu-id="e0af4-103">Overview</span></span>
<span data-ttu-id="e0af4-104">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 提供單一登入 (SSO) 支援。</span><span class="sxs-lookup"><span data-stu-id="e0af4-104">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) provides Single Sign-On (SSO) support.</span></span> <span data-ttu-id="e0af4-105">企業單一登入工具建立的分支機構應用程式代表一個伺服器系統 (例如 TIBCO EMS)。</span><span class="sxs-lookup"><span data-stu-id="e0af4-105">An affiliate application created by Enterprise Single Sign-On tools represents a server system such as TIBCO EMS.</span></span>  
  
 <span data-ttu-id="e0af4-106">若要使用「單一登入」，您需要：</span><span class="sxs-lookup"><span data-stu-id="e0af4-106">To use Single Sign-On, you must have:</span></span>  
  
-   <span data-ttu-id="e0af4-107">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e0af4-107">Microsoft BizTalk Server</span></span>
  
-   <span data-ttu-id="e0af4-108">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e0af4-108">Visual Studio</span></span>  
  
-   <span data-ttu-id="e0af4-109">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="e0af4-109">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="e0af4-110">支援 SSO 的伺服器系統</span><span class="sxs-lookup"><span data-stu-id="e0af4-110">A server system that supports SSO</span></span>  
  
 <span data-ttu-id="e0af4-111">外掛式主控件應設定為信任的驗證</span><span class="sxs-lookup"><span data-stu-id="e0af4-111">The isolated host should be configured as authentication trusted.</span></span>
  
## <a name="enable-sso"></a><span data-ttu-id="e0af4-112">啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="e0af4-112">Enable SSO</span></span>  
  
1.  <span data-ttu-id="e0af4-113">在**傳輸屬性**視窗中，選取**是**如**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="e0af4-113">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="e0af4-114">指定傳輸屬性時，選取適當的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0af4-114">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
     <span data-ttu-id="e0af4-115">如需如何建立分支機構應用程式資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications5.md)。</span><span class="sxs-lookup"><span data-stu-id="e0af4-115">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0af4-116">執行工作之後使用 SSO，請記得要重設任何 Web 共用資料夾，以**不會共用**。</span><span class="sxs-lookup"><span data-stu-id="e0af4-116">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="e0af4-117">不使用該資料夾的應用程式將會更新，或如果資料夾共用，因為它會被視為使用中正確地解除安裝。</span><span class="sxs-lookup"><span data-stu-id="e0af4-117">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0af4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0af4-118">See Also</span></span>  
[<span data-ttu-id="e0af4-119">保護配接器</span><span class="sxs-lookup"><span data-stu-id="e0af4-119">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-tibco-ems.md)