---
title: 設定通知 (Mdn) (AS2) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb2bf98a-deb4-460f-a1fc-3d2397c39470
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2df8c92d37d5f6bc8fbf8d6d77fb698e6178036
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234102"
---
# <a name="configuring-acknowledgements-mdns-as2"></a><span data-ttu-id="83cbe-102">設定通知 (MDN) (AS2)</span><span class="sxs-lookup"><span data-stu-id="83cbe-102">Configuring Acknowledgements (MDNs) (AS2)</span></span>
<span data-ttu-id="83cbe-103">在夥伴協議中，您可以指定收到 AS2 訊息的合作對象如何產生並傳回 MDN 回應。</span><span class="sxs-lookup"><span data-stu-id="83cbe-103">In the partner agreement, you can specify how the party receiving the AS2 message generates an MDN response and sends it to back.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83cbe-104">下列屬性會停用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="83cbe-104">The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  -   <span data-ttu-id="83cbe-105">**重新傳送 AS2 訊息，若未收到 MDN**核取方塊和相關聯的屬性</span><span class="sxs-lookup"><span data-stu-id="83cbe-105">**Resend AS2 message if MDN not received** check box and associated properties</span></span>  
> -   <span data-ttu-id="83cbe-106">**覆寫傳送埠設定**核取方塊和相關聯的屬性</span><span class="sxs-lookup"><span data-stu-id="83cbe-106">**Override send port settings** check box and associated properties</span></span>  
>   
>  <span data-ttu-id="83cbe-107">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="83cbe-107">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="83cbe-108">例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="83cbe-108">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="83cbe-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="83cbe-109">Prerequisites</span></span>  
 <span data-ttu-id="83cbe-110">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="83cbe-110">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-acknowledgements"></a><span data-ttu-id="83cbe-111">若要設定通知</span><span class="sxs-lookup"><span data-stu-id="83cbe-111">To configure acknowledgements</span></span>  
  
1.  <span data-ttu-id="83cbe-112">建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="83cbe-112">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="83cbe-113">若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="83cbe-113">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="83cbe-114">在單向協議索引標籤上，按一下 **通知 (Mdn)**。</span><span class="sxs-lookup"><span data-stu-id="83cbe-114">On a one-way agreement tab, click **Acknowledgements (MDNs)**.</span></span>  
  
3.  <span data-ttu-id="83cbe-115">選取**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**核取方塊，以透過 as2 解碼器將 MDN 路由，以通過訊息，然後放入 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="83cbe-115">Select the **Process inbound MDN into MessageBox for routing/delivery options** check box to route the MDN through the A2 Decoder as a passthrough message and then into the MessageBox.</span></span> <span data-ttu-id="83cbe-116">選取這個屬性時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會基於路由目的升級 `IsAS2MdnResponseMessage` 屬性。</span><span class="sxs-lookup"><span data-stu-id="83cbe-116">When this property is selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] promotes the `IsAS2MdnResponseMessage` property for routing purposes.</span></span>  
  
