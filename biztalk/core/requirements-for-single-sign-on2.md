---
title: 進行單一登入的需求 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae4b5c1f-1718-4628-9159-2fb877498913
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96a4101dc5380168db60e687ddc450f98f9192f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987311"
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="1ad30-102">單一登入的需求</span><span class="sxs-lookup"><span data-stu-id="1ad30-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="1ad30-103">若要使用「單一登入」(SSO)，您需要：</span><span class="sxs-lookup"><span data-stu-id="1ad30-103">To use Single Sign-On (SSO), you need:</span></span>  
  
- <span data-ttu-id="1ad30-104">BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1ad30-104">BizTalk Server</span></span>
  
- <span data-ttu-id="1ad30-105">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1ad30-105">Visual Studio</span></span>  
  
- <span data-ttu-id="1ad30-106">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="1ad30-106">Enterprise Single Sign-On</span></span>  
  
- <span data-ttu-id="1ad30-107">支援 SSO 的伺服器系統</span><span class="sxs-lookup"><span data-stu-id="1ad30-107">A Server System that supports SSO</span></span>  
  
  <span data-ttu-id="1ad30-108">外掛式主控件應設定為信任的驗證</span><span class="sxs-lookup"><span data-stu-id="1ad30-108">The isolated host should be configured as authentication trusted.</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="1ad30-109">啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="1ad30-109">Enable SSO</span></span>  
  
1. <span data-ttu-id="1ad30-110">在 **傳輸屬性**視窗中，選取**是**for**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="1ad30-110">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2. <span data-ttu-id="1ad30-111">指定傳輸屬性時，選取適當的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ad30-111">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
   <span data-ttu-id="1ad30-112">如需有關如何建立分支機構應用程式的資訊，請參閱 <<c0> [ 建立分支機構應用程式](../core/creating-affiliate-applications2.md)。</span><span class="sxs-lookup"><span data-stu-id="1ad30-112">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications2.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ad30-113">執行工作之後使用 SSO，請務必重設任何 Web 共用的資料夾，以**不會共用**。</span><span class="sxs-lookup"><span data-stu-id="1ad30-113">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="1ad30-114">不使用該資料夾的應用程式將會更新，或如果資料夾已共用，因為它會被視為使用中正確地解除安裝。</span><span class="sxs-lookup"><span data-stu-id="1ad30-114">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad30-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ad30-115">See Also</span></span>  
 <span data-ttu-id="1ad30-116">[執行 SSO 專案](../core/running-sso-projects1.md) </span><span class="sxs-lookup"><span data-stu-id="1ad30-116">[Running SSO Projects](../core/running-sso-projects1.md) </span></span>  
 [<span data-ttu-id="1ad30-117">保護配接器</span><span class="sxs-lookup"><span data-stu-id="1ad30-117">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)