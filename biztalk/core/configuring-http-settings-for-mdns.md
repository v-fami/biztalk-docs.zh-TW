---
title: "設定 Mdn 的 HTTP 設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c877e85-7887-43a9-9fd4-0853b573213f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f74ba2eaf11e8beed3e28d10beb9f95b2f0f6194
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-http-settings-for-mdns"></a><span data-ttu-id="f2573-102">設定 MDN 的 HTTP 設定</span><span class="sxs-lookup"><span data-stu-id="f2573-102">Configuring HTTP Settings for MDNs</span></span>
<span data-ttu-id="f2573-103">在 MDN 相關的 HTTP 設定中，您可以指定接收 MDN 的 Web 伺服器預期的屬性。</span><span class="sxs-lookup"><span data-stu-id="f2573-103">As part of MDN-related HTTP settings, you can specify the properties expected by the Web server that receives the MDNs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f2573-104">所有屬性會停都用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="f2573-104">All the properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="f2573-105">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="f2573-105">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="f2573-106">例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f2573-106">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f2573-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="f2573-107">Prerequisites</span></span>  
 <span data-ttu-id="f2573-108">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="f2573-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-mdn-related-http-settings"></a><span data-ttu-id="f2573-109">設定 MDN 相關的 HTTP 設定</span><span class="sxs-lookup"><span data-stu-id="f2573-109">To configure MDN-related HTTP settings</span></span>  
  
1.  <span data-ttu-id="f2573-110">建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="f2573-110">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="f2573-111">若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f2573-111">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f2573-112">在單向協議索引標籤底下**本機主機設定**區段中，按一下**Mdn 的 HTTP 設定**。</span><span class="sxs-lookup"><span data-stu-id="f2573-112">On a one-way agreement tab, under **Local Host Settings** section, click **HTTP Settings for MDNs**.</span></span>  
  
3.  <span data-ttu-id="f2573-113">選取**忽略 SSL 憑證名稱不符**核取方塊，以確保如果伺服器名稱不符合為其產生 SSL 憑證的伺服器名稱，SSL 連接會仍會接受。</span><span class="sxs-lookup"><span data-stu-id="f2573-113">Select the **Ignore SSL Certificate Name mismatch** check box to ensure that if the server name does not match the server name that the SSL certificate was generated for, the SSL connection would still be accepted.</span></span>  
  
4.  <span data-ttu-id="f2573-114">按一下**HTTP 需要 100 繼續**HTTP Expect 標頭設定為 100-繼續進行，以指定在初始 HTTP 要求中，而會等待伺服器要求內容不包含張貼的資料。</span><span class="sxs-lookup"><span data-stu-id="f2573-114">Click **HTTP expect 100 continue** to set the HTTP Expect header to 100-continue, which specifies that the posted data not be included in the initial HTTP request, but waits for the server to request the content.</span></span>  
  
5.  <span data-ttu-id="f2573-115">按一下**保持 HTTP 連線運作**要求 HTTP 連線在要求和回應循環完成之後會保持運作。</span><span class="sxs-lookup"><span data-stu-id="f2573-115">Click **Keep HTTP connection alive** to request that an HTTP connection be kept alive after a request and response cycle has been completed.</span></span>  
  
6.  <span data-ttu-id="f2573-116">按一下**展開 HTTP 標頭**到 HTTP content-type 標頭展開至單一行。</span><span class="sxs-lookup"><span data-stu-id="f2573-116">Click **Unfold HTTP headers** to unfold the HTTP content-type header into a single line.</span></span>  
  
7.  <span data-ttu-id="f2573-117">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f2573-117">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2573-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2573-118">See Also</span></span>  
 [<span data-ttu-id="f2573-119">設定本機主機設定 (AS2)</span><span class="sxs-lookup"><span data-stu-id="f2573-119">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)