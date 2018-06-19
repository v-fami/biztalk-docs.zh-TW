---
title: 設定傳送埠關聯 (X12) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 496beb0a-fabf-416e-bc3c-d8537097b50e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d81eee157c84677470e542c5d4ee5f9bf2cb5df5
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005559"
---
# <a name="configuring-send-port-association-x12"></a><span data-ttu-id="fc81a-102">設定傳送埠關聯 (X12)</span><span class="sxs-lookup"><span data-stu-id="fc81a-102">Configuring Send Port Association (X12)</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="fc81a-103"> 使用傳送埠關聯以解析外寄 EDI 交換的協議。</span><span class="sxs-lookup"><span data-stu-id="fc81a-103"> uses send port association to resolve an agreement for an outgoing EDI interchange.</span></span> <span data-ttu-id="fc81a-104">解析 EDI 交換所用協議的方法是，將訂閱該訊息的傳送埠和與協議相關聯的傳送埠進行比對。</span><span class="sxs-lookup"><span data-stu-id="fc81a-104">An EDI interchange is resolved to an agreement by matching the send port that subscribed to the message with the send port associated with an agreement.</span></span> <span data-ttu-id="fc81a-105">本主題提供如何將傳送埠關聯至協議的指示。</span><span class="sxs-lookup"><span data-stu-id="fc81a-105">This topic provides instructions on how to associate send ports to an agreement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc81a-106">如果相同的傳送埠與多個協議關聯，BizTalk Server 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fc81a-106">If the same send port is associated with multiple agreements, BizTalk Server will generate an error.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fc81a-107">在 BizTalk Server 傳送埠關聯是只能在協議層級。</span><span class="sxs-lookup"><span data-stu-id="fc81a-107">In BizTalk Server, the send port association is done only at the agreement level.</span></span> <span data-ttu-id="fc81a-108">但是在 BizTalk Server 2009 中，傳送埠是在合作對象層級受到關聯。</span><span class="sxs-lookup"><span data-stu-id="fc81a-108">However, in BizTalk Server 2009, the send ports were associated at the party level.</span></span> <span data-ttu-id="fc81a-109">回溯相容性，**傳送埠**頁面也會提供做為合作對象屬性的一部分 (請參閱[設定一般合作對象屬性](../core/configuring-general-party-properties.md))。</span><span class="sxs-lookup"><span data-stu-id="fc81a-109">For backward compatibility, a **Send Ports** page is also available as part of the party properties (see [Configuring General Party Properties](../core/configuring-general-party-properties.md)).</span></span> <span data-ttu-id="fc81a-110">當您將傳送埠與協議相關聯後，傳送埠設定也會傳播到合作對象設定，而您就可以在此頁面看到該傳送埠關聯。</span><span class="sxs-lookup"><span data-stu-id="fc81a-110">Whenever you associate a send port with an agreement, the send port setting is also propagated to the party setting and you can see the send port association in this page as well.</span></span> <span data-ttu-id="fc81a-111">但是，並非反之亦然。</span><span class="sxs-lookup"><span data-stu-id="fc81a-111">However, the reverse is not true.</span></span> <span data-ttu-id="fc81a-112">在您將傳送埠與合作夥伴相關聯後，該傳送埠無法自動出現在協議設定中。</span><span class="sxs-lookup"><span data-stu-id="fc81a-112">You cannot associate a send port with a party and then have that send port be automatically available as part of the agreement settings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc81a-113">此處所說明的設定也適用於 HIPAA 交換。</span><span class="sxs-lookup"><span data-stu-id="fc81a-113">The settings described here also apply to HIPAA interchanges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fc81a-114">傳送埠關聯格線會停用此頁面如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="fc81a-114">The send port association grid is disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="fc81a-115">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，此格線才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="fc81a-115">The grid is disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="fc81a-116">例如，如果您在兩個合作對象的合作對象 A 與合作對象 B 建立合作對象 a 清除該核取方塊，在方格上已停用**合作對象 a-> 合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fc81a-116">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the grid is disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fc81a-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="fc81a-117">Prerequisites</span></span>  
 <span data-ttu-id="fc81a-118">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="fc81a-118">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-associate-send-ports-with-an-agreement"></a><span data-ttu-id="fc81a-119">若要將傳送埠與協議相關聯</span><span class="sxs-lookup"><span data-stu-id="fc81a-119">To associate send ports with an agreement</span></span>  
  
1.  <span data-ttu-id="fc81a-120">建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="fc81a-120">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="fc81a-121">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="fc81a-121">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="fc81a-122">在單向協議索引標籤底下**交換設定**區段中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="fc81a-122">On a one-way agreement tab, under **Interchange Settings** section, click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="fc81a-123">按一下下方的空白儲存格**名稱**資料行，然後從下拉式清單中，選取 傳送埠與協議產生關聯。</span><span class="sxs-lookup"><span data-stu-id="fc81a-123">Click the empty cell under the **Name** column, and from the drop-down list, select the send port to associate with the agreement.</span></span> <span data-ttu-id="fc81a-124">**URI**資料行會顯示傳送埠位址。</span><span class="sxs-lookup"><span data-stu-id="fc81a-124">The **URI** column displays the send port address.</span></span>  
  
4.  <span data-ttu-id="fc81a-125">若要移除傳送埠關聯，請選取 傳送埠的資料列，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="fc81a-125">To remove a send port association, select the row for a send port and click **Remove**.</span></span>  
  
5.  <span data-ttu-id="fc81a-126">若要查看傳送埠的屬性，選取 傳送埠的資料列，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="fc81a-126">To see the properties for a send port, select the row for a send port and click **Properties**.</span></span>  
  
6.  <span data-ttu-id="fc81a-127">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fc81a-127">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc81a-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc81a-128">See Also</span></span>  
 [<span data-ttu-id="fc81a-129">設定交換設定 (X12)</span><span class="sxs-lookup"><span data-stu-id="fc81a-129">Configuring Interchange Settings (X12)</span></span>](../core/configuring-interchange-settings-x12.md)