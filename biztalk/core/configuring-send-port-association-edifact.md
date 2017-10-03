---
title: "設定傳送埠關聯 (EDIFACT) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7faabc7-072c-408c-bbd5-f0a039be81f8
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80d62b919e6d0546f103417af08b52dc3e536ea1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-send-port-association-edifact"></a><span data-ttu-id="986e4-102">設定傳送埠關聯 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="986e4-102">Configuring Send Port Association (EDIFACT)</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="986e4-103"> 使用傳送埠關聯以解析外寄 EDI 交換的協議。</span><span class="sxs-lookup"><span data-stu-id="986e4-103"> uses send port association to resolve an agreement for an outgoing EDI interchange.</span></span> <span data-ttu-id="986e4-104">解析 EDI 交換所用協議的方法是，將訂閱該訊息的傳送埠和與協議相關聯的傳送埠進行比對。</span><span class="sxs-lookup"><span data-stu-id="986e4-104">An EDI interchange is resolved to an agreement by matching the send port that subscribed to the message with the send port associated with an agreement.</span></span> <span data-ttu-id="986e4-105">本主題提供如何將傳送埠關聯至協議的指示。</span><span class="sxs-lookup"><span data-stu-id="986e4-105">This topic provides instructions on how to associate send ports to an agreement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="986e4-106">如果相同的傳送埠與多個協議關聯，BizTalk Server 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="986e4-106">If the same send port is associated with multiple agreements, BizTalk Server will generate an error.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="986e4-107">在 [!INCLUDE[prague](../includes/prague-md.md)] 中，傳送埠關聯是在協議層級完成。</span><span class="sxs-lookup"><span data-stu-id="986e4-107">In [!INCLUDE[prague](../includes/prague-md.md)], the send port association is done only at the agreement level.</span></span> <span data-ttu-id="986e4-108">但是在 BizTalk Server 2009 中，傳送埠是在合作對象層級受到關聯。</span><span class="sxs-lookup"><span data-stu-id="986e4-108">However, in BizTalk Server 2009, the send ports were associated at the party level.</span></span> <span data-ttu-id="986e4-109">回溯相容性，**傳送埠**頁面也會提供做為合作對象屬性的一部分 (請參閱[設定一般合作對象屬性](../core/configuring-general-party-properties.md))。</span><span class="sxs-lookup"><span data-stu-id="986e4-109">For backward compatibility, a **Send Ports** page is also available as part of the party properties (see [Configuring General Party Properties](../core/configuring-general-party-properties.md)).</span></span> <span data-ttu-id="986e4-110">當您將傳送埠與協議相關聯後，傳送埠設定也會傳播到合作對象設定，而您就可以在此頁面看到該傳送埠關聯。</span><span class="sxs-lookup"><span data-stu-id="986e4-110">Whenever you associate a send port with an agreement, the send port setting is also propagated to the party setting and you can see the send port association in this page as well.</span></span> <span data-ttu-id="986e4-111">但是，並非反之亦然。</span><span class="sxs-lookup"><span data-stu-id="986e4-111">However, the reverse is not true.</span></span> <span data-ttu-id="986e4-112">在您將傳送埠與合作夥伴相關聯後，該傳送埠無法自動出現在協議設定中。</span><span class="sxs-lookup"><span data-stu-id="986e4-112">You cannot associate a send port with a party and then have that send port be automatically available as part of the agreement settings.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="986e4-113">傳送埠關聯格線會停用此頁面如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="986e4-113">The send port association grid is disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="986e4-114">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，此格線才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="986e4-114">The grid is disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="986e4-115">例如，如果您在兩個合作對象的合作對象 A 與合作對象 B 建立合作對象 a 清除該核取方塊，在方格上已停用**合作對象 a-> 合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="986e4-115">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the grid is disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="986e4-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="986e4-116">Prerequisites</span></span>  
 <span data-ttu-id="986e4-117">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="986e4-117">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-associate-send-ports-with-an-agreement"></a><span data-ttu-id="986e4-118">若要將傳送埠與協議相關聯</span><span class="sxs-lookup"><span data-stu-id="986e4-118">To associate send ports with an agreement</span></span>  
  
1.  <span data-ttu-id="986e4-119">建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。</span><span class="sxs-lookup"><span data-stu-id="986e4-119">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="986e4-120">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="986e4-120">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="986e4-121">在單向協議索引標籤底下**交換設定**區段中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="986e4-121">On a one-way agreement tab, under **Interchange Settings** section, click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="986e4-122">按一下下方的空白儲存格**名稱**資料行，然後從下拉式清單中，選取 傳送埠與協議產生關聯。</span><span class="sxs-lookup"><span data-stu-id="986e4-122">Click the empty cell under the **Name** column, and from the drop-down list, select the send port to associate with the agreement.</span></span> <span data-ttu-id="986e4-123">**URI**資料行會顯示傳送埠位址。</span><span class="sxs-lookup"><span data-stu-id="986e4-123">The **URI** column displays the send port address.</span></span>  
  
4.  <span data-ttu-id="986e4-124">若要移除傳送埠關聯，請選取 傳送埠的資料列，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="986e4-124">To remove a send port association, select the row for a send port and click **Remove**.</span></span>  
  
5.  <span data-ttu-id="986e4-125">若要查看傳送埠的屬性，選取 傳送埠的資料列，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="986e4-125">To see the properties for a send port, select the row for a send port and click **Properties**.</span></span>  
  
6.  <span data-ttu-id="986e4-126">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="986e4-126">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="986e4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="986e4-127">See Also</span></span>  
 [<span data-ttu-id="986e4-128">設定交換設定 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="986e4-128">Configuring Interchange Settings (EDIFACT)</span></span>](../core/configuring-interchange-settings-edifact.md)