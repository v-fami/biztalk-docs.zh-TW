---
title: "AS2 方案架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41e493ba-919b-4520-9c12-92d6757984ef
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c22557059bd13dd99e0b24a2291b7f121d561bbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="as2-solution-architecture"></a><span data-ttu-id="3abb3-102">AS2 方案架構</span><span class="sxs-lookup"><span data-stu-id="3abb3-102">AS2 Solution Architecture</span></span>
<span data-ttu-id="3abb3-103">AS2 處理與 EDI 處理是分開的。</span><span class="sxs-lookup"><span data-stu-id="3abb3-103">AS2 processing is performed separately from EDI processing.</span></span> <span data-ttu-id="3abb3-104">AS2 訊息的接收、處理和通知傳送，都是與 EDI 內容的處理分開。</span><span class="sxs-lookup"><span data-stu-id="3abb3-104">AS2 messages are received, processed, and an acknowledgment sent apart from the processing of the EDI payload.</span></span> <span data-ttu-id="3abb3-105">因此，AS2 處理的設計和設定都與 EDI 處理分開進行。</span><span class="sxs-lookup"><span data-stu-id="3abb3-105">As a result, AS2 processing is designed and configured apart from EDI processing.</span></span> <span data-ttu-id="3abb3-106">此外，您可以使用 AS2 傳輸 EDI 訊息或非 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="3abb3-106">In addition, you can use AS2 to transport either EDI messages or non-EDI messages.</span></span>  
  
 <span data-ttu-id="3abb3-107">本章節描述 AS2 方案的架構上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，包括端對端、 接收端和傳送端處理。</span><span class="sxs-lookup"><span data-stu-id="3abb3-107">This section describes the architecture of AS2 solutions on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], including end-to-end, receive-side, and send-side processing.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3abb3-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="3abb3-108">In This Section</span></span>  
  
-   [<span data-ttu-id="3abb3-109">AS2 傳訊</span><span class="sxs-lookup"><span data-stu-id="3abb3-109">AS2 Messaging</span></span>](../core/as2-messaging.md)  
  
-   [<span data-ttu-id="3abb3-110">中協議的 AS2 處理的角色</span><span class="sxs-lookup"><span data-stu-id="3abb3-110">The Role of Agreements in AS2 Processing</span></span>](../core/the-role-of-agreements-in-as2-processing.md)  
  
-   [<span data-ttu-id="3abb3-111">BizTalk Server 如何接收 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="3abb3-111">How BizTalk Server Receives AS2 Messages</span></span>](../core/how-biztalk-server-receives-as2-messages.md)  
  
-   [<span data-ttu-id="3abb3-112">BizTalk Server 傳送 AS2 訊息的方式</span><span class="sxs-lookup"><span data-stu-id="3abb3-112">How BizTalk Server Sends AS2 Messages</span></span>](../core/how-biztalk-server-sends-as2-messages.md)