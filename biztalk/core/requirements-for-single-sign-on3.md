---
title: "單一登入的需求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d5c406b-f548-4df0-8644-fdf6a812a989
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61932b44364670515f02f89a1441a5d54030bc94
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="77d19-102">單一登入的需求</span><span class="sxs-lookup"><span data-stu-id="77d19-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="77d19-103">若要使用「單一登入」(SSO)，您必須具有下列項目：</span><span class="sxs-lookup"><span data-stu-id="77d19-103">To use Single Sign-On (SSO), you must have the following:</span></span>  
  
-   <span data-ttu-id="77d19-104">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="77d19-104">Microsoft BizTalk Server</span></span>
  
-   <span data-ttu-id="77d19-105">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="77d19-105">Visual Studio</span></span>  
  
-   <span data-ttu-id="77d19-106">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="77d19-106">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="77d19-107">支援 SSO 的伺服器系統</span><span class="sxs-lookup"><span data-stu-id="77d19-107">A server system that supports SSO</span></span>  
  
-   <span data-ttu-id="77d19-108">外掛式主控件應設定為信任的驗證。</span><span class="sxs-lookup"><span data-stu-id="77d19-108">The isolated host should be configured as Authentication Trusted.</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="77d19-109">啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="77d19-109">Enable SSO</span></span>  
  
1.  <span data-ttu-id="77d19-110">在**傳輸屬性**視窗中，選取**是**如**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="77d19-110">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="77d19-111">指定傳輸屬性時，選取適當的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="77d19-111">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
 <span data-ttu-id="77d19-112">如需詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications1.md)。</span><span class="sxs-lookup"><span data-stu-id="77d19-112">For more information, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77d19-113">執行工作之後使用 SSO，請記得要重設任何 Web 共用資料夾，以**不會共用**。</span><span class="sxs-lookup"><span data-stu-id="77d19-113">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="77d19-114">不使用該資料夾的應用程式將會更新，或如果資料夾共用，因為它會被視為使用中正確地解除安裝。</span><span class="sxs-lookup"><span data-stu-id="77d19-114">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d19-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77d19-115">See Also</span></span>  
 [<span data-ttu-id="77d19-116">使用單一登入</span><span class="sxs-lookup"><span data-stu-id="77d19-116">Using Single Sign-On</span></span>](../core/using-single-sign-on5.md)