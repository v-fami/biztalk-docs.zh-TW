---
title: 建立連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports, creating
- receive ports
- creating, send ports
- creating, ports
- Configuration database [BizTalk Server], connecting
- receive ports, creating
- send ports
- send ports, creating
ms.assetid: 4f99f884-5b84-4f9f-8cec-dd5da259ba7f
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d109e102ada04e673fa5eddc3010201b266a150
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015125"
---
# <a name="creating-ports"></a><span data-ttu-id="e193c-102">建立連接埠</span><span class="sxs-lookup"><span data-stu-id="e193c-102">Creating Ports</span></span>
<span data-ttu-id="e193c-103">請使用下列程序，為「單一登入」建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="e193c-103">Use the following procedures to create [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports for Single Sign-on.</span></span>  
  
## <a name="creating-a-send-port"></a><span data-ttu-id="e193c-104">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="e193c-104">Creating a Send Port</span></span>  
  
#### <a name="to-create-a-send-port"></a><span data-ttu-id="e193c-105">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="e193c-105">To create a send port</span></span>  
  
1.  <span data-ttu-id="e193c-106">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="e193c-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="e193c-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="e193c-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="e193c-108">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e193c-108">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="e193c-109">輸入傳送埠名稱，例如`SSOSendToPeopleSoft`。</span><span class="sxs-lookup"><span data-stu-id="e193c-109">Type a name for the send port, for example, `SSOSendToPeopleSoft`.</span></span>  
  
    2.  <span data-ttu-id="e193c-110">從**類型**下拉式清單中，選取**PeopleSoft**。</span><span class="sxs-lookup"><span data-stu-id="e193c-110">From the **Type** drop-down list, select **PeopleSoft**.</span></span>  
  
    3.  <span data-ttu-id="e193c-111">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="e193c-111">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="e193c-112">從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="e193c-112">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="e193c-113">從**接收管線**下拉式清單中，選取 **[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="e193c-113">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="e193c-114">按一下**設定**以設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e193c-114">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="e193c-115">在**PeopleSoft 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e193c-115">In the **PeopleSoft Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="e193c-116">展開**配接器必要屬性**，並輸入**應用程式伺服器路徑**， **JAVA_HOME**，**使用者名**， **密碼**，以及 Jar 檔案，以連接至 Peoplesoft 系統。</span><span class="sxs-lookup"><span data-stu-id="e193c-116">Expand **Adapter Required Properties**, and enter **Application Server Path**, **JAVA_HOME**, **user name**, **password**, and the Jar file for connecting into the Peoplesoft system.</span></span>  
  
         <span data-ttu-id="e193c-117">您不需要設定登入資訊。</span><span class="sxs-lookup"><span data-stu-id="e193c-117">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="e193c-118">在此清單中，選取您建立用來代表 PeopleSoft 系統的 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="e193c-118">In the list, select the SSO affiliate application you created to represent the PeopleSoft system.</span></span>  
  
    3.  <span data-ttu-id="e193c-119">如**使用 SSO**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="e193c-119">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="e193c-120">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e193c-120">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="e193c-121">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e193c-121">Click **OK**.</span></span>  
  
## <a name="creating-a-receive-port"></a><span data-ttu-id="e193c-122">建立接收埠</span><span class="sxs-lookup"><span data-stu-id="e193c-122">Creating a Receive Port</span></span>  
  
#### <a name="to-create-a-receive-port"></a><span data-ttu-id="e193c-123">建立接收埠</span><span class="sxs-lookup"><span data-stu-id="e193c-123">To create a receive port</span></span>  
  
1.  <span data-ttu-id="e193c-124">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="e193c-124">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="e193c-125">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="e193c-125">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Ports**.</span></span>  
  
3.  <span data-ttu-id="e193c-126">在**接收埠屬性**視窗，請在**一般**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e193c-126">In the **Receive Port Properties** window, on the **General** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="e193c-127">在**名稱**欄位中，輸入`ReceiveFromTIBCOEMS`。</span><span class="sxs-lookup"><span data-stu-id="e193c-127">In the **Name** field, type `ReceiveFromTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="e193c-128">在**驗證**群組方塊中，指定使用驗證時，如何處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="e193c-128">In the **Authentication** group box, specify how messages are handled when using authentication.</span></span>  
  
    3.  <span data-ttu-id="e193c-129">選取**啟用的路由失敗訊息**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e193c-129">Select the **Enable routing for failed messages** checkbox.</span></span>  
  
4.  <span data-ttu-id="e193c-130">在**接收位置**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e193c-130">On the **Receive Locations** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="e193c-131">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="e193c-131">Click **New**.</span></span>  
  
    2.  <span data-ttu-id="e193c-132">在**接收位置**視窗，請在**一般**頁面上，輸入**名稱**接收位置。</span><span class="sxs-lookup"><span data-stu-id="e193c-132">In the **Receive Locations** window, on the **General** page, type the **Name** of the receive location.</span></span>  
  
    3.  <span data-ttu-id="e193c-133">從**類型**下拉式清單中，選取傳輸類型，以及從**接收處理常式**下拉式清單中，選取傳輸位址。</span><span class="sxs-lookup"><span data-stu-id="e193c-133">From the **Type** drop-down list, select the transport type, and from the **Receive handler** drop-down list, select the transport address.</span></span>  
  
    4.  <span data-ttu-id="e193c-134">從**接收管線**下拉式清單中，選取接收管線。</span><span class="sxs-lookup"><span data-stu-id="e193c-134">From the **Receive pipeline** drop-down list, select the receive pipeline.</span></span>  
  
    5.  <span data-ttu-id="e193c-135">在**排程**頁面上，選取**開始日期**和**結束日期**限制接收文件。</span><span class="sxs-lookup"><span data-stu-id="e193c-135">On the **Schedule** page, select the **Start date** and the **End date** to restrict receiving documents.</span></span>  
  
    6.  <span data-ttu-id="e193c-136">選取**啟用服務窗口**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e193c-136">Select the **Enable service window** checkbox.</span></span>  
  
    7.  <span data-ttu-id="e193c-137">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e193c-137">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="e193c-138">在**輸入對應**頁面上，選取輸入的對應轉換文件上選取的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e193c-138">On the **Inbound Maps** page, select the inbound maps for transforming documents on the selected port.</span></span>  
  
6.  <span data-ttu-id="e193c-139">在**追蹤**頁面上，選取所需的追蹤訊息內文和追蹤訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="e193c-139">On the **Tracking** page, select the desired tracking message bodies and tracking message properties.</span></span>  
  
7.  <span data-ttu-id="e193c-140">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e193c-140">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e193c-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e193c-141">See Also</span></span>  
 [<span data-ttu-id="e193c-142">保護配接器</span><span class="sxs-lookup"><span data-stu-id="e193c-142">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)