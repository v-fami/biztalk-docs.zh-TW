---
title: "沒有要傳送的批次元素並無法傳送空白訊息，因為它不會設定合作對象 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0752079a-173e-4de3-96f4-e5de01b799b5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80dcf96feef006a2576afc5829e7927e003524a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="there-are-no-batch-elements-to-send-and-an-empty-message-cannot-be-sent-as-it-is-not-configured-for-party"></a><span data-ttu-id="08370-102">沒有要傳送的批次元素並無法傳送空白訊息，因為它不會設定合作對象</span><span class="sxs-lookup"><span data-stu-id="08370-102">There are no batch elements to send and an empty message cannot be sent as it is not configured for party</span></span>
## <a name="details"></a><span data-ttu-id="08370-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="08370-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08370-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="08370-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="08370-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="08370-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="08370-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="08370-106">Event ID</span></span>|-|  
|<span data-ttu-id="08370-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="08370-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="08370-108">EDI</span><span class="sxs-lookup"><span data-stu-id="08370-108"> EDI</span></span>|  
|<span data-ttu-id="08370-109">元件</span><span class="sxs-lookup"><span data-stu-id="08370-109">Component</span></span>|<span data-ttu-id="08370-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="08370-110">Batching Engine</span></span>|  
|<span data-ttu-id="08370-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="08370-111">Symbolic Name</span></span>|<span data-ttu-id="08370-112">EmptyMessageNotAllowed</span><span class="sxs-lookup"><span data-stu-id="08370-112">EmptyMessageNotAllowed</span></span>|  
|<span data-ttu-id="08370-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="08370-113">Message Text</span></span>|<span data-ttu-id="08370-114">沒有要傳送的批次元素並無法傳送空白訊息，因為它不會設定合作對象 {0}</span><span class="sxs-lookup"><span data-stu-id="08370-114">There are no batch elements to send and an empty message cannot be sent as it is not configured for party {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="08370-115">說明</span><span class="sxs-lookup"><span data-stu-id="08370-115">Explanation</span></span>  
 <span data-ttu-id="08370-116">這個警告表示任何批次訊息已傳送排程為基礎的批次程序中，因為有尚未收到任何批次項目，當批次釋放已排程，以及空的批次訊號未啟用。</span><span class="sxs-lookup"><span data-stu-id="08370-116">This Warning indicates that no batch message was sent in a schedule-based batching process because no batch elements had been received when the batch release was scheduled, and the empty batch signal has not been enabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="08370-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="08370-117">User Action</span></span>  
 <span data-ttu-id="08370-118">若要避免此警告訊息公佈，請透過下列方式設定空的批次訊號：</span><span class="sxs-lookup"><span data-stu-id="08370-118">To prevent this warning from being posted, configure the empty batch signal by doing the following:</span></span>  
  
1.  <span data-ttu-id="08370-119">開啟 [BizTalk Server 管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="08370-119">Open the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="08370-120">移至合作對象節點。</span><span class="sxs-lookup"><span data-stu-id="08370-120">Move to the Parties node.</span></span>  
  
3.  <span data-ttu-id="08370-121">開啟 [EDI 屬性] 對話方塊的合作對象。</span><span class="sxs-lookup"><span data-stu-id="08370-121">Open the EDI Properties dialog box for the party.</span></span>  
  
4.  <span data-ttu-id="08370-122">按一下 [交換批次建立設定] 節點 （適用於適當的編碼方式）。</span><span class="sxs-lookup"><span data-stu-id="08370-122">Click the Interchange Batch Creation Settings node (for the appropriate encoding).</span></span>  
  
5.  <span data-ttu-id="08370-123">按一下 排程器。</span><span class="sxs-lookup"><span data-stu-id="08370-123">Click the Scheduler.</span></span>  
  
6.  <span data-ttu-id="08370-124">按一下 [傳送空的批次訊號] 屬性。</span><span class="sxs-lookup"><span data-stu-id="08370-124">Click the Send empty batch signal property.</span></span>