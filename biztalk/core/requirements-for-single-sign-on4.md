---
title: TIBCO EMS 配接器的 SSO 需求 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 645c7b3f-f860-4c20-b5ca-a8fb93736344
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8baf665a7f997293130a2c1eb93f893167f39a4f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967879"
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="4b15e-102">單一登入的需求</span><span class="sxs-lookup"><span data-stu-id="4b15e-102">Requirements for Single Sign-On</span></span>

## <a name="overview"></a><span data-ttu-id="4b15e-103">概觀</span><span class="sxs-lookup"><span data-stu-id="4b15e-103">Overview</span></span>
<span data-ttu-id="4b15e-104">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 提供單一登入 (SSO) 支援。</span><span class="sxs-lookup"><span data-stu-id="4b15e-104">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) provides Single Sign-On (SSO) support.</span></span> <span data-ttu-id="4b15e-105">企業單一登入工具建立的分支機構應用程式代表一個伺服器系統 (例如 TIBCO EMS)。</span><span class="sxs-lookup"><span data-stu-id="4b15e-105">An affiliate application created by Enterprise Single Sign-On tools represents a server system such as TIBCO EMS.</span></span>  
  
 <span data-ttu-id="4b15e-106">若要使用「單一登入」，您需要：</span><span class="sxs-lookup"><span data-stu-id="4b15e-106">To use Single Sign-On, you must have:</span></span>  
  
- <span data-ttu-id="4b15e-107">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4b15e-107">Microsoft BizTalk Server</span></span>
  
- <span data-ttu-id="4b15e-108">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4b15e-108">Visual Studio</span></span>  
  
- <span data-ttu-id="4b15e-109">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="4b15e-109">Enterprise Single Sign-On</span></span>  
  
- <span data-ttu-id="4b15e-110">支援 SSO 的伺服器系統</span><span class="sxs-lookup"><span data-stu-id="4b15e-110">A server system that supports SSO</span></span>  
  
  <span data-ttu-id="4b15e-111">外掛式主控件應設定為信任的驗證</span><span class="sxs-lookup"><span data-stu-id="4b15e-111">The isolated host should be configured as authentication trusted.</span></span>
  
## <a name="enable-sso"></a><span data-ttu-id="4b15e-112">啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="4b15e-112">Enable SSO</span></span>  
  
1.  <span data-ttu-id="4b15e-113">在 **傳輸屬性**視窗中，選取**是**for**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="4b15e-113">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="4b15e-114">指定傳輸屬性時，選取適當的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b15e-114">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
     <span data-ttu-id="4b15e-115">如需有關如何建立分支機構應用程式的資訊，請參閱 <<c0> [ 建立分支機構應用程式](../core/creating-affiliate-applications5.md)。</span><span class="sxs-lookup"><span data-stu-id="4b15e-115">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4b15e-116">執行工作之後使用 SSO，請務必重設任何 Web 共用的資料夾，以**不會共用**。</span><span class="sxs-lookup"><span data-stu-id="4b15e-116">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="4b15e-117">不使用該資料夾的應用程式將會更新，或如果資料夾已共用，因為它會被視為使用中正確地解除安裝。</span><span class="sxs-lookup"><span data-stu-id="4b15e-117">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b15e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b15e-118">See Also</span></span>  
[<span data-ttu-id="4b15e-119">保護配接器</span><span class="sxs-lookup"><span data-stu-id="4b15e-119">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-tibco-ems.md)