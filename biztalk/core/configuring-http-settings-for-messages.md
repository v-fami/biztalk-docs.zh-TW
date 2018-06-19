---
title: 設定訊息的 HTTP 設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ed400f1-561d-4812-adf1-20e4300fd048
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d15ebb5ff5be6678c4dc2aee3f9333f36c75c89f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233086"
---
# <a name="configuring-http-settings-for-messages"></a><span data-ttu-id="e2334-102">設定訊息的 HTTP 設定</span><span class="sxs-lookup"><span data-stu-id="e2334-102">Configuring HTTP Settings for Messages</span></span>
<span data-ttu-id="e2334-103">在訊息相關的 HTTP 設定中，您可以指定接收 AS2 訊息之 Web 伺服器預期的屬性。</span><span class="sxs-lookup"><span data-stu-id="e2334-103">As part of message-related HTTP settings, you can specify the properties expected by the Web server that receives AS2 messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2334-104">任何屬性已停用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊合作對象 a。不過，所有屬性已停都用中相同頁面**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊</span><span class="sxs-lookup"><span data-stu-id="e2334-104">No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e2334-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="e2334-105">Prerequisites</span></span>  
 <span data-ttu-id="e2334-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="e2334-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-message-related-http-settings"></a><span data-ttu-id="e2334-107">設定訊息相關的 HTTP 設定</span><span class="sxs-lookup"><span data-stu-id="e2334-107">To configure message-related HTTP settings</span></span>  
  
1.  <span data-ttu-id="e2334-108">建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="e2334-108">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="e2334-109">若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="e2334-109">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="e2334-110">在單向協議索引標籤底下**本機主機設定**區段中，按一下**訊息的 HTTP 設定**。</span><span class="sxs-lookup"><span data-stu-id="e2334-110">On a one-way agreement tab, under **Local Host Settings** section, click **HTTP Settings for Messages**.</span></span>  
  
3.  <span data-ttu-id="e2334-111">選取**忽略 SSL 憑證名稱不符**核取方塊，以確保如果伺服器名稱不符合為其產生 SSL 憑證的伺服器名稱，SSL 連接會仍會接受。</span><span class="sxs-lookup"><span data-stu-id="e2334-111">Select the **Ignore SSL Certificate Name mismatch** check box to ensure that if the server name does not match the server name that the SSL certificate was generated for, the SSL connection would still be accepted.</span></span>  
  
4.  <span data-ttu-id="e2334-112">按一下**HTTP 需要 100 繼續**HTTP Expect 標頭設定為 100-繼續進行，以指定在初始 HTTP 要求中，而會等待伺服器要求內容不包含張貼的資料。</span><span class="sxs-lookup"><span data-stu-id="e2334-112">Click **HTTP expect 100 continue** to set the HTTP Expect header to 100-continue, which specifies that the posted data not be included in the initial HTTP request, but waits for the server to request the content.</span></span>  
  
5.  <span data-ttu-id="e2334-113">按一下**保持 HTTP 連線運作**要求 HTTP 連線在要求和回應循環完成之後會保持運作。</span><span class="sxs-lookup"><span data-stu-id="e2334-113">Click **Keep HTTP connection alive** to request that an HTTP connection be kept alive after a request and response cycle has been completed.</span></span>  
  
6.  <span data-ttu-id="e2334-114">按一下**展開 HTTP 標頭**到 HTTP content-type 標頭展開至單一行。</span><span class="sxs-lookup"><span data-stu-id="e2334-114">Click **Unfold HTTP headers** to unfold the HTTP content-type header into a single line.</span></span>  
  
7.  <span data-ttu-id="e2334-115">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e2334-115">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2334-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2334-116">See Also</span></span>  
 [<span data-ttu-id="e2334-117">設定本機主機設定 (AS2)</span><span class="sxs-lookup"><span data-stu-id="e2334-117">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)