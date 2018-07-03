---
title: 如何設定 SOAP 傳送處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4bcbe39861c37db348e1e37752fbad6d9616033
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005479"
---
# <a name="how-to-configure-a-soap-send-handler"></a><span data-ttu-id="d4364-102">如何設定 SOAP 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="d4364-102">How to Configure a SOAP Send Handler</span></span>
<span data-ttu-id="d4364-103">使用下列程序，來設定 SOAP 傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="d4364-103">Use the following procedure to configure the SOAP send handler.</span></span>  

> [!CAUTION]
>  <span data-ttu-id="d4364-104">當使用 HTTP 或 SOAP 配接器處理常式時，建議您安裝這些處理常式的主控件執行個體，在 Microsoft[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="d4364-104">When using HTTP or SOAP adapter handlers, it is recommended that you install the host instances for these handlers on Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]computers.</span></span>  

### <a name="to-change-global-variables-for-a-soap-send-handler"></a><span data-ttu-id="d4364-105">變更 SOAP 傳送處理常式的全域變數</span><span class="sxs-lookup"><span data-stu-id="d4364-105">To change global variables for a SOAP send handler</span></span>  

1. <span data-ttu-id="d4364-106">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="d4364-106">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  

2. <span data-ttu-id="d4364-107">在展開的配接器清單中，按一下**SOAP**，在右窗格以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d4364-107">In the expanded adapter list, click **SOAP**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  

3. <span data-ttu-id="d4364-108">在 **配接器處理常式屬性**對話方塊的 **一般**索引標籤**主機名稱**清單中，選取與其相關聯的接收處理常式的主控。</span><span class="sxs-lookup"><span data-stu-id="d4364-108">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  

4. <span data-ttu-id="d4364-109">在  **Proxy**索引標籤上，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="d4364-109">On the **Proxy** tab, do the following.</span></span>  


   |   <span data-ttu-id="d4364-110">使用</span><span class="sxs-lookup"><span data-stu-id="d4364-110">Use this</span></span>    |                                                                                                                  <span data-ttu-id="d4364-111">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="d4364-111">To do this</span></span>                                                                                                                   |
   |---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | <span data-ttu-id="d4364-112">**使用 Proxy**</span><span class="sxs-lookup"><span data-stu-id="d4364-112">**Use proxy**</span></span> |                                                                                          <span data-ttu-id="d4364-113">指示 SOAP 傳送處理常式是否要使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d4364-113">Indicate whether the SOAP send handler uses a proxy server.</span></span>                                                                                          |
   |  <span data-ttu-id="d4364-114">**Server**</span><span class="sxs-lookup"><span data-stu-id="d4364-114">**Server**</span></span>   |                  <span data-ttu-id="d4364-115">指定 Proxy 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4364-115">Specify the name of the proxy server.</span></span><br /><br /> <span data-ttu-id="d4364-116">此屬性只需要一個值，如果**使用 proxy**已選取。</span><span class="sxs-lookup"><span data-stu-id="d4364-116">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="d4364-117">類型：字串</span><span class="sxs-lookup"><span data-stu-id="d4364-117">Type: String</span></span><br /><br /> <span data-ttu-id="d4364-118">最小長度：00</span><span class="sxs-lookup"><span data-stu-id="d4364-118">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="d4364-119">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="d4364-119">Maximum length: 256</span></span>                   |
   |   <span data-ttu-id="d4364-120">**通訊埠**</span><span class="sxs-lookup"><span data-stu-id="d4364-120">**Port**</span></span>    | <span data-ttu-id="d4364-121">指定 SOAP 傳送處理常式使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d4364-121">Specify the port the SOAP send handler uses.</span></span><br /><br /> <span data-ttu-id="d4364-122">此屬性只需要一個值，如果**使用 proxy**已選取。</span><span class="sxs-lookup"><span data-stu-id="d4364-122">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="d4364-123">預設值： 80</span><span class="sxs-lookup"><span data-stu-id="d4364-123">Default Value: 80</span></span><br /><br /> <span data-ttu-id="d4364-124">類型：Long</span><span class="sxs-lookup"><span data-stu-id="d4364-124">Type: Long</span></span><br /><br /> <span data-ttu-id="d4364-125">最小值：0</span><span class="sxs-lookup"><span data-stu-id="d4364-125">Minimum value: 0</span></span><br /><br /> <span data-ttu-id="d4364-126">最大值： 65535</span><span class="sxs-lookup"><span data-stu-id="d4364-126">Maximum value: 65535</span></span> |
   | <span data-ttu-id="d4364-127">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="d4364-127">**User name**</span></span> |             <span data-ttu-id="d4364-128">指定要用於驗證的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="d4364-128">Specify the user name to use for authentication.</span></span><br /><br /> <span data-ttu-id="d4364-129">此屬性只需要一個值，如果**使用 proxy**已選取。</span><span class="sxs-lookup"><span data-stu-id="d4364-129">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="d4364-130">類型：字串</span><span class="sxs-lookup"><span data-stu-id="d4364-130">Type: String</span></span><br /><br /> <span data-ttu-id="d4364-131">最小長度：00</span><span class="sxs-lookup"><span data-stu-id="d4364-131">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="d4364-132">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="d4364-132">Maximum length: 256</span></span>             |
   | <span data-ttu-id="d4364-133">**密碼**</span><span class="sxs-lookup"><span data-stu-id="d4364-133">**Password**</span></span>  |             <span data-ttu-id="d4364-134">指定要用於驗證的密碼。</span><span class="sxs-lookup"><span data-stu-id="d4364-134">Specify the password to use for authentication.</span></span><br /><br /> <span data-ttu-id="d4364-135">此屬性只需要一個值，如果**使用 proxy**已選取。</span><span class="sxs-lookup"><span data-stu-id="d4364-135">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="d4364-136">類型：字串</span><span class="sxs-lookup"><span data-stu-id="d4364-136">Type: String</span></span><br /><br /> <span data-ttu-id="d4364-137">最小長度：00</span><span class="sxs-lookup"><span data-stu-id="d4364-137">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="d4364-138">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="d4364-138">Maximum length: 256</span></span>              |


5. <span data-ttu-id="d4364-139">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d4364-139">Click **OK**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="d4364-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4364-140">See Also</span></span>  
 <span data-ttu-id="d4364-141">[設定 SOAP 配接器](../core/configuring-the-soap-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d4364-141">[Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md) </span></span>  
 [<span data-ttu-id="d4364-142">發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="d4364-142">Publishing Web Services</span></span>](../core/publishing-web-services.md)