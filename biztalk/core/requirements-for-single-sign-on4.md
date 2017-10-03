---
title: "單一登 On4 需求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Single Sign-On, requirements
- SSO, enabling
- Single Sign-On, enabling
- SSO requirements
ms.assetid: 645c7b3f-f860-4c20-b5ca-a8fb93736344
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15d7bdbf52869e5b13ae113716689bbb5b7ffec3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="8892f-102">單一登入的需求</span><span class="sxs-lookup"><span data-stu-id="8892f-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="8892f-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 提供單一登入 (SSO) 支援。</span><span class="sxs-lookup"><span data-stu-id="8892f-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) provides Single Sign-On (SSO) support.</span></span> <span data-ttu-id="8892f-104">企業單一登入工具建立的分支機構應用程式代表一個伺服器系統 (例如 TIBCO EMS)。</span><span class="sxs-lookup"><span data-stu-id="8892f-104">An affiliate application created by Enterprise Single Sign-On tools represents a server system such as TIBCO EMS.</span></span>  
  
 <span data-ttu-id="8892f-105">若要使用「單一登入」，您需要：</span><span class="sxs-lookup"><span data-stu-id="8892f-105">To use Single Sign-On, you must have:</span></span>  
  
-   <span data-ttu-id="8892f-106">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8892f-106">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span></span>  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   <span data-ttu-id="8892f-107">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="8892f-107">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="8892f-108">支援 SSO 的伺服器系統</span><span class="sxs-lookup"><span data-stu-id="8892f-108">A server system that supports SSO</span></span>  
  
 <span data-ttu-id="8892f-109">外掛式主控件應設定為信任的驗證</span><span class="sxs-lookup"><span data-stu-id="8892f-109">The isolated host should be configured as authentication trusted</span></span>  
  
### <a name="to-enable-sso"></a><span data-ttu-id="8892f-110">啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="8892f-110">To enable SSO</span></span>  
  
1.  <span data-ttu-id="8892f-111">在**傳輸屬性**視窗中，選取**是**如**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="8892f-111">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="8892f-112">指定傳輸屬性時，選取適當的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="8892f-112">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
     <span data-ttu-id="8892f-113">如需如何建立分支機構應用程式資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications5.md)。</span><span class="sxs-lookup"><span data-stu-id="8892f-113">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8892f-114">執行工作之後使用 SSO，請記得要重設任何 Web 共用資料夾，以**不會共用**。</span><span class="sxs-lookup"><span data-stu-id="8892f-114">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="8892f-115">不使用該資料夾的應用程式將會更新，或如果資料夾共用，因為它會被視為使用中正確地解除安裝。</span><span class="sxs-lookup"><span data-stu-id="8892f-115">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8892f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8892f-116">See Also</span></span>  
 [<span data-ttu-id="8892f-117">使用單一登入</span><span class="sxs-lookup"><span data-stu-id="8892f-117">Using Single Sign-On</span></span>](../core/using-single-sign-on4.md)