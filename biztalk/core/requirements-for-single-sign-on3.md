---
title: "TIBCO 會合配接器的 SSO 需求 |Microsoft 文件"
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
ms.openlocfilehash: 40cf27a3b96534239fa871bd04b90febee9beafe
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="8a056-102">單一登入的需求</span><span class="sxs-lookup"><span data-stu-id="8a056-102">Requirements for Single Sign-On</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a056-103">必要條件</span><span class="sxs-lookup"><span data-stu-id="8a056-103">Prerequisites</span></span>
<span data-ttu-id="8a056-104">若要使用「單一登入」(SSO)，您必須具有下列項目：</span><span class="sxs-lookup"><span data-stu-id="8a056-104">To use Single Sign-On (SSO), you must have the following:</span></span>  
  
-   <span data-ttu-id="8a056-105">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8a056-105">Microsoft BizTalk Server</span></span>
  
-   <span data-ttu-id="8a056-106">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8a056-106">Visual Studio</span></span>  
  
-   <span data-ttu-id="8a056-107">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="8a056-107">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="8a056-108">支援 SSO 的伺服器系統</span><span class="sxs-lookup"><span data-stu-id="8a056-108">A server system that supports SSO</span></span>  
  
-   <span data-ttu-id="8a056-109">外掛式主控件應設定為信任的驗證。</span><span class="sxs-lookup"><span data-stu-id="8a056-109">The isolated host should be configured as Authentication Trusted.</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="8a056-110">啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="8a056-110">Enable SSO</span></span>  
  
1.  <span data-ttu-id="8a056-111">在**傳輸屬性**視窗中，選取**是**如**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="8a056-111">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="8a056-112">指定傳輸屬性時，選取適當的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a056-112">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
 <span data-ttu-id="8a056-113">如需詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications1.md)。</span><span class="sxs-lookup"><span data-stu-id="8a056-113">For more information, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a056-114">執行工作之後使用 SSO，請記得要重設任何 Web 共用資料夾，以**不會共用**。</span><span class="sxs-lookup"><span data-stu-id="8a056-114">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="8a056-115">不使用該資料夾的應用程式將會更新，或如果資料夾共用，因為它會被視為使用中正確地解除安裝。</span><span class="sxs-lookup"><span data-stu-id="8a056-115">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a056-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a056-116">See Also</span></span>  
[<span data-ttu-id="8a056-117">安全性</span><span class="sxs-lookup"><span data-stu-id="8a056-117">Security</span></span>](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)