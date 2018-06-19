---
title: 單一登入的需求 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1111377-2fe1-4d65-ac0d-c89d2f1740b8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43e54da709384611bffd1e05da6a79decc778e57
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015621"
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="6e392-102">單一登入的需求</span><span class="sxs-lookup"><span data-stu-id="6e392-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="6e392-103">若要使用單一登入 (SSO)，您必須已安裝下列軟體：</span><span class="sxs-lookup"><span data-stu-id="6e392-103">To use Single Sign-On (SSO), you must have the following software installed:</span></span>  
  
-   <span data-ttu-id="6e392-104">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6e392-104">Microsoft BizTalk Server</span></span>
  
-   <span data-ttu-id="6e392-105">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6e392-105">Visual Studio</span></span>  
  
-   <span data-ttu-id="6e392-106">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="6e392-106">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="6e392-107">支援 SSO 的伺服器系統</span><span class="sxs-lookup"><span data-stu-id="6e392-107">A Server System that supports SSO</span></span>  
  
-   <span data-ttu-id="6e392-108">外掛式主控的件應設定為**信任的驗證**。</span><span class="sxs-lookup"><span data-stu-id="6e392-108">The isolated host should be configured as **Authentication Trusted**.</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="6e392-109">啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="6e392-109">Enable SSO</span></span>  
  
1.  <span data-ttu-id="6e392-110">在**傳輸屬性**視窗中，選取**是**如**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="6e392-110">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="6e392-111">指定傳輸屬性時，選取適當的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e392-111">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
 <span data-ttu-id="6e392-112">如需建立分支機構應用程式的資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications4.md)。</span><span class="sxs-lookup"><span data-stu-id="6e392-112">For information about creating an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications4.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e392-113">執行工作之後使用 SSO，請記得要重設任何 Web 共用資料夾，以**不會共用**。</span><span class="sxs-lookup"><span data-stu-id="6e392-113">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="6e392-114">如果資料夾是共用的，使用該資料夾的應用程式將不會正確更新或解除安裝，因為它會被視為使用中。</span><span class="sxs-lookup"><span data-stu-id="6e392-114">Applications using that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e392-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e392-115">See Also</span></span>  
 [<span data-ttu-id="6e392-116">BizTalk Adapter for JD Edwards EnterpriseOne 中的安全性</span><span class="sxs-lookup"><span data-stu-id="6e392-116">Security in BizTalk Adapter for JD Edwards EnterpriseOne</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)