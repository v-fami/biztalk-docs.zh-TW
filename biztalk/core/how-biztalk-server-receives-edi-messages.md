---
title: "BizTalk Server 如何接收 EDI 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f3bb88c-9226-4791-b100-ba68dea45278
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb7cdda6a54db06c0388d8c72dcb65a2c8f21f02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-biztalk-server-receives-edi-messages"></a><span data-ttu-id="8be09-102">BizTalk Server 如何接收 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="8be09-102">How BizTalk Server Receives EDI Messages</span></span>
<span data-ttu-id="8be09-103">當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收 EDI 訊息時，它會執行交易夥伴協議尋查和結構描述探索、 驗證訊息、 傳送通知 （適當的話），而會剖析 EDI 批次。</span><span class="sxs-lookup"><span data-stu-id="8be09-103">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDI message, it performs trading partner agreement lookup and schema discovery, validates the message, sends an acknowledgment (if appropriate), and parses the EDI batch.</span></span> <span data-ttu-id="8be09-104">EDI 解譯器會在 EDI 接收管線中執行這項處理。</span><span class="sxs-lookup"><span data-stu-id="8be09-104">This processing is performed by the EDI disassembler in the EDI Receive Pipeline.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8be09-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="8be09-105">In This Section</span></span>  
  
-   [<span data-ttu-id="8be09-106">EDI 接收元件</span><span class="sxs-lookup"><span data-stu-id="8be09-106">EDI Receive Components</span></span>](../core/edi-receive-components.md)  
  
-   [<span data-ttu-id="8be09-107">協議解析、 結構描述探索和授權的收到的 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="8be09-107">Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages</span></span>](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)  
  
-   [<span data-ttu-id="8be09-108">EDI 解譯器的運作方式</span><span class="sxs-lookup"><span data-stu-id="8be09-108">How the EDI Disassembler Works</span></span>](../core/how-the-edi-disassembler-works.md)  
  
-   [<span data-ttu-id="8be09-109">收到的 EDI 訊息的驗證</span><span class="sxs-lookup"><span data-stu-id="8be09-109">Validation of Received EDI Messages</span></span>](../core/validation-of-received-edi-messages.md)  
  
-   [<span data-ttu-id="8be09-110">傳送 EDI 通知</span><span class="sxs-lookup"><span data-stu-id="8be09-110">Sending an EDI Acknowledgment</span></span>](../core/sending-an-edi-acknowledgment.md)  
  
-   [<span data-ttu-id="8be09-111">處理內送的批次</span><span class="sxs-lookup"><span data-stu-id="8be09-111">Processing Incoming Batches</span></span>](../core/processing-incoming-batches.md)