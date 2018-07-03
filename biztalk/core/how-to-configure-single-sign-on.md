---
title: 如何設定單一登入 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 511edc1d-de82-4d17-88ea-6cacfccde10d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b23e2bb61f4549e642bcd9a59f56bc232b40038
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019933"
---
# <a name="how-to-configure-single-sign-on"></a><span data-ttu-id="722b5-102">如何設定單一登入</span><span class="sxs-lookup"><span data-stu-id="722b5-102">How to Configure Single Sign-On</span></span>
<span data-ttu-id="722b5-103">在存取「企業單一登入」之前，您應該確認目前的使用者已正確設定「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="722b5-103">Before accessing Enterprise Single Sign-On, you should make sure that Enterprise Single Sign-On is set correctly for the current user.</span></span> <span data-ttu-id="722b5-104">對於多數組態，您會使用兩個介面之一。</span><span class="sxs-lookup"><span data-stu-id="722b5-104">For most configurations, you use one of two interfaces.</span></span> <span data-ttu-id="722b5-105">`ISSOAdmin` 是可讓您建立新的分支機構應用程式的一般系統管理介面。</span><span class="sxs-lookup"><span data-stu-id="722b5-105">`ISSOAdmin` is the general administration interface that enables you to create new affiliation applications.</span></span> <span data-ttu-id="722b5-106">不過，藉由使用 ISSOAdmin.GetGlobalInfo 和 ISSOAdmin.UpdateGlobalInfo，您可以設定各種旗標和管理值。</span><span class="sxs-lookup"><span data-stu-id="722b5-106">However, by using ISSOAdmin.GetGlobalInfo and ISSOAdmin.UpdateGlobalInfo, you can set a variety of flags and administration values.</span></span> <span data-ttu-id="722b5-107">如下所述的一項可能工作就是確保已經啟用 SSO 票證。</span><span class="sxs-lookup"><span data-stu-id="722b5-107">One possible task, as described in the following procedure, is to ensure that SSO ticketing has been enabled.</span></span>  
  
### <a name="to-enable-ticketing"></a><span data-ttu-id="722b5-108">若要啟用票證</span><span class="sxs-lookup"><span data-stu-id="722b5-108">To enable ticketing</span></span>  
  
1. <span data-ttu-id="722b5-109">建立新的 `ISSOAdmin` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="722b5-109">Create a new instance of `ISSOAdmin`.</span></span>  
  
2. <span data-ttu-id="722b5-110">透過 `ISSOAdmin.GetGlobalInfo` 擷取目前的設定。</span><span class="sxs-lookup"><span data-stu-id="722b5-110">Retrieve the current settings through `ISSOAdmin.GetGlobalInfo`.</span></span>  
  
    <span data-ttu-id="722b5-111">如有需要，您可能要在此時確認旗標已設定為正確的值。</span><span class="sxs-lookup"><span data-stu-id="722b5-111">If necessary, you may want to confirm that the flags are set to the correct values at this point.</span></span>  
  
3. <span data-ttu-id="722b5-112">使用 `ISSOAdmin.UpdateGlobalInfo` 變更任何相關的旗標。</span><span class="sxs-lookup"><span data-stu-id="722b5-112">Change any relevant flags using `ISSOAdmin.UpdateGlobalInfo`.</span></span>  
  
    <span data-ttu-id="722b5-113">在本個案中，所有旗標均會設為驗證並啟用票證。</span><span class="sxs-lookup"><span data-stu-id="722b5-113">In this particular case, all the flags are being set to validate and enable tickets.</span></span>  
  
   <span data-ttu-id="722b5-114">下列範例顯示如何使用「單一登入」啟用票證。</span><span class="sxs-lookup"><span data-stu-id="722b5-114">The following example shows how to enable ticketing using Single Sign-On.</span></span>  
  
```  
public static bool EnableTickets()  
{  
   try  
   {  
      ISSOAdmin admin=new ISSOAdmin();  
      int flags=0;  
      int appDeleteMax=1000;  
      int mappingDeleteMax=1000;  
      int ntpLookupMax=-1000;  
      int xplLookupMax=-1000;  
      int ticketTimeout=2;  
      int cacheTimeout=60;  
      string secretServer=null;  
      string ssoAdminGroup=null;  
      string affiliateAppMgrGroup=null;  
      // Get current default settings.  
      admin.GetGlobalInfo(out flags, out appDeleteMax, out mappingDeleteMax, out ntpLookupMax, out xplLookupMax, out ticketTimeout, out cacheTimeout, out secretServer, out ssoAdminGroup, out affiliateAppMgrGroup);  
      // Update global settings.  
      admin.UpdateGlobalInfo(SSOFlag.SSO_FLAG_ALLOW_TICKETS | SSOFlag.SSO_FLAG_VALIDATE_TICKETS, SSOFlag.SSO_FLAG_ALLOW_TICKETS | SSOFlag.SSO_FLAG_VALIDATE_TICKETS, ref appDeleteMax, ref mappingDeleteMax, ref ntpLookupMax, ref xplLookupMax, ref ticketTimeout, ref cacheTimeout, null, null, null);   
   }  
   catch  
   {  
      return false;  
   }  
return true;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="722b5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="722b5-115">See Also</span></span>  
 [<span data-ttu-id="722b5-116">企業單一登入程式設計</span><span class="sxs-lookup"><span data-stu-id="722b5-116">Programming with Enterprise Single Sign-On</span></span>](../core/programming-with-enterprise-single-sign-on.md)