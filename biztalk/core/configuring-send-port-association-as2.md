---
title: "設定傳送埠關聯 (AS2) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8624d4c-cee8-4072-bff7-2468d83a06de
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: babc3084515b50e0414c296f9029f223511305e3
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-send-port-association-as2"></a><span data-ttu-id="0e7ee-102">設定傳送埠關聯 (AS2)</span><span class="sxs-lookup"><span data-stu-id="0e7ee-102">Configuring Send Port Association (AS2)</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0e7ee-103"> 會使用傳送埠關聯來解析外寄 AS2 訊息的協議。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-103"> uses send port association to resolve an agreement for an outgoing AS2 message.</span></span> <span data-ttu-id="0e7ee-104">解析 AS2 訊息所用協議的方法是，將訂閱該訊息的傳送埠和與協議相關聯的傳送埠進行比對。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-104">An AS2 message is resolved to an agreement by matching the send port that subscribed to the message with the send port associated with an agreement.</span></span> <span data-ttu-id="0e7ee-105">本主題提供如何將傳送埠關聯至協議的指示。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-105">This topic provides instructions on how to associate send ports to an agreement.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0e7ee-106">在 BizTalk Server 傳送埠關聯是只能在協議層級。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-106">In BizTalk Server, the send port association is done only at the agreement level.</span></span> <span data-ttu-id="0e7ee-107">但是在 BizTalk Server 2009 中，傳送埠是在合作對象層級受到關聯。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-107">However, in BizTalk Server 2009, the send ports were associated at the party level.</span></span> <span data-ttu-id="0e7ee-108">回溯相容性，**傳送埠**頁面也會提供做為合作對象屬性的一部分 (請參閱[設定一般合作對象屬性 (AS2)](../core/configuring-general-party-properties-as2.md))。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-108">For backward compatibility, a **Send Ports** page is also available as part of the party properties (see [Configuring General Party Properties (AS2)](../core/configuring-general-party-properties-as2.md)).</span></span> <span data-ttu-id="0e7ee-109">當您將傳送埠與協議相關聯後，傳送埠設定也會傳播到合作對象設定，而您就可以在此頁面看到該傳送埠關聯。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-109">Whenever you associate a send port with an agreement, the send port setting is also propagated to the party setting and you can see the send port association in this page as well.</span></span> <span data-ttu-id="0e7ee-110">但是，並非反之亦然。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-110">However, the reverse is not true.</span></span> <span data-ttu-id="0e7ee-111">在您將傳送埠與合作夥伴相關聯後，該傳送埠無法自動出現在協議設定中。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-111">You cannot associate a send port with a party and then have that send port be automatically available as part of the agreement settings.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0e7ee-112">傳送埠關聯格線會停用此頁面如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-112">The send port association grid is disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="0e7ee-113">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，此格線才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-113">The grid is disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="0e7ee-114">例如，如果您在兩個合作對象的合作對象 A 與合作對象 B 建立合作對象 a 清除該核取方塊，在方格上已停用**合作對象 a-> 合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-114">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the grid is disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0e7ee-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="0e7ee-115">Prerequisites</span></span>  
 <span data-ttu-id="0e7ee-116">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-116">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-send-port-association"></a><span data-ttu-id="0e7ee-117">若要設定傳送埠關聯</span><span class="sxs-lookup"><span data-stu-id="0e7ee-117">To configure send port association</span></span>  
  
1.  <span data-ttu-id="0e7ee-118">建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-118">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="0e7ee-119">若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-119">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="0e7ee-120">在單向協議索引標籤上，按一下 **傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-120">On a one-way agreement tab, click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="0e7ee-121">按一下下方的空白儲存格**名稱**資料行，然後從下拉式清單中，選取 傳送埠與協議產生關聯。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-121">Click the empty cell under the **Name** column, and from the drop-down list, select the send port to associate with the agreement.</span></span> <span data-ttu-id="0e7ee-122">**URI**資料行會顯示傳送埠位址。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-122">The **URI** column displays the send port address.</span></span>  
  
4.  <span data-ttu-id="0e7ee-123">若要移除傳送埠關聯，請選取 傳送埠的資料列，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-123">To remove a send port association, select the row for a send port and click **Remove**.</span></span>  
  
5.  <span data-ttu-id="0e7ee-124">若要查看傳送埠的屬性，選取 傳送埠的資料列，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-124">To see the properties for a send port, select the row for a send port and click **Properties**.</span></span>  
  
6.  <span data-ttu-id="0e7ee-125">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0e7ee-125">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e7ee-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="0e7ee-126">See Also</span></span>  
 [<span data-ttu-id="0e7ee-127">設定 AS2 協議屬性</span><span class="sxs-lookup"><span data-stu-id="0e7ee-127">Configuring AS2 Agreement Properties</span></span>](../core/configuring-as2-agreement-properties.md)