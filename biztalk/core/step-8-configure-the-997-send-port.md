---
title: 步驟 8： 設定 997 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4780c491-9f1a-4f13-b346-6a2e1801ec09
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd203912dbf77c3e677f8f1180ba312c02829699
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022756"
---
# <a name="step-8-configure-the-997-send-port"></a><span data-ttu-id="adba7-102">步驟 8： 設定 997 傳送埠</span><span class="sxs-lookup"><span data-stu-id="adba7-102">Step 8: Configure the 997 Send Port</span></span>
<span data-ttu-id="adba7-103">![步驟 11-8](../core/media/tut-step8-of-11.gif "Tut_Step8_of_11")</span><span class="sxs-lookup"><span data-stu-id="adba7-103">![Step 8 of 11](../core/media/tut-step8-of-11.gif "Tut_Step8_of_11")</span></span>  
  
 <span data-ttu-id="adba7-104">在此步驟中，您會設定傳送埠，以將 997 訊息傳送給夥伴。</span><span class="sxs-lookup"><span data-stu-id="adba7-104">In this step, you set up a send port to send the 997 message to the partner.</span></span> <span data-ttu-id="adba7-105">這個傳送埠會使用 AS2EdiSend 傳送管線，將 EDIINT/AS2 編碼的 997 通知傳送至 _997ToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="adba7-105">This send port uses the AS2EdiSend send pipeline to transport an EDIINT/AS2-encoded 997 acknowledgment to the _997ToFabrikam folder.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="adba7-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="adba7-106">Prerequisites</span></span>  
 <span data-ttu-id="adba7-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="adba7-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-create-the-sendasync997-send-port"></a><span data-ttu-id="adba7-108">若要建立 Send_Async_997 傳送埠</span><span class="sxs-lookup"><span data-stu-id="adba7-108">To create the Send_Async_997 send port</span></span>  
  
1. <span data-ttu-id="adba7-109">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，在 [BizTalk Application 1] 節點中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**.</span><span class="sxs-lookup"><span data-stu-id="adba7-109">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the BizTalk Application 1 node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="adba7-110">使用靜態單向傳送埠的原因是，Fabrikam 合作對象並沒有設定 MDN 做為 AS2 訊息接收者。</span><span class="sxs-lookup"><span data-stu-id="adba7-110">You will use a static one-way send port because no MDN has been set up for the Fabrikam party as an AS2 message receiver.</span></span>  
  
2. <span data-ttu-id="adba7-111">在 **傳送埠屬性**對話方塊方塊中，將傳送埠命名**Send_Async_997**。</span><span class="sxs-lookup"><span data-stu-id="adba7-111">In the **Send Port Properties** dialog box, name your send port **Send_Async_997**.</span></span> <span data-ttu-id="adba7-112">選取  **HTTP** for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="adba7-112">Select **HTTP** for **Type**, and then click **Configure**.</span></span>  
  
3. <span data-ttu-id="adba7-113">在 [ **HTTP 傳輸屬性**] 對話方塊中，如**目的地 URL**，輸入`http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam`。</span><span class="sxs-lookup"><span data-stu-id="adba7-113">In the **HTTP Transport Properties** dialog box, for **Destination URL**, enter `http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam`.</span></span> <span data-ttu-id="adba7-114">清除**啟用區塊編碼**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="adba7-114">Clear **Enable chunked encoding** and then click **OK**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="adba7-115">**目的地 URL**設定可確保傳送埠會將 997 訊息傳送至 Fabrikam 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="adba7-115">The **Destination URL** setting ensures that the send port will send the 997 message to the Fabrikam virtual directory.</span></span> <span data-ttu-id="adba7-116">與該虛擬目錄相關的 Default.aspx.cs 檔案會以 .msg 副檔名建立 997，並將它傳送至目的資料夾。</span><span class="sxs-lookup"><span data-stu-id="adba7-116">The Default.aspx.cs file associated with that virtual directory builds the 997 with an .msg extension, and sends it to the destination folder.</span></span>  
  
4. <span data-ttu-id="adba7-117">在 **傳送埠屬性**對話方塊中，選取**AS2EdiSend** for**傳送管線**。</span><span class="sxs-lookup"><span data-stu-id="adba7-117">In the **Send Port Properties** dialog box, select **AS2EdiSend** for **Send Pipeline**.</span></span>  
  
5. <span data-ttu-id="adba7-118">按一下 **篩選器**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="adba7-118">Click **Filters** in the console tree.</span></span> <span data-ttu-id="adba7-119">針對**屬性**，選取**BTS。MessageType**。</span><span class="sxs-lookup"><span data-stu-id="adba7-119">For **Property**, select **BTS.MessageType**.</span></span> <span data-ttu-id="adba7-120">針對**運算子**，選取**==**。</span><span class="sxs-lookup"><span data-stu-id="adba7-120">For **Operator**, select **==**.</span></span> <span data-ttu-id="adba7-121">針對**值**，輸入`http://schemas.microsoft.com/Edi/X12#X12_997_Root`。</span><span class="sxs-lookup"><span data-stu-id="adba7-121">For **Value**, enter `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="adba7-122">此篩選條件可確保傳送埠僅會從 MessageBox 挑選 997 通知。</span><span class="sxs-lookup"><span data-stu-id="adba7-122">This filter ensures that the send port will only pick up 997 acknowledgments from the MessageBox.</span></span>  
  
6. <span data-ttu-id="adba7-123">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="adba7-123">Click **OK**.</span></span>  
  
7. <span data-ttu-id="adba7-124">在**傳送埠**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**Send_Async_997**傳送埠，，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="adba7-124">In the **Send Ports** pane of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send_Async_997** send port, and then click **Start**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="adba7-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="adba7-125">Next Steps</span></span>  
 <span data-ttu-id="adba7-126">設定傳送埠 (**Send_Payload_EdiXml**) 中所述，將 EDI 內容傳送至 Contoso，[步驟 9： 設定 EDI 內容傳送埠](../core/step-9-configure-the-edi-payload-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="adba7-126">You configure the send port (**Send_Payload_EdiXml**) to send the EDI payload to Contoso, as described in [Step 9: Configure the EDI Payload Send Port](../core/step-9-configure-the-edi-payload-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adba7-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adba7-127">See Also</span></span>  
 <span data-ttu-id="adba7-128">[BizTalk Server 如何傳送 AS2 訊息](../core/how-biztalk-server-sends-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="adba7-128">[How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md) </span></span>  
 [<span data-ttu-id="adba7-129">為透過 AS2 的訊息設定靜態傳送埠</span><span class="sxs-lookup"><span data-stu-id="adba7-129">Configuring a Static Send Port for Messages over AS2</span></span>](../core/configuring-a-static-send-port-for-messages-over-as2.md)