---
title: 進行單一登入的需求 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 318b9977-ce24-48d6-971b-49a059a1bdbc
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48346802c25e4b5aeb4d6ac1d5e83552b1220149
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005487"
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="a309b-102">單一登入的需求</span><span class="sxs-lookup"><span data-stu-id="a309b-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="a309b-103">若要使用單一登入 (SSO)，您必須有：</span><span class="sxs-lookup"><span data-stu-id="a309b-103">To use Single Sign-On (SSO), you must have:</span></span>  
  
- <span data-ttu-id="a309b-104">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a309b-104">Microsoft BizTalk Server</span></span> 
  
- <span data-ttu-id="a309b-105">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a309b-105">Visual Studio</span></span>  
  
- <span data-ttu-id="a309b-106">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a309b-106">Enterprise Single Sign-On</span></span>  
  
- <span data-ttu-id="a309b-107">支援 SSO 的伺服器系統</span><span class="sxs-lookup"><span data-stu-id="a309b-107">A Server System that supports SSO</span></span>  
  
  <span data-ttu-id="a309b-108">外掛式主控件應設定為信任的驗證</span><span class="sxs-lookup"><span data-stu-id="a309b-108">The isolated host should be configured as authentication trusted.</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="a309b-109">啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="a309b-109">Enable SSO</span></span>  
  
1.  <span data-ttu-id="a309b-110">在 **傳輸屬性**視窗中，選取**是**for**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="a309b-110">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="a309b-111">指定傳輸屬性時，選取適當的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="a309b-111">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
     <span data-ttu-id="a309b-112">如需建立分支機構應用程式的資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications3.md)。</span><span class="sxs-lookup"><span data-stu-id="a309b-112">For information about creating affiliate applications, see [Creating Affiliate Applications](../core/creating-affiliate-applications3.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a309b-113">執行工作之後使用 SSO，請務必重設任何**Web 共用**資料夾，以**不會共用**。</span><span class="sxs-lookup"><span data-stu-id="a309b-113">After performing work using SSO, remember to reset any **Web-Sharing** folder to **Do not share**.</span></span> <span data-ttu-id="a309b-114">如果資料夾是共用的，使用該資料夾的應用程式將不會正確更新或解除安裝，因為它會被視為使用中。</span><span class="sxs-lookup"><span data-stu-id="a309b-114">Applications using that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a309b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a309b-115">See Also</span></span>  
 [<span data-ttu-id="a309b-116">配接器中的安全性</span><span class="sxs-lookup"><span data-stu-id="a309b-116">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)