---
title: 建立傳送埠和接收埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, receive ports
- adapters [JD Edwards OneWorld adapters], receive ports
- creating, receive ports [JD Edwards OneWorld adapters]
- send ports, creating [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], send ports
- adapters [JD Edwards OneWorld adapters], transport properties
- JD Edwards OneWorld adapters, send ports
- JD Edwards OneWorld adapters, transport properties
- receive ports, creating [JD Edwards OneWorld adapters]
- creating, send ports [JD Edwards OneWorld adapters]
ms.assetid: fb4ca8b1-40d9-4beb-a791-554086f8ca98
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da4b117ca2d032ef1dc10731128acca903a51790
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014029"
---
# <a name="creating-send-and-receive-ports"></a><span data-ttu-id="e9668-102">建立傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="e9668-102">Creating Send and Receive Ports</span></span>
<span data-ttu-id="e9668-103">使用下列程序為 BizTalk Adapter for JD Edwards OneWorld 建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="e9668-103">Use the following procedures to create [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports for BizTalk Adapter for JD Edwards OneWorld.</span></span>  
  
## <a name="creating-a-port"></a><span data-ttu-id="e9668-104">建立連接埠</span><span class="sxs-lookup"><span data-stu-id="e9668-104">Creating a Port</span></span>  
  
#### <a name="to-create-a-send-port"></a><span data-ttu-id="e9668-105">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="e9668-105">To create a send port</span></span>  
  
1.  <span data-ttu-id="e9668-106">按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e9668-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e9668-107">在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，並展開**應用程式**，然後展開您要建立傳送埠的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9668-107">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, and expand **Applications**, and then expand the application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="e9668-108">以滑鼠右鍵按一下**傳送埠**按一下**新增**，然後按一下 **靜態請求-回應連接埠**。</span><span class="sxs-lookup"><span data-stu-id="e9668-108">Right-click **Send Ports** and click **New**, and then click **Static Solicit-Response Port**.</span></span>  
  
4.  <span data-ttu-id="e9668-109">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e9668-109">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    -   <span data-ttu-id="e9668-110">在**名稱**方塊中，輸入傳送埠名稱 (例如， `SSOSendToJDE OneWorld`)。</span><span class="sxs-lookup"><span data-stu-id="e9668-110">In the **Name** box, type a send port name (for example, `SSOSendToJDE OneWorld`).</span></span>  
  
    -   <span data-ttu-id="e9668-111">從**類型**下拉式清單中，選取**JDEdwards**。</span><span class="sxs-lookup"><span data-stu-id="e9668-111">From the **Type** drop-down list, select **JDEdwards**.</span></span>  
  
    -   <span data-ttu-id="e9668-112">從**傳送處理常式**下拉式清單中，選取傳送處理常式位址。</span><span class="sxs-lookup"><span data-stu-id="e9668-112">From the **Send handler** drop-down list, select the send handler address.</span></span>  
  
    -   <span data-ttu-id="e9668-113">如**傳送管線**，選取**Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="e9668-113">For the **Send Pipeline**, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    -   <span data-ttu-id="e9668-114">如**接收管線**，選取 **[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="e9668-114">For the **Receive Pipeline**, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
5.  <span data-ttu-id="e9668-115">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e9668-115">Click **OK**.</span></span>  
  
## <a name="creating-a-receive-port"></a><span data-ttu-id="e9668-116">建立接收埠</span><span class="sxs-lookup"><span data-stu-id="e9668-116">Creating a Receive Port</span></span>  
  
#### <a name="to-create-a-receive-port"></a><span data-ttu-id="e9668-117">建立接收埠</span><span class="sxs-lookup"><span data-stu-id="e9668-117">To create a receive port</span></span>  
  
1.  <span data-ttu-id="e9668-118">按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e9668-118">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e9668-119">在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，並展開**應用程式**，然後展開您要建立傳送埠的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9668-119">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, and expand **Applications**, and then expand the application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="e9668-120">以滑鼠右鍵按一下**接收埠**按一下**新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="e9668-120">Right-click **Receive Ports** and click **New**, and then click **One-way Receive Port**.</span></span>  
  
     <span data-ttu-id="e9668-121">在**單向接收埠屬性**畫面上，在**名稱**欄位中，輸入`ReceiveFromHttp`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e9668-121">On the **One-Way Receive Port Properties** screen, in the **Name** field, type `ReceiveFromHttp`, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="e9668-122">輸入中的下列資訊**單向接收埠屬性**視窗：</span><span class="sxs-lookup"><span data-stu-id="e9668-122">Enter the following information in the **One-way Receive Port Properties** window:</span></span>  
  
    -   <span data-ttu-id="e9668-123">在**名稱**欄位中，輸入`ReceiveFromHTTP`。</span><span class="sxs-lookup"><span data-stu-id="e9668-123">In the **Name** field, type `ReceiveFromHTTP`.</span></span>  
  
    -   <span data-ttu-id="e9668-124">如**傳輸類型**，選取**HTTP**。</span><span class="sxs-lookup"><span data-stu-id="e9668-124">For the **Transport Type**, select **HTTP**.</span></span>  
  
5.  <span data-ttu-id="e9668-125">按一下 [位址 (URI)] 中的省略符號 (? 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e9668-125">Click the ellipsis (…) button in the address (URI).</span></span>  
  
     ![](../core/media/siebeladapter-32-ssodemo-httptransport.gif "SiebelAdapter_32_SSODemo_HTTPTransport")  
  
    1.  <span data-ttu-id="e9668-126">將 [虛擬目錄加 ISAPI 延伸模組] 設定為 /mySSODemo/BTSHTTPReceive.dll。</span><span class="sxs-lookup"><span data-stu-id="e9668-126">Set the Virtual directory plus ISAPI extension, /mySSODemo/BTSHTTPReceive.dll.</span></span>  
  
    2.  <span data-ttu-id="e9668-127">選取**成功時傳回相互關聯控制代碼**。</span><span class="sxs-lookup"><span data-stu-id="e9668-127">Select **Return correlation handle on success**.</span></span>  
  
    3.  <span data-ttu-id="e9668-128">選取**使用單一登入**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e9668-128">Select **Use Single Sign-On**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="e9668-129">在**接收處理常式**下拉式清單中，選取**BizTalkServerIsolatedHost**。</span><span class="sxs-lookup"><span data-stu-id="e9668-129">In the **Receive Handler** drop-down list, select **BizTalkServerIsolatedHost**.</span></span>  
  
     ![](../core/media/siebeladapter-33-ssodemo-receivelocationproperty.gif "SiebelAdapter_33_SSODemo_ReceiveLocationProperty")  
  
7.  <span data-ttu-id="e9668-130">如**接收管線**，選取**microsoft.biztalk.defaultpiplelines.xmlreceive**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e9668-130">For the **Receive Pipeline**, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9668-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9668-131">See Also</span></span>  
 <span data-ttu-id="e9668-132">[將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="e9668-132">[Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span></span>  
 <span data-ttu-id="e9668-133">[將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="e9668-133">[Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span></span>  
 [<span data-ttu-id="e9668-134">在配接器的安全性</span><span class="sxs-lookup"><span data-stu-id="e9668-134">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)