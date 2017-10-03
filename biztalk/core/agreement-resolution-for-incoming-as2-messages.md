---
title: "內送 AS2 訊息的協議解析 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 746d01af-de6a-4d5d-9433-b0e1a2b41861
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24e5e9795979ddf0a8b8f13fe7ab53bd4e783bd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-resolution-for-incoming-as2-messages"></a><span data-ttu-id="bd2af-102">內送 AS2 訊息的協議解析</span><span class="sxs-lookup"><span data-stu-id="bd2af-102">Agreement Resolution for Incoming AS2 Messages</span></span>
<span data-ttu-id="bd2af-103">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 透過 HTTP/HTTPS 傳輸接收 EDIINT/AS2 編碼訊息時，它會嘗試判斷傳送該訊息的交易夥伴商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="bd2af-103">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDIINT/AS2-encoded message over HTTP/HTTPS transport, it attempts to determine the trading partner’s business profile that sent the message.</span></span> <span data-ttu-id="bd2af-104">它會嘗試執行下列步驟 (順序如下所示) 來進行判斷：</span><span class="sxs-lookup"><span data-stu-id="bd2af-104">It does so by attempting to do the following (in the order shown):</span></span>  
  
1.  <span data-ttu-id="bd2af-105">比對內 AS2-中的值將傳入訊息標頭**AS2-從**中**識別碼**頁面中，單向 AS2 協議**協議屬性**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bd2af-105">Make a match between the AS2-From header in the incoming message with the value for **AS2-From** in the **Identifiers** page of the one-way AS2 agreement in the **Agreement Properties** dialog box.</span></span>  
  
2.  <span data-ttu-id="bd2af-106">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法判斷協議，它就會嘗試針對內送訊息所設定的 AS2-From 內容屬性與交易夥伴名稱進行比對。</span><span class="sxs-lookup"><span data-stu-id="bd2af-106">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot determine the agreement, it will attempt to match the AS2-From context property that is set for the incoming message with the name of a trading partner.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd2af-107">AS2-From 標頭只能包含 ASCII 字元，因此，您必須確認您的交易夥伴名稱與 AS2-From 別名也只包含 ASCII 字元。</span><span class="sxs-lookup"><span data-stu-id="bd2af-107">Since the AS2-From header can only contain ASCII characters, you must ensure that your trading partner name and the AS2-From alias also contain only ASCII characters.</span></span> <span data-ttu-id="bd2af-108">如果沒有完全相符的項目，BizTalk 將無法根據內送訊息標頭判斷協議。</span><span class="sxs-lookup"><span data-stu-id="bd2af-108">If an exact match does not occur, BizTalk will be unable to determine the agreement based on the incoming message headers.</span></span>  
  
 <span data-ttu-id="bd2af-109">只有在判斷協議之後，AS2 接收管線才會處理訊息。</span><span class="sxs-lookup"><span data-stu-id="bd2af-109">The AS2 receive pipeline will process the message only if an agreement is determined.</span></span> <span data-ttu-id="bd2af-110">與 EDI 處理不同的是，當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法判斷協議時，沒有可用的後援 AS2 屬性。</span><span class="sxs-lookup"><span data-stu-id="bd2af-110">Unlike in EDI processing, there are no fallback AS2 properties that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can use if it cannot determine the agreement.</span></span>  
  
 <span data-ttu-id="bd2af-111">一旦管線判斷出協議，它會檢查設定**使用協議設定進行驗證並以 MDN 取代訊息標頭**屬性**驗證**頁面的單向 AS2中的協議**協議設定** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bd2af-111">Once the pipeline has determined the agreement, it will check the setting of the **Use agreement settings for validation and MDN instead message header** property in the **Validation** page of the one-way AS2 agreement in the **Agreement Settings** dialog box.</span></span> <span data-ttu-id="bd2af-112">如果該屬性為核取狀態，接收管線會使用該協議屬性來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="bd2af-112">If that property is checked, the receive pipeline will use the agreement properties to process the message.</span></span> <span data-ttu-id="bd2af-113">若該屬性已取消核取，接收管線會使用訊息之 AS2 標頭的值來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="bd2af-113">If the property is cleared, the receive pipeline will use the values in the AS2 header of the message to process it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd2af-114">在協議解析期間所判斷出的 AS2 協議可能與 EDI 內容的協議不同。</span><span class="sxs-lookup"><span data-stu-id="bd2af-114">The AS2 agreement that is determined during agreement resolution may not be the same agreement as the EDI payload.</span></span> <span data-ttu-id="bd2af-115">AS2 和 EDI 不必共用相同的協議，因為 AS2 協議可能代表從多個合作對象路由 EDI 文件的 Clearinghouse。</span><span class="sxs-lookup"><span data-stu-id="bd2af-115">There is no requirement that AS2 and EDI must share the same agreement, as the AS2 agreement may represent a clearinghouse that routes EDI documents from multiple parties.</span></span>  
  
 <span data-ttu-id="bd2af-116">如需接收程序的詳細資訊，請參閱[處理內送 AS2 訊息](../core/processing-an-incoming-as2-message.md)。</span><span class="sxs-lookup"><span data-stu-id="bd2af-116">For more details on the receive process, see [Processing an Incoming AS2 Message](../core/processing-an-incoming-as2-message.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd2af-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd2af-117">See Also</span></span>  
 [<span data-ttu-id="bd2af-118">BizTalk Server 如何接收 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="bd2af-118">How BizTalk Server Receives AS2 Messages</span></span>](../core/how-biztalk-server-receives-as2-messages.md)