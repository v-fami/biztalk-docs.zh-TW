---
title: 沒有要傳送的批次項目，並無法傳送空白訊息，因為它不會針對合作對象設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0752079a-173e-4de3-96f4-e5de01b799b5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73d0d44c8a5a206748eb128cd2461d1d04b54c93
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976663"
---
# <a name="there-are-no-batch-elements-to-send-and-an-empty-message-cannot-be-sent-as-it-is-not-configured-for-party"></a><span data-ttu-id="0eb98-102">沒有要傳送的批次項目，並無法傳送空白訊息，因為它不會針對合作對象設定</span><span class="sxs-lookup"><span data-stu-id="0eb98-102">There are no batch elements to send and an empty message cannot be sent as it is not configured for party</span></span>
## <a name="details"></a><span data-ttu-id="0eb98-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0eb98-103">Details</span></span>  
  
|                 |                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="0eb98-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0eb98-104">Product Name</span></span>   |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| <span data-ttu-id="0eb98-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0eb98-105">Product Version</span></span> |                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                           |
|    <span data-ttu-id="0eb98-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0eb98-106">Event ID</span></span>     |                                                       -                                                       |
|  <span data-ttu-id="0eb98-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="0eb98-107">Event Source</span></span>   |            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0eb98-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="0eb98-108"> EDI</span></span>             |
|    <span data-ttu-id="0eb98-109">元件</span><span class="sxs-lookup"><span data-stu-id="0eb98-109">Component</span></span>    |                                                <span data-ttu-id="0eb98-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="0eb98-110">Batching Engine</span></span>                                                |
|  <span data-ttu-id="0eb98-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0eb98-111">Symbolic Name</span></span>  |                                            <span data-ttu-id="0eb98-112">EmptyMessageNotAllowed</span><span class="sxs-lookup"><span data-stu-id="0eb98-112">EmptyMessageNotAllowed</span></span>                                             |
|  <span data-ttu-id="0eb98-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0eb98-113">Message Text</span></span>   | <span data-ttu-id="0eb98-114">沒有要傳送的批次項目，並無法傳送空白訊息，因為它不會針對合作對象設定 {0}</span><span class="sxs-lookup"><span data-stu-id="0eb98-114">There are no batch elements to send and an empty message cannot be sent as it is not configured for party {0}</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="0eb98-115">說明</span><span class="sxs-lookup"><span data-stu-id="0eb98-115">Explanation</span></span>  
 <span data-ttu-id="0eb98-116">這則警告指出，批次沒有傳送任何訊息在排程為基礎的批次程序中因為已排程批次釋放，並將空的批次訊號尚未啟用時，先前已收到批次元素。</span><span class="sxs-lookup"><span data-stu-id="0eb98-116">This Warning indicates that no batch message was sent in a schedule-based batching process because no batch elements had been received when the batch release was scheduled, and the empty batch signal has not been enabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0eb98-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0eb98-117">User Action</span></span>  
 <span data-ttu-id="0eb98-118">若要避免這個警告，發佈，請透過下列方式設定空的批次訊號：</span><span class="sxs-lookup"><span data-stu-id="0eb98-118">To prevent this warning from being posted, configure the empty batch signal by doing the following:</span></span>  
  
1.  <span data-ttu-id="0eb98-119">開啟 [BizTalk Server 管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="0eb98-119">Open the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="0eb98-120">將移至 [合作對象] 節點。</span><span class="sxs-lookup"><span data-stu-id="0eb98-120">Move to the Parties node.</span></span>  
  
3.  <span data-ttu-id="0eb98-121">開啟 [EDI 屬性] 對話方塊中的合作對象。</span><span class="sxs-lookup"><span data-stu-id="0eb98-121">Open the EDI Properties dialog box for the party.</span></span>  
  
4.  <span data-ttu-id="0eb98-122">按一下 [交換批次建立設定] 節點 （適用於適當的編碼方式）。</span><span class="sxs-lookup"><span data-stu-id="0eb98-122">Click the Interchange Batch Creation Settings node (for the appropriate encoding).</span></span>  
  
5.  <span data-ttu-id="0eb98-123">按一下 排程器。</span><span class="sxs-lookup"><span data-stu-id="0eb98-123">Click the Scheduler.</span></span>  
  
6.  <span data-ttu-id="0eb98-124">按一下 傳送空的批次訊號 」 屬性。</span><span class="sxs-lookup"><span data-stu-id="0eb98-124">Click the Send empty batch signal property.</span></span>