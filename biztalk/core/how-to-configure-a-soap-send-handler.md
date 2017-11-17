---
title: "如何設定 SOAP 傳送處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send handlers, SOAP adapters
- SOAP adapters, denial of service
- denital of service, HTTP adapters
- configuring [SOAP adapters], send handlers
- configuring [SOAP adapters], denial of service
- SOAP adapters, send handlers
- denial of service, SOAP adapters
ms.assetid: fd610a3f-ca10-42e0-b81e-219e07e33830
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65ca116b47e36d754b27839a09225aeb313c9e0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-soap-send-handler"></a><span data-ttu-id="44b35-102">如何設定 SOAP 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="44b35-102">How to Configure a SOAP Send Handler</span></span>
<span data-ttu-id="44b35-103">使用下列程序，來設定 SOAP 傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="44b35-103">Use the following procedure to configure the SOAP send handler.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="44b35-104">當使用 HTTP 或 SOAP 配接器處理常式時，建議您在 Microsoft 上安裝這些處理常式的主控件執行個體[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="44b35-104">When using HTTP or SOAP adapter handlers, it is recommended that you install the host instances for these handlers on Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]computers.</span></span>  
  
### <a name="to-change-global-variables-for-a-soap-send-handler"></a><span data-ttu-id="44b35-105">變更 SOAP 傳送處理常式的全域變數</span><span class="sxs-lookup"><span data-stu-id="44b35-105">To change global variables for a SOAP send handler</span></span>  
  
1.  <span data-ttu-id="44b35-106">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="44b35-106">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="44b35-107">在展開的配接器清單中，按一下  **SOAP**，在右窗格，以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="44b35-107">In the expanded adapter list, click **SOAP**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="44b35-108">在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的接收處理常式的主機。</span><span class="sxs-lookup"><span data-stu-id="44b35-108">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  
  
4.  <span data-ttu-id="44b35-109">在**Proxy**索引標籤上，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="44b35-109">On the **Proxy** tab, do the following.</span></span>  
  
    |<span data-ttu-id="44b35-110">使用</span><span class="sxs-lookup"><span data-stu-id="44b35-110">Use this</span></span>|<span data-ttu-id="44b35-111">動作</span><span class="sxs-lookup"><span data-stu-id="44b35-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="44b35-112">**使用 Proxy**</span><span class="sxs-lookup"><span data-stu-id="44b35-112">**Use proxy**</span></span>|<span data-ttu-id="44b35-113">指示 SOAP 傳送處理常式是否要使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="44b35-113">Indicate whether the SOAP send handler uses a proxy server.</span></span>|  
    |<span data-ttu-id="44b35-114">**Server**</span><span class="sxs-lookup"><span data-stu-id="44b35-114">**Server**</span></span>|<span data-ttu-id="44b35-115">指定 Proxy 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="44b35-115">Specify the name of the proxy server.</span></span><br /><br /> <span data-ttu-id="44b35-116">這個屬性只需要一個值，如果**使用 proxy**已選取。</span><span class="sxs-lookup"><span data-stu-id="44b35-116">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="44b35-117">類型：字串</span><span class="sxs-lookup"><span data-stu-id="44b35-117">Type: String</span></span><br /><br /> <span data-ttu-id="44b35-118">最小長度：00</span><span class="sxs-lookup"><span data-stu-id="44b35-118">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="44b35-119">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="44b35-119">Maximum length: 256</span></span>|  
    |<span data-ttu-id="44b35-120">**[通訊埠]**</span><span class="sxs-lookup"><span data-stu-id="44b35-120">**Port**</span></span>|<span data-ttu-id="44b35-121">指定 SOAP 傳送處理常式使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="44b35-121">Specify the port the SOAP send handler uses.</span></span><br /><br /> <span data-ttu-id="44b35-122">這個屬性只需要一個值，如果**使用 proxy**已選取。</span><span class="sxs-lookup"><span data-stu-id="44b35-122">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="44b35-123">預設值： 80</span><span class="sxs-lookup"><span data-stu-id="44b35-123">Default Value: 80</span></span><br /><br /> <span data-ttu-id="44b35-124">類型：Long</span><span class="sxs-lookup"><span data-stu-id="44b35-124">Type: Long</span></span><br /><br /> <span data-ttu-id="44b35-125">最小值：0</span><span class="sxs-lookup"><span data-stu-id="44b35-125">Minimum value: 0</span></span><br /><br /> <span data-ttu-id="44b35-126">最大值： 65535</span><span class="sxs-lookup"><span data-stu-id="44b35-126">Maximum value: 65535</span></span>|  
    |<span data-ttu-id="44b35-127">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="44b35-127">**User name**</span></span>|<span data-ttu-id="44b35-128">指定要用於驗證的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="44b35-128">Specify the user name to use for authentication.</span></span><br /><br /> <span data-ttu-id="44b35-129">這個屬性只需要一個值，如果**使用 proxy**已選取。</span><span class="sxs-lookup"><span data-stu-id="44b35-129">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="44b35-130">類型：字串</span><span class="sxs-lookup"><span data-stu-id="44b35-130">Type: String</span></span><br /><br /> <span data-ttu-id="44b35-131">最小長度：00</span><span class="sxs-lookup"><span data-stu-id="44b35-131">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="44b35-132">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="44b35-132">Maximum length: 256</span></span>|  
    |<span data-ttu-id="44b35-133">**密碼**</span><span class="sxs-lookup"><span data-stu-id="44b35-133">**Password**</span></span>|<span data-ttu-id="44b35-134">指定要用於驗證的密碼。</span><span class="sxs-lookup"><span data-stu-id="44b35-134">Specify the password to use for authentication.</span></span><br /><br /> <span data-ttu-id="44b35-135">這個屬性只需要一個值，如果**使用 proxy**已選取。</span><span class="sxs-lookup"><span data-stu-id="44b35-135">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="44b35-136">類型：字串</span><span class="sxs-lookup"><span data-stu-id="44b35-136">Type: String</span></span><br /><br /> <span data-ttu-id="44b35-137">最小長度：00</span><span class="sxs-lookup"><span data-stu-id="44b35-137">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="44b35-138">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="44b35-138">Maximum length: 256</span></span>|  
  
5.  <span data-ttu-id="44b35-139">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="44b35-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b35-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44b35-140">See Also</span></span>  
 <span data-ttu-id="44b35-141">[設定 SOAP 配接器](../core/configuring-the-soap-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="44b35-141">[Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md) </span></span>  
 [<span data-ttu-id="44b35-142">發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="44b35-142">Publishing Web Services</span></span>](../core/publishing-web-services.md)