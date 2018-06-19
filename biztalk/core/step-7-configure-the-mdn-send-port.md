---
title: 步驟 7： 設定 MDN 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 983033ac-9d32-47c8-9bb8-b4161bcdf183
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0f70df6846553e2d64711f33e8c5a0b0e4d2cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277958"
---
# <a name="step-7-configure-the-mdn-send-port"></a><span data-ttu-id="ddd5d-102">步驟 7： 設定 MDN 傳送埠</span><span class="sxs-lookup"><span data-stu-id="ddd5d-102">Step 7: Configure the MDN Send Port</span></span>
<span data-ttu-id="ddd5d-103">![步驟 7 11](../core/media/tut-step7-of-11.gif "Tut_Step7_of_11")</span><span class="sxs-lookup"><span data-stu-id="ddd5d-103">![Step 7 of 11](../core/media/tut-step7-of-11.gif "Tut_Step7_of_11")</span></span>  
  
 <span data-ttu-id="ddd5d-104">在此步驟中，您將設定動態傳送埠傳送非同步 MDN \\_MDNToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-104">In this step, you set up a dynamic send port to send an asynchronous MDN to the \\_MDNToFabrikam folder.</span></span> <span data-ttu-id="ddd5d-105">此傳送埠會使用 AS2Send 傳送管線產生外寄 MDN 回應。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-105">This send port uses the AS2Send send pipeline to generate the outgoing MDN response.</span></span> <span data-ttu-id="ddd5d-106">由於這是動態傳送埠時，它會使用位址的訊息標頭中的回條傳遞選項列中將訊息路由至\\_MDNToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-106">Since this is a dynamic send port, it will use the address in the Receipt-Delivery-Option line in the header of the message to route the message to the \\_MDNToFabrikam folder.</span></span> <span data-ttu-id="ddd5d-107">該位址是 Fabrikam 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-107">That address is the Fabrikam virtual directory.</span></span> <span data-ttu-id="ddd5d-108">與該虛擬目錄相關的 Default.aspx.cs 檔案會以 .msg 副檔名建立 MDN，並傳送檔案至目的資料夾 (也是於 Receipt-Delivery-Option 中所指定)。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-108">The Default.aspx.cs file associated with that virtual directory builds the MDN with an .msg extension, and sends the file to the destination folder (which is also specified in Receipt-Delivery-Option).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddd5d-109">您也可以透過用協議設定覆寫訊息設定，將協議設定成將 MDN 傳送至其他位址。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-109">You can also configure the agreement to send the MDN to another address, by overriding the message settings with the agreement settings.</span></span> <span data-ttu-id="ddd5d-110">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="ddd5d-110">For more information, see</span></span>  
  
 <span data-ttu-id="ddd5d-111">在這個範例中，會使用動態傳送埠來傳送 MDN；但是，您也可以使用靜態傳送埠將 MDN 傳送至靜態位址。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-111">In this example the MDN is sent using a dynamic send port; however you can also use a static send port to send the MDN to a static address.</span></span> <span data-ttu-id="ddd5d-112">如需詳細資訊，請參閱[設定透過 AS2 之非同步 Mdn 的靜態傳送埠](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)和[設定透過 AS2 之非同步 Mdn 的動態傳送埠](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-112">For more information, see [Configuring a Static Send Port for Asynchronous MDNs over AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md) and [Configuring a Dynamic Send Port for Asynchronous MDNs over AS2](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ddd5d-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="ddd5d-113">Prerequisites</span></span>  
 <span data-ttu-id="ddd5d-114">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-114">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-create-the-sendasyncmdn-send-port"></a><span data-ttu-id="ddd5d-115">若要建立 Send_Async_MDN 傳送埠</span><span class="sxs-lookup"><span data-stu-id="ddd5d-115">To create the Send_Async_MDN send port</span></span>  
  
1.  <span data-ttu-id="ddd5d-116">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，在 [BizTalk Application 1] 節點中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **動態單向傳送連接埠**.</span><span class="sxs-lookup"><span data-stu-id="ddd5d-116">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the BizTalk Application 1 node, right-click **Send Ports**, point to **New**, and then click **Dynamic One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="ddd5d-117">在**傳送埠屬性**對話方塊中，將傳送埠為**Send_Async_MDN**。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-117">In the **Send Port Properties** dialog box, name the send port as **Send_Async_MDN**.</span></span>  
  
3.  <span data-ttu-id="ddd5d-118">選取**AS2Send**如**傳送管線**。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-118">Select **AS2Send** for **Send pipeline**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ddd5d-119">要使用 AS2Send 管線是因為 MDN 完全不需要 EDI 處理。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-119">The AS2Send pipeline is used because no EDI processing is required for the MDN.</span></span>  
  
4.  <span data-ttu-id="ddd5d-120">按一下**篩選**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-120">Click **Filters** in the console tree.</span></span> <span data-ttu-id="ddd5d-121">在 [篩選] 窗格中，選取**EdiIntAS.IsAS2AsynchronousMdn**如**屬性**，  **==** 的**運算子**，然後輸入**True**如**值**。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-121">In the Filters pane, select **EdiIntAS.IsAS2AsynchronousMdn** for **Property**, **==** for **Operator**, and enter **True** for **Value**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ddd5d-122">此篩選條件可確保動態傳送埠僅會從 MessageBox 挑選非同步 MDN。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-122">This filter ensures that the dynamic send port only picks up asynchronous MDNs from the MessageBox.</span></span>  
  
5.  <span data-ttu-id="ddd5d-123">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-123">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="ddd5d-124">在**傳送埠**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**Send_Async_MDN**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-124">In the **Send Ports** pane of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Send_Async_MDN**, and then click **Start**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ddd5d-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ddd5d-125">Next Steps</span></span>  
 <span data-ttu-id="ddd5d-126">設定傳送埠 (**Send_Async_997**) 將 997 通知送回給 Fabrikam，如中所述[步驟 8： 設定 997 傳送埠](../core/step-8-configure-the-997-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="ddd5d-126">You configure the send port (**Send_Async_997**) to send the 997 acknowledgement back to Fabrikam, as described in [Step 8: Configure the 997 Send Port](../core/step-8-configure-the-997-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd5d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddd5d-127">See Also</span></span>  
 <span data-ttu-id="ddd5d-128">[BizTalk Server 傳送 AS2 訊息的方式](../core/how-biztalk-server-sends-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="ddd5d-128">[How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md) </span></span>  
 <span data-ttu-id="ddd5d-129">[設定透過 AS2 之非同步 Mdn 的靜態傳送埠](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md) </span><span class="sxs-lookup"><span data-stu-id="ddd5d-129">[Configuring a Static Send Port for Asynchronous MDNs over AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md) </span></span>  
 [<span data-ttu-id="ddd5d-130">透過 AS2 的訊息設定動態傳送埠</span><span class="sxs-lookup"><span data-stu-id="ddd5d-130">Configuring a Dynamic Send Port for Messages over AS2</span></span>](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)