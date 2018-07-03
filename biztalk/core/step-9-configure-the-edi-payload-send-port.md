---
title: 步驟 9： 設定 EDI 內容傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71a8a4a7-7c3e-4e33-a9c0-a6445a3cc236
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11f12d57a0aee016055412b9221ff2b2de442c17
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005551"
---
# <a name="step-9-configure-the-edi-payload-send-port"></a><span data-ttu-id="9e1b1-102">步驟 9： 設定 EDI 內容傳送埠</span><span class="sxs-lookup"><span data-stu-id="9e1b1-102">Step 9: Configure the EDI Payload Send Port</span></span>
<span data-ttu-id="9e1b1-103">![步驟 11-9](../core/media/tut-step9-of-11.gif "Tut_Step9_of_11")</span><span class="sxs-lookup"><span data-stu-id="9e1b1-103">![Step 9 of 11](../core/media/tut-step9-of-11.gif "Tut_Step9_of_11")</span></span>  
  
 <span data-ttu-id="9e1b1-104">在此步驟中，您可以設定為傳送至後端 Contoso 應用程式中，從 EDI 內容產生的 XML 傳送埠以\\_EDIXMLToContoso 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-104">In this step, you set up a send port to send the XML generated from the EDI payload to the back-end Contoso application, represented by the \\_EDIXMLToContoso folder.</span></span> <span data-ttu-id="9e1b1-105">這個傳送埠會使用 PassThruTransmit 傳送管線。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-105">This send port uses a PassThruTransmit send pipeline.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9e1b1-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="9e1b1-106">Prerequisites</span></span>  
 <span data-ttu-id="9e1b1-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-create-the-sendpayloadedixml-send-port"></a><span data-ttu-id="9e1b1-108">若要建立 Send_Payload_EdiXml 傳送埠</span><span class="sxs-lookup"><span data-stu-id="9e1b1-108">To create the Send_Payload_EdiXml send port</span></span>  
  
1. <span data-ttu-id="9e1b1-109">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-Way Send Port**.</span></span>  
  
2. <span data-ttu-id="9e1b1-110">在 **傳送埠屬性**對話方塊中，將傳送埠作為**Send_Payload_EdiXml**。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-110">In the **Send Port Properties** dialog box, name your send port as **Send_Payload_EdiXml**.</span></span> <span data-ttu-id="9e1b1-111">選取 **檔案**for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-111">Select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="9e1b1-112">因為傳送管線並不會針對該內容檔案執行 AS2 處理，所以要設定 FILE 類型。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-112">The FILE type is specified because the send pipeline is not performing AS2 processing on the payload file.</span></span> <span data-ttu-id="9e1b1-113">該管線只是將內容檔案路由到本機資料夾，以便您可以檢視 EDI 交易集。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-113">It is just routing the payload file to a local folder so you can see the EDI transaction set.</span></span>  
  
3. <span data-ttu-id="9e1b1-114">在**FILE 傳輸屬性** 對話方塊中，如**目的地資料夾**中，瀏覽並選取[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-114">In the **FILE Transport Properties** dialog box, for **Destination folder**, browse to and select [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso.</span></span> <span data-ttu-id="9e1b1-115">離開**檔名**作為 **%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-115">Leave **File name** as **%MessageID%.xml**.</span></span> <span data-ttu-id="9e1b1-116">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-116">Click **OK**.</span></span>  
  
4. <span data-ttu-id="9e1b1-117">接受預設值是**PassThruTransmit** for**傳送管線**。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-117">Accept the default of **PassThruTransmit** for **Send Pipeline**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="9e1b1-118">由於此時是使用 PassThruTransmit 傳送管線，所以此管線不會對內容訊息執行任何 EDI 處理，反而是以 XML 格式傳送到 AS2EdiReceive 接收管線產生的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-118">Because the PassThruTransmit send pipeline is used, the pipeline will not perform any EDI processing on the payload message, but will be sent to the local folder in the XML format produced by the AS2EdiReceive receive pipeline.</span></span>  
  
5. <span data-ttu-id="9e1b1-119">按一下 **篩選器**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-119">Click **Filters** in the console tree.</span></span> <span data-ttu-id="9e1b1-120">針對**屬性**，輸入**BTS。MessageType**。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-120">For **Property**, enter **BTS.MessageType**.</span></span> <span data-ttu-id="9e1b1-121">針對**運算子**，輸入**==**。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-121">For **Operator**, enter **==**.</span></span> <span data-ttu-id="9e1b1-122">針對**值**，輸入`http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-122">For **Value**, enter `http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="9e1b1-123">此篩選條件可確保這個傳送埠僅會收取來自 MessageBox 的 X12 864 內容通知。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-123">This filter ensures that this send port will only pick up X12 864 payload messages from the MessageBox.</span></span>  
  
6. <span data-ttu-id="9e1b1-124">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-124">Click **OK**.</span></span>  
  
7. <span data-ttu-id="9e1b1-125">在**傳送埠**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**Send_Payload_EdiXml**傳送埠，，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="9e1b1-125">In the **Send Ports** pane of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send_Payload_EdiXml** send port, and then click **Start**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9e1b1-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9e1b1-126">Next Steps</span></span>  
 <span data-ttu-id="9e1b1-127">您建立的 AS2 與 X12 協議兩個交易合作夥伴中所述[步驟 10： 設定 X12 和 AS2 交易夥伴協議](../core/step-10-configure-the-x12-and-as2-trading-partner-agreement.md)</span><span class="sxs-lookup"><span data-stu-id="9e1b1-127">You create an AS2 and X12 agreement between the two trading partners, as described in [Step 10: Configure the X12 and AS2 Trading Partner Agreement](../core/step-10-configure-the-x12-and-as2-trading-partner-agreement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e1b1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e1b1-128">See Also</span></span>  
 [<span data-ttu-id="9e1b1-129">教學課程 3: AS2 教學課程</span><span class="sxs-lookup"><span data-stu-id="9e1b1-129">Tutorial 3: AS2 Tutorial</span></span>](../core/tutorial-3-as2-tutorial.md)