4.  <span data-ttu-id="83cbe-117">如果您核取**使用協議設定進行驗證，並 MSDN，取代訊息標頭**屬性**驗證**頁面上，選取**要求 MDN**如果核取方塊交易夥伴必須產生 MDN 以回應 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="83cbe-117">If you checked the **Use agreement settings for validation and MSDN instead of message header** property in the **Validations** page, select the **Request MDN** check box if the trading partner must generate an MDN in response to the AS2 message.</span></span>  
  
     <span data-ttu-id="83cbe-118">如果**要求 MDN**核取方塊已選取，您也可以設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="83cbe-118">If the **Request MDN** check box is selected, you can also set the following properties:</span></span>  
  
    1.  <span data-ttu-id="83cbe-119">選取**要求簽署的 MDN**核取方塊，並從**簽署演算法**下拉式清單選取交易夥伴必須用來簽署 MDN 的 MIC 演算法。</span><span class="sxs-lookup"><span data-stu-id="83cbe-119">Select the **Request signed MDN** check box and from the **Signing Algorithm** drop-down select the MIC algorithm that the trading partner must use to sign the MDN.</span></span> [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="83cbe-120">支援 MD5、 SHA1、 和 SHA2 (SHA256 （預設）、 SHA384 及 SHA512)。</span><span class="sxs-lookup"><span data-stu-id="83cbe-120"> supports MD5, SHA1, and SHA2 (SHA256 (default), SHA384, and SHA512).</span></span>
    
        > [!NOTE] 
        > <span data-ttu-id="83cbe-121">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]和較新版本**，SHA2 支援會自動包含。</span><span class="sxs-lookup"><span data-stu-id="83cbe-121">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] and newer versions**, SHA2 support is automatically included.</span></span> <span data-ttu-id="83cbe-122">如先前[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]版本中，請參閱[KB 3123748](https://support.microsoft.com/kb/3123748)。</span><span class="sxs-lookup"><span data-stu-id="83cbe-122">For previous [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] versions, see [KB 3123748](https://support.microsoft.com/kb/3123748).</span></span>
  
    2.  <span data-ttu-id="83cbe-123">選取**要求非同步 MDN**核取方塊，然後在**回條傳遞選項 (URL)** 文字方塊中，輸入接收合作對象應該傳送 MDN 的 URL。</span><span class="sxs-lookup"><span data-stu-id="83cbe-123">Select the **Request asynchronous MDN** check box and then in the **Receipt-Delivery-Option (URL)** text box, enter the URL that the receiving party should send the MDN to.</span></span>  
  
         <span data-ttu-id="83cbe-124">如果**要求非同步 MDN**核取方塊已選取，您也可以設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="83cbe-124">If the **Request asynchronous MDN** check box is selected, you can also set the following properties:</span></span>  
  
        1.  <span data-ttu-id="83cbe-125">選取**重新傳送 AS2 訊息，若未收到 MDN**核取方塊以啟用重新傳輸 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="83cbe-125">Select the **Resend AS2 message if MDN not received** check box to enable retransmission of the AS2 message.</span></span> <span data-ttu-id="83cbe-126">輸入一個值**最小值 AS2 訊息重新傳送間隔**，**數目的 AS2 訊息重新傳送嘗試**和**停止嘗試之後會重新傳送訊息的 AS2**欄位，即可指定重試間隔、 最大嘗試次數和何時停止重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="83cbe-126">Enter a value for **Minimum AS2 message resend interval**, **Number of AS2 message resend attempts** and **Stop attempting AS2 message resends after** fields to specify the retry interval, maximum number of attempts and when to stop resending the message.</span></span>  
  
            > [!NOTE]
            >  <span data-ttu-id="83cbe-127">您必須選取**開啟報告** 核取方塊**一般屬性**頁面**一般** 索引標籤，然後再選取**重新傳送 AS2 訊息，如果 MDN 不收到**。</span><span class="sxs-lookup"><span data-stu-id="83cbe-127">You must select the **Turn ON Reporting** check box on the **General Properties** page of the **General** tab before selecting **Resend AS2 message if MDN not received**.</span></span>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="83cbe-128">使用追蹤針對 AS2 報告，以判斷何時重新傳送 AS2 訊息儲存的資訊。</span><span class="sxs-lookup"><span data-stu-id="83cbe-128"> uses tracking information stored for AS2 reporting in order to determine when to resend an AS2 message.</span></span>  
  
        2.  <span data-ttu-id="83cbe-129">如果**重新傳送 AS2 訊息，若未收到 MDN**選取核取方塊時，請檢查**覆寫傳送埠設定**指定**最小值的 HTTP 重試間隔**和**HTTP 重試嘗試次數**。</span><span class="sxs-lookup"><span data-stu-id="83cbe-129">If **Resend AS2 message if MDN not received** check box is selected, check **Override send port settings** to specify the **Minimum HTTP retry interval** and **Number of HTTP retry attempts**.</span></span> <span data-ttu-id="83cbe-130">輸入一個值**停止嘗試 HTTP 重試後**欄位來指定要使用 HTTP 配接器嘗試重試時間的最大數量。</span><span class="sxs-lookup"><span data-stu-id="83cbe-130">Enter a value for the **Stop attempting HTTP retries after** field to specify the maximum amount of time to attempt retries using the HTTP adapter.</span></span>  
  
    3.  <span data-ttu-id="83cbe-131">如果您選取**要求非同步 MDN**核取方塊，而且指定的 URL**回條傳遞選項 (URL)** 屬性，**配置通知至**文字方塊中，依預設設定為相同的 URL。</span><span class="sxs-lookup"><span data-stu-id="83cbe-131">If you selected the **Request asynchronous MDN** check box and specified a URL for **Receipt-Delivery-Option (URL)** property, the **Disposition-Notification-To** text box, is by default set to the same URL.</span></span> <span data-ttu-id="83cbe-132">如果您未選取**要求非同步 MDN**核取方塊，您必須輸入的值**配置通知至**。</span><span class="sxs-lookup"><span data-stu-id="83cbe-132">If you did not select the **Request asynchronous MDN** check box, you must enter a value for **Disposition-Notification-To**.</span></span> <span data-ttu-id="83cbe-133">在處理 AS2 的過程中並不會使用這個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="83cbe-133">The value of this field is not used during AS2 processing.</span></span>  
  
5.  <span data-ttu-id="83cbe-134">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="83cbe-134">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83cbe-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83cbe-135">See Also</span></span>  
 [<span data-ttu-id="83cbe-136">設定 AS2 協議屬性</span><span class="sxs-lookup"><span data-stu-id="83cbe-136">Configuring AS2 Agreement Properties</span></span>](../core/configuring-as2-agreement-properties.md)