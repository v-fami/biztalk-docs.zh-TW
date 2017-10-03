---
title: "單一登 On1 需求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, Single Sign-On
- SSO, requirements [JD Edwards EnterpriseOne adapters]
- adapters [JD Edwards EnterpriseOne adapters], Single Sign-On
- Single Sign-On, requirements [JD Edwards EnterpriseOne adapters]
- Single Sign-On, enabling [JD Edwards EnterpriseOne adapters]
ms.assetid: d1111377-2fe1-4d65-ac0d-c89d2f1740b8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfab6d6cfea2ddef3b953d3fb3bb15900420fdcf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="4b708-102">單一登入的需求</span><span class="sxs-lookup"><span data-stu-id="4b708-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="4b708-103">若要使用單一登入 (SSO)，您必須已安裝下列軟體：</span><span class="sxs-lookup"><span data-stu-id="4b708-103">To use Single Sign-On (SSO), you must have the following software installed:</span></span>  
  
-   <span data-ttu-id="4b708-104">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b708-104">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span></span>  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   <span data-ttu-id="4b708-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="4b708-105">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="4b708-106">支援 SSO 的伺服器系統</span><span class="sxs-lookup"><span data-stu-id="4b708-106">A Server System that supports SSO</span></span>  
  
-   <span data-ttu-id="4b708-107">外掛式主控的件應設定為**信任的驗證**。</span><span class="sxs-lookup"><span data-stu-id="4b708-107">The isolated host should be configured as **Authentication Trusted**.</span></span>  
  
### <a name="to-enable-sso"></a><span data-ttu-id="4b708-108">啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="4b708-108">To enable SSO</span></span>  
  
1.  <span data-ttu-id="4b708-109">在**傳輸屬性**視窗中，選取**是**如**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="4b708-109">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="4b708-110">指定傳輸屬性時，選取適當的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b708-110">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
 <span data-ttu-id="4b708-111">如需建立分支機構應用程式的資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications4.md)。</span><span class="sxs-lookup"><span data-stu-id="4b708-111">For information about creating an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications4.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b708-112">執行工作之後使用 SSO，請記得要重設任何 Web 共用資料夾，以**不會共用**。</span><span class="sxs-lookup"><span data-stu-id="4b708-112">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="4b708-113">如果資料夾是共用的，使用該資料夾的應用程式將不會正確更新或解除安裝，因為它會被視為使用中。</span><span class="sxs-lookup"><span data-stu-id="4b708-113">Applications using that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b708-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b708-114">See Also</span></span>  
 [<span data-ttu-id="4b708-115">使用單一登入</span><span class="sxs-lookup"><span data-stu-id="4b708-115">Using Single Sign-On</span></span>](../core/using-single-sign-on1.md)