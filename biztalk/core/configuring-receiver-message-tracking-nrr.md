---
title: "設定接收者訊息追蹤 (NRR) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce30737a-341b-45be-81a0-a7336219185e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 942a9c62e69f9f39bf445f0b3028a4e6707f48d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-receiver-message-tracking-nrr"></a><span data-ttu-id="0b48b-102">設定接收者訊息追蹤 (NRR)</span><span class="sxs-lookup"><span data-stu-id="0b48b-102">Configuring Receiver Message Tracking (NRR)</span></span>
<span data-ttu-id="0b48b-103">在此頁面的設定中，您可以指定是否將輸入訊息和其通知 (MDN) 儲存在不可否認性的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0b48b-103">As part of the settings on this page, you can specify whether the inbound messages and their acknowledgements (MDNs) are stored in the non-repudiation database.</span></span> <span data-ttu-id="0b48b-104">如需詳細資訊，請參閱[BizTalk Server 中的 AS2 處理](../core/as2-processing-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0b48b-104">For more information, see [AS2 Processing in BizTalk Server](../core/as2-processing-in-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="0b48b-105">若要將訊息儲存在不可否認性的資料庫中，合作對象必須在 AS2 協議屬性中啟用 NRR (Non-repudiation of receipt，接收不可否認性)。</span><span class="sxs-lookup"><span data-stu-id="0b48b-105">To store messages in the non-repudiation database, the parties must enable NRR (Non-repudiation of receipt) as part of the AS2 agreement properties.</span></span> <span data-ttu-id="0b48b-106">NRR 可確保寄件方已確認訊息收件者已簽署回條。</span><span class="sxs-lookup"><span data-stu-id="0b48b-106">NRR ensures that the sender party has verified the signed receipt from the message recipient.</span></span> <span data-ttu-id="0b48b-107">概念上而言，NRR 對於訊息寄件者是一個不可否認的證明，代表訊息已完整無缺地送達目的地。</span><span class="sxs-lookup"><span data-stu-id="0b48b-107">Conceptually, an NRR is an undeniable proof for the message sender that the message reached the destination unaltered.</span></span> <span data-ttu-id="0b48b-108">只有當原始訊息和回條都完成數位簽署時，才會建立 NRR。</span><span class="sxs-lookup"><span data-stu-id="0b48b-108">NRR can be established only when the original message and the receipt are digitally signed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0b48b-109">任何屬性已停用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊合作對象 a。不過，所有屬性已停都用中相同頁面**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊</span><span class="sxs-lookup"><span data-stu-id="0b48b-109">No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0b48b-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="0b48b-110">Prerequisites</span></span>  
 <span data-ttu-id="0b48b-111">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="0b48b-111">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-message-tracking-for-inbound-as2-messages-and-outbound-mdn"></a><span data-ttu-id="0b48b-112">若要為輸入 AS2 訊息和輸出 MDN 設定訊息追蹤</span><span class="sxs-lookup"><span data-stu-id="0b48b-112">To configure message tracking for inbound AS2 messages and outbound MDN</span></span>  
  
1.  <span data-ttu-id="0b48b-113">建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="0b48b-113">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="0b48b-114">若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="0b48b-114">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="0b48b-115">在單向協議索引標籤底下**本機主機設定**區段中，按一下**接收者訊息追蹤 (NRR)**。</span><span class="sxs-lookup"><span data-stu-id="0b48b-115">On a one-way agreement tab, under **Local Host Settings** section, click **Receiver Message Tracking (NRR)**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0b48b-116">為了確保接收不可否認性，您必須建立訊息的真實性和完整性。</span><span class="sxs-lookup"><span data-stu-id="0b48b-116">To guarantee non-repudiation of receipt, you must establish the authentication and integrity of the message.</span></span> <span data-ttu-id="0b48b-117">建議做法是對訊息使用數位簽章。</span><span class="sxs-lookup"><span data-stu-id="0b48b-117">The recommended way of doing so is by using a digital signature on the message.</span></span> <span data-ttu-id="0b48b-118">如此一來，如果您選取任何要將訊息儲存在不可否認性資料庫的屬性，您應該簽署訊息以選取**訊息應該簽署**屬性**驗證**頁面。</span><span class="sxs-lookup"><span data-stu-id="0b48b-118">As a result, if you select any of the properties to store messages in the non-repudiation database, you should sign the message by selecting the **Message should be signed** property on the **Validation** page.</span></span>  
  
3.  <span data-ttu-id="0b48b-119">選取**為輸入的編碼 AS2 訊息啟用 NRR**輸出的編碼的 AS2 訊息儲存在不可否認性資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0b48b-119">Select **NRR enabled for inbound encoded AS2 messages** to store outbound encoded AS2 messages in the non-repudiation database.</span></span>  
  
4.  <span data-ttu-id="0b48b-120">選取**為輸入的解碼 AS2 訊息啟用 NRR**輸出的解碼的 AS2 訊息儲存在不可否認性資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0b48b-120">Select **NRR enabled for inbound decoded AS2 messages** to store outbound decoded AS2 messages in the non-repudiation database.</span></span>  
  
5.  <span data-ttu-id="0b48b-121">選取**為輸出的 MDN 啟用 NRR** ，將輸入的 MDN 儲存在不可否認性資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0b48b-121">Select **NRR enabled for outbound MDN** to store inbound MDN in the non-repudiation database.</span></span>  
  
6.  <span data-ttu-id="0b48b-122">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0b48b-122">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b48b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b48b-123">See Also</span></span>  
 [<span data-ttu-id="0b48b-124">設定本機主機設定 (AS2)</span><span class="sxs-lookup"><span data-stu-id="0b48b-124">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)