---
title: 步驟 5： 設定接收埠和接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43fc8d12-5fde-4ddf-a7f0-770f078ba66b
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8ec436657aefaceb71207d37808936aa6eaa1a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277950"
---
# <a name="step-5-configure-a-receive-port-and-receive-location"></a><span data-ttu-id="fc3b8-102">步驟 5： 設定接收埠和接收位置</span><span class="sxs-lookup"><span data-stu-id="fc3b8-102">Step 5: Configure a Receive Port and Receive Location</span></span>
<span data-ttu-id="fc3b8-103">![步驟 5 之 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")</span><span class="sxs-lookup"><span data-stu-id="fc3b8-103">![Step 5 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")</span></span>  
  
 <span data-ttu-id="fc3b8-104">在此步驟中，您將設定接收埠和接收位置，以在為 Fabrikam 合作對象設定的資料夾中接收 850 訊息。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-104">In this step you configure a receive port and receive location for receiving the 850 message in the folder set up for the Fabrikam party.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fc3b8-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="fc3b8-105">Prerequisites</span></span>  
 <span data-ttu-id="fc3b8-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-a-receive-port-and-receive-location-for-receiving-the-850-message"></a><span data-ttu-id="fc3b8-107">若要設定用來接收 850 訊息的接收埠和接收位置</span><span class="sxs-lookup"><span data-stu-id="fc3b8-107">To configure a receive port and receive location for receiving the 850 message</span></span>  
  
1.  <span data-ttu-id="fc3b8-108">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開  **BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，然後**BizTalk應用程式 1**。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-108">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and then **BizTalk Application 1**.</span></span> <span data-ttu-id="fc3b8-109">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-109">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="fc3b8-110">在 [接收埠屬性] 對話方塊中**名稱**欄位中，輸入`ReceiveEDI_fromTHEM_A`。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-110">In the Receive Port Properties dialog box, in the **Name** field, enter `ReceiveEDI_fromTHEM_A`.</span></span>  
  
3.  <span data-ttu-id="fc3b8-111">按一下**接收位置**在主控台樹狀目錄中，然後按一下**新增**在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-111">Click **Receive Locations** in the console tree, and then click **New** in the right-hand pane.</span></span>  
  
4.  <span data-ttu-id="fc3b8-112">在**接收位置屬性**對話方塊中，於**名稱**欄位中，輸入`fromTHEM_4010_850`。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-112">In the **Receive Location Properties** dialog box, in the **Name** field, enter `fromTHEM_4010_850`.</span></span>  
  
5.  <span data-ttu-id="fc3b8-113">如**類型**，選取**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-113">For **Type**, select **FILE**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc3b8-114">接收位置的傳輸類型是 FILE，因為測試訊息是傳送到資料夾的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-114">The transport type of the receive location is FILE because the test message is a flat file delivered into a folder.</span></span>  
  
6.  <span data-ttu-id="fc3b8-115">在**FILE 傳輸屬性**對話方塊中，按一下 **瀏覽**旁邊**接收資料夾**欄位。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-115">In the **FILE Transport Properties** dialog box, click the **Browse** button next to the **Receive folder** field.</span></span> <span data-ttu-id="fc3b8-116">在**瀏覽資料夾**對話方塊中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-116">In the **Browse for Folder** dialog box, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="fc3b8-117">在**FILE 傳輸屬性**對話方塊中，變更**檔案遮罩**至 **\*.txt**按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-117">In the **FILE Transport Properties** dialog box, change the **File mask** to **\*.txt** and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc3b8-118">檔案遮罩之所以設為 \*.txt，是因為輸入測試訊息是文字檔案 SamplePO.txt。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-118">The file mask is set to \*.txt because the input test message is a text file, SamplePO.txt.</span></span>  
  
8.  <span data-ttu-id="fc3b8-119">在**接收位置屬性**對話方塊中，於**接收管線**欄位中，選取**EdiReceive**。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-119">In the **Receive Location Properties** dialog box, in the **Receive Pipeline** field, select **EdiReceive**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc3b8-120">用來接收 EDI 交換 (除了透過 AS2 傳輸所傳送的交換之外) 的接收管線是 EdiReceive 管線</span><span class="sxs-lookup"><span data-stu-id="fc3b8-120">The receive pipeline used to receive EDI interchanges, except for those delivered over the AS2 transport, is the EdiReceive pipeline.</span></span> <span data-ttu-id="fc3b8-121">(透過 AS2 傳輸所傳送的 EDI 交換則使用 AS2EdiReceive 接收管線接收)。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-121">(The AS2EdiReceive receive pipeline is used to receive EDI interchanges delivered over the AS2 transport.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc3b8-122">如果接收管線的下拉式清單未列有 EdiReceive，表示您的應用程式可能沒有 BizTalk EDI 應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-122">If EdiReceive is not listed in the drop-down list for receive pipeline, your application may not have a reference to the BizTalk EDI Application.</span></span> <span data-ttu-id="fc3b8-123">若要加入參考，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-123">To add the reference, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
9. <span data-ttu-id="fc3b8-124">按一下**確定**，然後按一下 **確定**一次。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-124">Click **OK**, and then click **OK** again.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc3b8-125">擁有 BizTalk 服務登入權限的帳戶也應獲得與 fromTHEM_4010_850 接收位置相關聯之接收資料夾 ([!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\ProcessEDI_TestLocations\fromTHEM) 的完整存取權限。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-125">The account that has log-on privileges for the BizTalk service should also be granted full access permissions for the receive folder associated with the fromTHEM_4010_850 receive location ([!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\ProcessEDI_TestLocations\fromTHEM).</span></span> <span data-ttu-id="fc3b8-126">如果沒有，則當您嘗試啟用接收位置時，會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-126">If not, you will receive an error when attempting to enable the receive location.</span></span> <span data-ttu-id="fc3b8-127">若要變更接收資料夾的存取權限，請移至 安全性 索引標籤中**屬性**為該資料夾，在 Windows 檔案總管 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-127">To change the access permissions for the receive folder, go to the Security tab in the **Properties** dialog box for that folder in Windows Explorer.</span></span>  
  
10. <span data-ttu-id="fc3b8-128">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **接收位置**，以滑鼠右鍵按一下**fromTHEM_4010_850**，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-128">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **Receive Locations**, right-click **fromTHEM_4010_850**, and then click **Enable**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fc3b8-129">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fc3b8-129">Next Steps</span></span>  
 <span data-ttu-id="fc3b8-130">設定傳送埠 (**toOrderSystem**) 中所述，850 訊息傳送到 OrderSystem，[步驟 6： 設定傳送埠以傳送資料至貴組織](../core/step-6-configure-a-send-port-to-send-data-to-your-organization.md)。</span><span class="sxs-lookup"><span data-stu-id="fc3b8-130">You configure the send port (**toOrderSystem**) to send the 850 message to OrderSystem, as described in [Step 6: Configure a Send Port to Send Data to Your Organization](../core/step-6-configure-a-send-port-to-send-data-to-your-organization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc3b8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc3b8-131">See Also</span></span>  
 [<span data-ttu-id="fc3b8-132">設定連接埠來接收 EDI 訊息和通知</span><span class="sxs-lookup"><span data-stu-id="fc3b8-132">Configuring a Port to Receive EDI Messages and Acknowledgments</span></span>](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md)