---
title: BizTalk Server 如何傳送 EDI 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4eaf1085-4244-4df2-9d89-52ebdf6bcbbc
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4727a407c28ede98bba67774576d4d43329a946
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246630"
---
# <a name="how-biztalk-server-sends-edi-messages"></a><span data-ttu-id="0f0db-102">BizTalk Server 傳送 EDI 訊息的方式</span><span class="sxs-lookup"><span data-stu-id="0f0db-102">How BizTalk Server Sends EDI Messages</span></span>
<span data-ttu-id="0f0db-103">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送 EDI 訊息時，它會執行協議尋查和結構描述探索、驗證訊息、傳送通知 (適當情況下)，以及序列化 EDI 批次。</span><span class="sxs-lookup"><span data-stu-id="0f0db-103">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends an EDI message, it performs agreement lookup and schema discovery, validates the message, sends an acknowledgment (if appropriate), and serializes the EDI batch.</span></span> <span data-ttu-id="0f0db-104">EDI 組合器會在「EDI 傳送管線」中執行這項處理。</span><span class="sxs-lookup"><span data-stu-id="0f0db-104">This processing is performed by the EDI assembler in the EDI Send Pipeline.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f0db-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="0f0db-105">In This Section</span></span>  
  
-   [<span data-ttu-id="0f0db-106">EDI 傳送元件</span><span class="sxs-lookup"><span data-stu-id="0f0db-106">EDI Send Components</span></span>](../core/edi-send-components.md)  
  
-   [<span data-ttu-id="0f0db-107">協議解析和外寄 EDI 訊息的結構描述判斷</span><span class="sxs-lookup"><span data-stu-id="0f0db-107">Agreement Resolution and Schema Determination for Outgoing EDI Messages</span></span>](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)  
  
-   [<span data-ttu-id="0f0db-108">「 EDI 組合器 」 的運作方式</span><span class="sxs-lookup"><span data-stu-id="0f0db-108">How the EDI Assembler Works</span></span>](../core/how-the-edi-assembler-works.md)  
  
-   [<span data-ttu-id="0f0db-109">覆寫 EDI 標頭</span><span class="sxs-lookup"><span data-stu-id="0f0db-109">Overriding EDI Headers</span></span>](../core/overriding-edi-headers.md)  
  
-   [<span data-ttu-id="0f0db-110">外寄 EDI 訊息的驗證</span><span class="sxs-lookup"><span data-stu-id="0f0db-110">Validation of Outgoing EDI Messages</span></span>](../core/validation-of-outgoing-edi-messages.md)  
  
-   [<span data-ttu-id="0f0db-111">批次處理外寄 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="0f0db-111">Batching Outgoing EDI Messages</span></span>](../core/batching-outgoing-edi-messages.md)  
  
-   [<span data-ttu-id="0f0db-112">處理接收的通知</span><span class="sxs-lookup"><span data-stu-id="0f0db-112">Processing a Received Acknowledgment</span></span>](../core/processing-a-received-acknowledgment.md)