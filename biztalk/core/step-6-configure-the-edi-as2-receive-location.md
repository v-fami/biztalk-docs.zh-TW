---
title: 步驟 6： 設定 EDI-AS2 接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 167f8ba2-d38b-4088-863b-2bd90c2a12a2
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d5ec3a7c253ab37a76846962cb348cd8b203a23
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009847"
---
# <a name="step-6-configure-the-edi-as2-receive-location"></a><span data-ttu-id="06ba7-102">步驟 6： 設定 EDI-AS2 接收位置</span><span class="sxs-lookup"><span data-stu-id="06ba7-102">Step 6: Configure the EDI-AS2 Receive Location</span></span>
<span data-ttu-id="06ba7-103">![步驟 11-6](../core/media/tut-step6-of-11.gif "Tut_Step6_of_11")</span><span class="sxs-lookup"><span data-stu-id="06ba7-103">![Step 6 of 11](../core/media/tut-step6-of-11.gif "Tut_Step6_of_11")</span></span>  
  
 <span data-ttu-id="06ba7-104">在這個步驟中，您會設定從 Fabrikam 合作對象接收 EDI 訊息的單向接收位置。</span><span class="sxs-lookup"><span data-stu-id="06ba7-104">In this step, you set up a one-way receive location that receives the EDI message from the Fabrikam party.</span></span> <span data-ttu-id="06ba7-105">這個接收位置會使用 AS2EdiReceive 接收管線來處理內送的 EDI/AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="06ba7-105">This receive location uses the AS2EdiReceive receive pipeline to process the incoming EDI/AS2 message.</span></span> <span data-ttu-id="06ba7-106">sender.exe 應用程式將會透過 Contoso 虛擬目錄，利用 BTSHTTPReceive.dll ISAPI 延伸模組，將訊息傳送到接收位置。</span><span class="sxs-lookup"><span data-stu-id="06ba7-106">The message will be sent to the receive location by the sender.exe application through the Contoso virtual directory using the BTSHTTPReceive.dll ISAPI extension.</span></span>  
  
 <span data-ttu-id="06ba7-107">在本教學課程中，您將設定動態傳送埠，以非同步方式傳送 MDN 回應。</span><span class="sxs-lookup"><span data-stu-id="06ba7-107">In this tutorial, you will set up a dynamic send port to send the MDN response asynchronously.</span></span> <span data-ttu-id="06ba7-108">在這個案例中，您只需要單向的接收埠。</span><span class="sxs-lookup"><span data-stu-id="06ba7-108">In this scenario, only a one-way receive port is required.</span></span> <span data-ttu-id="06ba7-109">不過，您也可以變更 Sender.exe 來傳送指定同步 MDN 的 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="06ba7-109">However, you could also change Sender.exe to send an AS2 message specifying a synchronous MDN.</span></span> <span data-ttu-id="06ba7-110">這樣您就必須建立雙向的要求-回應接收埠來傳回 MDN。</span><span class="sxs-lookup"><span data-stu-id="06ba7-110">You would then have to create a two-way request response receive port to return the MDN.</span></span> <span data-ttu-id="06ba7-111">如需詳細資訊，請參閱 < 測試方案 > 一節的[逐步解說 (AS2): 使用同步 MDN 透過 AS2 接收的 EDI](../core/walkthrough-as2-receiving-edi-over-as2-with-a-synchronous-mdn.md)。</span><span class="sxs-lookup"><span data-stu-id="06ba7-111">For more information, see the "To test the solution" section of [Walkthrough (AS2): Receiving EDI over AS2 with a Synchronous MDN](../core/walkthrough-as2-receiving-edi-over-as2-with-a-synchronous-mdn.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="06ba7-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="06ba7-112">Prerequisites</span></span>  
 <span data-ttu-id="06ba7-113">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="06ba7-113">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-create-the-biztalk-http-receive-location"></a><span data-ttu-id="06ba7-114">若要建立 BizTalk HTTP 接收位置</span><span class="sxs-lookup"><span data-stu-id="06ba7-114">To create the BizTalk HTTP receive location</span></span>  
  
1. <span data-ttu-id="06ba7-115">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，在 [BizTalk Application 1] 節點中，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下 **單向接收埠**.</span><span class="sxs-lookup"><span data-stu-id="06ba7-115">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the BizTalk Application 1 node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2. <span data-ttu-id="06ba7-116">接收埠命名為**Receive_AS2**。</span><span class="sxs-lookup"><span data-stu-id="06ba7-116">Name the receive port as **Receive_AS2**.</span></span>  
  
3. <span data-ttu-id="06ba7-117">按一下 **接收位置**在主控台樹狀目錄中，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="06ba7-117">Click **Receive Locations** in the console tree, and then click **New**.</span></span>  
  
4. <span data-ttu-id="06ba7-118">在**接收位置屬性**對話方塊中，名稱您接收位置**Receive_AS2**，選取**HTTP**如**類型**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="06ba7-118">In the **Receive Location Properties** dialog box, name your receive location **Receive_AS2**, select **HTTP** for **Type**, and then click **Configure**.</span></span>  
  
5. <span data-ttu-id="06ba7-119">在  **HTTP 傳輸屬性**對話方塊方塊中，輸入 **/Contoso/BTSHTTPReceive.dll** for**虛擬目錄加 ISAPI 延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="06ba7-119">In the **HTTP Transport Properties** dialog box, enter **/Contoso/BTSHTTPReceive.dll** for **Virtual directory plus ISAPI extension**.</span></span> <span data-ttu-id="06ba7-120">清除**成功時傳回相互關聯控制代碼**，然後選取**擱置失敗的要求**。</span><span class="sxs-lookup"><span data-stu-id="06ba7-120">Clear **Return correlation handle on success** and select **Suspend failed requests**.</span></span> <span data-ttu-id="06ba7-121">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="06ba7-121">Click **OK**.</span></span>  
  
6. <span data-ttu-id="06ba7-122">選取  **AS2EdiReceive** for**接收管線**。</span><span class="sxs-lookup"><span data-stu-id="06ba7-122">Select **AS2EdiReceive** for the **Receive Pipeline**.</span></span> <span data-ttu-id="06ba7-123">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="06ba7-123">Click **OK**, and then click **OK** again.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="06ba7-124">AS2EdiReceive 接收管線會執行 AS2 解碼和 EDI 解譯。</span><span class="sxs-lookup"><span data-stu-id="06ba7-124">The AS2EdiReceive receive pipeline performs AS2 decoding and EDI disassembly.</span></span>  
  
7. <span data-ttu-id="06ba7-125">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**接收位置**在 [BizTalk Application 1] 節點中，以滑鼠右鍵按一下**Receive_AS2**，然後按一下 **啟用**.</span><span class="sxs-lookup"><span data-stu-id="06ba7-125">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **Receive Locations** under the BizTalk Application 1 node, right-click **Receive_AS2**, and then click **Enable**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="06ba7-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="06ba7-126">Next Steps</span></span>  
 <span data-ttu-id="06ba7-127">設定傳送埠 (**Send_Asynch_MDN**) 中所述，傳送埠以將非同步 MDN 傳回 Fabrikam[步驟 7： 設定 MDN 傳送埠](../core/step-7-configure-the-mdn-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="06ba7-127">You configure the send port (**Send_Asynch_MDN**) send port to send the asynchronous MDN back to Fabrikam, as described in [Step 7: Configure the MDN Send Port](../core/step-7-configure-the-mdn-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ba7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06ba7-128">See Also</span></span>  
 <span data-ttu-id="06ba7-129">[BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="06ba7-129">[How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md) </span></span>  
 [<span data-ttu-id="06ba7-130">為透過 AS2 的訊息設定接收埠</span><span class="sxs-lookup"><span data-stu-id="06ba7-130">Configuring a Receive Port for Messages over AS2</span></span>](../core/configuring-a-receive-port-for-messages-over-as2.md)