---
title: "設定通知 (EDIFACT) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9436feb7-4c29-4b7c-b5c2-991660e6c1a9
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fe376437c2d6657acb98d548c2c1373b050d599
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-acknowledgements-edifact"></a><span data-ttu-id="ba894-102">設定通知 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="ba894-102">Configuring Acknowledgements (EDIFACT)</span></span>
<span data-ttu-id="ba894-103">在夥伴協議中，您可以指定要將何種類型的通知傳回給合作對象，以及要在傳送通知時使用何種傳送埠。</span><span class="sxs-lookup"><span data-stu-id="ba894-103">In the partner agreement, you can specify what type of acknowledgment to return to a party and what kind of send port to use in sending the acknowledgment.</span></span> <span data-ttu-id="ba894-104">您也可以指定是否要批次處理通知、通知的開始交易集參考編號為何，以及是否要針對接受的交易集產生 SG1/SG4 迴圈。</span><span class="sxs-lookup"><span data-stu-id="ba894-104">You also specify whether to batch an acknowledgment, what the starting transaction set reference number is for the acknowledgment, and whether SG1/SG4 loops are generated for accepted transaction sets.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba894-105">下列屬性會停用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="ba894-105">The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  -   <span data-ttu-id="ba894-106">**產生 SG1/SG4 迴圈接受的交易集 （如果未選取，會產生迴圈在 UCM.5 不等於 7 時，才）**。</span><span class="sxs-lookup"><span data-stu-id="ba894-106">**Generate SG1/SG4 loop for accepted transaction sets (If unchecked, loop will be generated only if UCM.5 is not equal to 7)**.</span></span>  
>   
>  <span data-ttu-id="ba894-107">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="ba894-107">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="ba894-108">例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ba894-108">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ba894-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="ba894-109">Prerequisites</span></span>  
 <span data-ttu-id="ba894-110">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="ba894-110">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-edifact-ack-contrl-properties"></a><span data-ttu-id="ba894-111">若要設定 EDIFACT 通知 (CONTRL) 屬性</span><span class="sxs-lookup"><span data-stu-id="ba894-111">To configure EDIFACT ACK (CONTRL) properties</span></span>  
  
1.  <span data-ttu-id="ba894-112">建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。</span><span class="sxs-lookup"><span data-stu-id="ba894-112">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="ba894-113">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ba894-113">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="ba894-114">在單向協議索引標籤底下**交換設定**區段中，按一下**通知**。</span><span class="sxs-lookup"><span data-stu-id="ba894-114">On a one-way agreement tab, under **Interchange Settings** section, click **Acknowledgements**.</span></span>  
  
3.  <span data-ttu-id="ba894-115">在**EDIFACT ACK （控制） 區段**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ba894-115">In the **EDIFACT ACK (Control) section**, do the following:</span></span>  
  
    1.  <span data-ttu-id="ba894-116">選取**訊息回條 (CONTRL 必須是)**技術 (CONTRL) 通知傳回給交換傳送者。</span><span class="sxs-lookup"><span data-stu-id="ba894-116">Select **Receipt of message (CONTRL) expected** to return a technical (CONTRL) acknowledgment to the interchange sender.</span></span> <span data-ttu-id="ba894-117">如果**訊息回條 (CONTRL 必須是)**選取，請選取**不要批次處理訊息 (CONTRL) 訊息回條**可分別傳送每個通知，或是不選取該項即可批次處理通知。</span><span class="sxs-lookup"><span data-stu-id="ba894-117">If **Receipt of message (CONTRL) expected** is selected, select **Do not batch receipt of message (CONTRL) message** to send each acknowledgment separately, or leave cleared to batch the acknowledgments.</span></span>  
  
    2.  <span data-ttu-id="ba894-118">選取**通知 (CONTRL) 必須是**功能 (CONTRL) 通知傳回給交換傳送者。</span><span class="sxs-lookup"><span data-stu-id="ba894-118">Select **Acknowledgement (CONTRL) expected** to return a functional (CONTRL) acknowledgment to the interchange sender.</span></span> <span data-ttu-id="ba894-119">如果**通知 (CONTRL) 必須是**選取，請選取**不要批次處理通知 (CONTRL)**分別傳送每個功能通知，或不選取可批次處理功能通知。</span><span class="sxs-lookup"><span data-stu-id="ba894-119">If **Acknowledgement (CONTRL) expected** is selected, select **Do not batch Acknowledgement (CONTRL)** to send each functional acknowledgment separately, or leave cleared to batch the functional acknowledgments.</span></span>  
  
4.  <span data-ttu-id="ba894-120">在**交易集狀態認可報告**區段中，若要接受的交易集功能 CONTRL 通知中強制產生 SG1/SG4 迴圈選取**產生 SG1/SG4 迴圈的接受交易集 （如果未選取，會產生迴圈在 UCM.5 不等於 7 時，才）**。</span><span class="sxs-lookup"><span data-stu-id="ba894-120">In the **Transaction set status acceptance reporting** section, to force generation of SG1/SG4 loops in functional CONTRL acknowledgments for accepted transaction sets, select **Generate SG1/SG4 loop for accepted transaction sets (If unchecked, loop will be generated only if UCM.5 is not equal to 7)**.</span></span> <span data-ttu-id="ba894-121">如需 SG1/SG4 迴圈的詳細資訊，請參閱[EDIFACT CONTRL 訊息做為功能通知](../core/edifact-contrl-message-as-functional-acknowledgment.md)。</span><span class="sxs-lookup"><span data-stu-id="ba894-121">For more information about SG1/SG4 loops, see [EDIFACT CONTRL Message as Functional Acknowledgment](../core/edifact-contrl-message-as-functional-acknowledgment.md).</span></span>  
  
5.  <span data-ttu-id="ba894-122">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ba894-122">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba894-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba894-123">See Also</span></span>  
 [<span data-ttu-id="ba894-124">設定交換設定 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="ba894-124">Configuring Interchange Settings (EDIFACT)</span></span>](../core/configuring-interchange-settings-edifact.md)