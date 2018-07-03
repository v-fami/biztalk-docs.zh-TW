---
title: 如何移除 SSO |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Master Secret server, deleting
- SSO, deleting
- deleting, SSO
- deleting, Master Secret server
ms.assetid: 0e1ad8e3-0938-4f36-b85b-4631d0eeb8c9
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb712972c0fd7ba8975f30ee6519812dd863e442
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004103"
---
# <a name="how-to-remove-sso"></a><span data-ttu-id="28c31-102">如何移除 SSO</span><span class="sxs-lookup"><span data-stu-id="28c31-102">How to Remove SSO</span></span>
<span data-ttu-id="28c31-103">若您移除 BizTalk Server，就不會再設定「企業單一登入」(SSO)，除非相依產品正在使用它。</span><span class="sxs-lookup"><span data-stu-id="28c31-103">If you remove BizTalk Server, Enterprise Single Sign-On (SSO) is no longer configured unless a dependent product is using it.</span></span> <span data-ttu-id="28c31-104">但不會將它移除。</span><span class="sxs-lookup"><span data-stu-id="28c31-104">However, it is not removed.</span></span> <span data-ttu-id="28c31-105">您必須個別移除 SSO。</span><span class="sxs-lookup"><span data-stu-id="28c31-105">You must remove SSO separately.</span></span> <span data-ttu-id="28c31-106">您也可以還原組態資訊 (包括主要密碼)，以重複使用現有的資料。</span><span class="sxs-lookup"><span data-stu-id="28c31-106">You can also restore configuration information including the master secret to reuse existing data.</span></span> <span data-ttu-id="28c31-107">如需詳細資訊，請參閱 <<c0> [ 如何還原主要祕密](../core/how-to-restore-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="28c31-107">For more information, see [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md).</span></span>  
  
### <a name="to-remove-enterprise-single-sign-on"></a><span data-ttu-id="28c31-108">若要移除企業單一登入</span><span class="sxs-lookup"><span data-stu-id="28c31-108">To remove Enterprise Single Sign-On</span></span>  
  
1. <span data-ttu-id="28c31-109">備份主要密碼金鑰。</span><span class="sxs-lookup"><span data-stu-id="28c31-109">Back up the master secret key.</span></span> <span data-ttu-id="28c31-110">如需詳細資訊，請參閱 <<c0> [ 如何重新設定主要密碼](../core/how-to-back-up-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="28c31-110">For more information, see [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md).</span></span>  
  
2. <span data-ttu-id="28c31-111">解除安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="28c31-111">Uninstall [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
3. <span data-ttu-id="28c31-112">在 **[開始]** 功能表上，按一下 **[控制台]**。</span><span class="sxs-lookup"><span data-stu-id="28c31-112">On the **Start** menu, click **Control Panel**.</span></span>  
  
4. <span data-ttu-id="28c31-113">按一下 **新增/移除程式**。</span><span class="sxs-lookup"><span data-stu-id="28c31-113">Click **Add/Remove Programs**.</span></span>  
  
5. <span data-ttu-id="28c31-114">在 [**新增/移除程式**] 對話方塊中，按一下**Microsoft 企業單一登入**，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="28c31-114">In the **Add/Remove Programs** dialog box, click **Microsoft Enterprise Single Sign-On**, and then click **Remove**.</span></span>  
  
6. <span data-ttu-id="28c31-115">按一下 **是**當系統提示您確認的 Microsoft 企業單一登入移除。</span><span class="sxs-lookup"><span data-stu-id="28c31-115">Click **Yes** when prompted to confirm the removal of Microsoft Enterprise Single Sign-On.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="28c31-116">如果您已安裝 BizTalk Server 執行階段、程式開發或管理功能，或是安裝了 Host Integration Server 管理功能，則在移除所有相依性之前，您將無法解除安裝「SSO 執行階段」或「管理」元件。</span><span class="sxs-lookup"><span data-stu-id="28c31-116">If you have BizTalk Server Runtime, Development, or Administration features installed, or Host Integration Server Administration features installed, you will not be able to uninstall the SSO Runtime or Administration components until all dependencies are removed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c31-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28c31-117">See Also</span></span>  
 [<span data-ttu-id="28c31-118">安裝 SSO</span><span class="sxs-lookup"><span data-stu-id="28c31-118">Installing SSO</span></span>](../core/installing-sso.md)