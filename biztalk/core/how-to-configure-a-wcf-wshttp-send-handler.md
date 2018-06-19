---
title: 如何設定 Wcf-wshttp 傳送處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-WSHttp adapters, global variables
- configuring [WCF-WSHttp adapters], send handlers
- configuring [WCF-WSHttp adapters], global variables
- send handlers, WCF-WSHttp adapters
ms.assetid: b2c30edb-8f7b-4d3c-812b-5b877c47fda1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11566bcc902ccbda33b6b15922292390df3d5201
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248454"
---
# <a name="how-to-configure-a-wcf-wshttp-send-handler"></a><span data-ttu-id="4495d-102">如何設定 WCF-WSHttp 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="4495d-102">How to Configure a WCF-WSHttp Send Handler</span></span>
<span data-ttu-id="4495d-103">您可以透過下列程序，設定 WCF-WSHttp 傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="4495d-103">Use the following procedure to configure the WCF-WSHttp send handler.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4495d-104">使用 WCF-WSHttp 配接器處理常式時，建議您在 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 電腦上安裝這些處理常式的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="4495d-104">When using WCF-WSHttp adapter handlers, it is recommended that you install the host instances for these handlers on [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computers.</span></span>  
  
### <a name="to-change-global-variables-for-a-wcf-wshttp-send-handler"></a><span data-ttu-id="4495d-105">若要變更 WCF-WSHttp 傳送處理常式的全域變數</span><span class="sxs-lookup"><span data-stu-id="4495d-105">To change global variables for a WCF-WSHttp send handler</span></span>  
  
1.  <span data-ttu-id="4495d-106">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="4495d-106">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="4495d-107">在展開的配接器清單中，按一下  **Wcf-wshttp**，在右窗格，以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4495d-107">In the expanded adapter list, click **WCF-WSHttp**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="4495d-108">在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的接收處理常式的主機。</span><span class="sxs-lookup"><span data-stu-id="4495d-108">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  
  
4.  <span data-ttu-id="4495d-109">在**一般**索引標籤上，按一下**屬性**上**Proxy**索引標籤上，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="4495d-109">In the **General** tab, Click **Properties**, On the **Proxy** tab, do the following.</span></span>  
  
    |<span data-ttu-id="4495d-110">使用</span><span class="sxs-lookup"><span data-stu-id="4495d-110">Use this</span></span>|<span data-ttu-id="4495d-111">動作</span><span class="sxs-lookup"><span data-stu-id="4495d-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4495d-112">**使用 Proxy**</span><span class="sxs-lookup"><span data-stu-id="4495d-112">**Use proxy**</span></span>|<span data-ttu-id="4495d-113">指出這個傳送埠是否要使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="4495d-113">Indicate whether this send port uses a proxy server.</span></span><br /><br /> <span data-ttu-id="4495d-114">預設值為清除核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4495d-114">The default value is cleared.</span></span>|  
    |<span data-ttu-id="4495d-115">**位址**</span><span class="sxs-lookup"><span data-stu-id="4495d-115">**Address**</span></span>|<span data-ttu-id="4495d-116">指定 Proxy 伺服器的位址。</span><span class="sxs-lookup"><span data-stu-id="4495d-116">Specify the address of the proxy server.</span></span> <span data-ttu-id="4495d-117">使用**https**或**http**根據安全性組態的配置。</span><span class="sxs-lookup"><span data-stu-id="4495d-117">Use the **https** or the **http** scheme depending on the security configuration.</span></span> <span data-ttu-id="4495d-118">這個位址後面可以加上冒號和連接埠編號，</span><span class="sxs-lookup"><span data-stu-id="4495d-118">This address can be followed by a colon and the port number.</span></span> <span data-ttu-id="4495d-119">例如 http://127.0.0.1:8080。</span><span class="sxs-lookup"><span data-stu-id="4495d-119">For example, http://127.0.0.1:8080.</span></span><br /><br /> <span data-ttu-id="4495d-120">這個屬性的值才需要**使用 proxy**已選取。</span><span class="sxs-lookup"><span data-stu-id="4495d-120">This property requires a value only if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="4495d-121">類型：字串</span><span class="sxs-lookup"><span data-stu-id="4495d-121">Type: String</span></span><br /><br /> <span data-ttu-id="4495d-122">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="4495d-122">Maximum length: 256</span></span><br /><br /> <span data-ttu-id="4495d-123">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="4495d-123">The default is an empty string.</span></span>|  
    |<span data-ttu-id="4495d-124">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="4495d-124">**User name**</span></span>|<span data-ttu-id="4495d-125">指定要用於驗證的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4495d-125">Specify the user name to use for authentication.</span></span> <span data-ttu-id="4495d-126">若使用整合式或基本驗證，則使用者名稱也包括網域，即「網域\使用者名稱」。</span><span class="sxs-lookup"><span data-stu-id="4495d-126">If integrated or Basic authentication is used, the user name includes the domain, that is, domain\username.</span></span> <span data-ttu-id="4495d-127">如果使用摘要式驗證，則使用者名稱不包含網域\\。</span><span class="sxs-lookup"><span data-stu-id="4495d-127">If Digest authentication is used, the user name does not include domain\\.</span></span><br /><br /> <span data-ttu-id="4495d-128">這個屬性的值才需要**使用 proxy**已選取。</span><span class="sxs-lookup"><span data-stu-id="4495d-128">This property requires a value only if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="4495d-129">類型：字串</span><span class="sxs-lookup"><span data-stu-id="4495d-129">Type: String</span></span><br /><br /> <span data-ttu-id="4495d-130">最小長度：00</span><span class="sxs-lookup"><span data-stu-id="4495d-130">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="4495d-131">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="4495d-131">Maximum length: 256</span></span><br /><br /> <span data-ttu-id="4495d-132">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="4495d-132">The default is an empty string.</span></span>|  
    |<span data-ttu-id="4495d-133">**密碼**</span><span class="sxs-lookup"><span data-stu-id="4495d-133">**Password**</span></span>|<span data-ttu-id="4495d-134">指定要用於驗證的密碼。</span><span class="sxs-lookup"><span data-stu-id="4495d-134">Specify the password to use for authentication.</span></span><br /><br /> <span data-ttu-id="4495d-135">這個屬性的值才需要**使用 proxy**已選取。</span><span class="sxs-lookup"><span data-stu-id="4495d-135">This property requires a value only if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="4495d-136">類型：字串</span><span class="sxs-lookup"><span data-stu-id="4495d-136">Type: String</span></span><br /><br /> <span data-ttu-id="4495d-137">最小長度：00</span><span class="sxs-lookup"><span data-stu-id="4495d-137">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="4495d-138">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="4495d-138">Maximum length: 256</span></span><br /><br /> <span data-ttu-id="4495d-139">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="4495d-139">The default is an empty string.</span></span>|  
  
5.  <span data-ttu-id="4495d-140">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4495d-140">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4495d-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4495d-141">See Also</span></span>  
 [<span data-ttu-id="4495d-142">設定 Wcf-wshttp 配接器</span><span class="sxs-lookup"><span data-stu-id="4495d-142">Configuring the WCF-WSHttp Adapter</span></span>](../core/configuring-the-wcf-wshttp-adapter.md)