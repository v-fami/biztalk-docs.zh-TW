---
title: "設定通知 (X12) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eec2dbff-5d04-4a38-bad0-33d040b6dd12
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edec872f4055bb2c06772d361f18345d4a4be2d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-acknowledgements-x12"></a><span data-ttu-id="ef925-102">設定通知 (X12)</span><span class="sxs-lookup"><span data-stu-id="ef925-102">Configuring Acknowledgements (X12)</span></span>
<span data-ttu-id="ef925-103">在夥伴協議中，您可以指定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在收到來自合作對象的 X12 編碼交換後，應如何產生通知，以及應對合作對象傳回哪種類型的通知。</span><span class="sxs-lookup"><span data-stu-id="ef925-103">In the partner agreement, you can specify how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates acknowledgments in response to X12-encoded interchanges received from the party and what type of acknowledgment to return to a party.</span></span> <span data-ttu-id="ef925-104">您可以指定是否要批次處理通知，以及是否要針對接受的交易集產生 AK2 迴圈。</span><span class="sxs-lookup"><span data-stu-id="ef925-104">You can also specify whether to batch an acknowledgement and whether AK2 loops are generated for accepted transaction sets.</span></span> <span data-ttu-id="ef925-105">本節提供如何執行此作業的指示。</span><span class="sxs-lookup"><span data-stu-id="ef925-105">This section provides instructions on how to do so.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef925-106">此處所說明的通知屬性也適用於 HIPAA 通知。</span><span class="sxs-lookup"><span data-stu-id="ef925-106">The acknowledgement properties described here apply also for HIPAA acknowledgements.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ef925-107">下列屬性會停用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="ef925-107">The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  -   <span data-ttu-id="ef925-108">**包含針對接受的交易集的 AK2 迴圈 （如果未選取，會產生迴圈只有在 AK501 不等於 A 時才）**。</span><span class="sxs-lookup"><span data-stu-id="ef925-108">**Include AK2 loop for accepted transaction sets (if unchecked, loop will be generated only if AK501 is not equal to A)**.</span></span>  
>   
>  <span data-ttu-id="ef925-109">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="ef925-109">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="ef925-110">例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ef925-110">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ef925-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="ef925-111">Prerequisites</span></span>  
 <span data-ttu-id="ef925-112">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="ef925-112">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-x12-ack-properties"></a><span data-ttu-id="ef925-113">若要設定 X12 通知屬性</span><span class="sxs-lookup"><span data-stu-id="ef925-113">To configure X12 ACK properties</span></span>  
  
1.  <span data-ttu-id="ef925-114">建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="ef925-114">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="ef925-115">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ef925-115">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="ef925-116">在單向協議索引標籤底下**交換設定**，按一下 **通知**。</span><span class="sxs-lookup"><span data-stu-id="ef925-116">On a one-way agreement tab, under **Interchange Settings**, click **Acknowledgements**.</span></span>  
  
3.  <span data-ttu-id="ef925-117">選取**預期 TA1**技術 (TA1) 通知傳回給交換傳送者。</span><span class="sxs-lookup"><span data-stu-id="ef925-117">Select **TA1 Expected** to return a technical (TA1) acknowledgment to the interchange sender.</span></span> <span data-ttu-id="ef925-118">如果選取，請選取**不要批次處理 TA1**分別傳送每個技術通知，則會批次處理技術通知 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ef925-118">If selected, select **Do not batch TA1** to send each technical acknowledgment separately, or leave the check box cleared to batch the technical acknowledgments.</span></span>  
  
4.  <span data-ttu-id="ef925-119">選取**預期 997**功能 (997) 通知傳回給交換傳送者。</span><span class="sxs-lookup"><span data-stu-id="ef925-119">Select **997 Expected** to return a functional (997) acknowledgment to the interchange sender.</span></span> <span data-ttu-id="ef925-120">如果選取，請選取**不要批次處理 997**分別傳送每個功能通知，則會批次處理功能通知 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ef925-120">If selected, select **Do not batch 997** to send each functional acknowledgment separately, or leave the check box cleared to batch the functional acknowledgments.</span></span>  
  
5.  <span data-ttu-id="ef925-121">為了在 997 通知接受的交易集產生 AK2 迴圈，選取**接受的交易集包含 AK2 迴圈 （如果未選取，會產生迴圈只有在 AK501 不等於 A 時才）**。</span><span class="sxs-lookup"><span data-stu-id="ef925-121">To enable generation of AK2 loops in 997 acknowledgments for accepted transaction sets, select **Include AK2 loop for accepted transaction sets (if unchecked, loop will be generated only if AK501 is not equal to A)**.</span></span> <span data-ttu-id="ef925-122">如需 AK2 迴圈的詳細資訊，請參閱[X12 997 通知](../core/x12-997-acknowledgment.md)。</span><span class="sxs-lookup"><span data-stu-id="ef925-122">For more information about AK2 loops, see [X12 997 Acknowledgment](../core/x12-997-acknowledgment.md).</span></span>  
  
6.  <span data-ttu-id="ef925-123">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ef925-123">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef925-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef925-124">See Also</span></span>  
 [<span data-ttu-id="ef925-125">設定交換設定 (X12)</span><span class="sxs-lookup"><span data-stu-id="ef925-125">Configuring Interchange Settings (X12)</span></span>](../core/configuring-interchange-settings-x12.md)