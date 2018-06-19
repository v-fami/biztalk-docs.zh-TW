---
title: 一般檔案訊息的結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00f2adf6-a47c-498b-b5ae-c6bd55bafceb
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: badb8aacf6f2ed8ce9e38f1ea6bbe432a1d3b89e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278934"
---
# <a name="structure-of-a-flat-file-message"></a><span data-ttu-id="e498b-102">一般檔案訊息的結構</span><span class="sxs-lookup"><span data-stu-id="e498b-102">Structure of a Flat File Message</span></span>
<span data-ttu-id="e498b-103">在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的內容中，一般檔案執行個體訊息是包含三種邏輯部分的文字檔：依序為標頭、內文及結尾。</span><span class="sxs-lookup"><span data-stu-id="e498b-103">In the context of Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], a flat file instance message is a text file that can contain three logical parts: a header, a body, and a trailer, in that order.</span></span> <span data-ttu-id="e498b-104">標頭和結尾為選擇性。</span><span class="sxs-lookup"><span data-stu-id="e498b-104">Both the header and the trailer are optional.</span></span> <span data-ttu-id="e498b-105">下列範例將顯示包含這三個部分的一般檔案執行個體訊息，其中內文是以粗體顯示。</span><span class="sxs-lookup"><span data-stu-id="e498b-105">The following example shows a flat file instance message that consists of all three parts, with the body shown in bold type.</span></span>  
  
```  
Microsoft Corporation  
One Microsoft Way  
Redmond, WA 98033  
  
TRANSACTION-1111,1  
  
```  
  
 <span data-ttu-id="e498b-106">為了讓一般檔案解譯器能夠正確地辨識一般檔案執行個體訊息的標頭、內文及結尾，您必須各別為其建立和設定各自的結構描述。</span><span class="sxs-lookup"><span data-stu-id="e498b-106">For the flat file disassembler to correctly distinguish the header, the body, and the trailer of a flat file instance message, you must create and configure a separate schema for each of them.</span></span>  
  
 <span data-ttu-id="e498b-107">在一般檔案執行個體訊息的特定部分，分組資料的不同項目記錄，到哪一個本身可以包含子記錄和最終的資料，又稱為欄位的個別項目。</span><span class="sxs-lookup"><span data-stu-id="e498b-107">Within a particular part of a flat file instance message, different items of data are grouped into records, which themselves can contain subrecords and ultimately the individual items of data, known as fields.</span></span> <span data-ttu-id="e498b-108">這些記錄及欄位可以使用兩種不同的基本方法之一來加以識別。</span><span class="sxs-lookup"><span data-stu-id="e498b-108">These records and fields are distinguished from each other using one of two different basic methodologies.</span></span> <span data-ttu-id="e498b-109">第一種方法 (稱為位置) 會定義每個資料項目預先建立的長度，且若資料項目長度短於預期的長度則會使用填補字元填滿。</span><span class="sxs-lookup"><span data-stu-id="e498b-109">The first methodology, known as positional, defines each item of data to be of a pre-established length, with pad characters being used to bring a shorter item of data up to its expected length.</span></span> <span data-ttu-id="e498b-110">第二種方法 (稱為分隔) 會使用一或多個特殊字元來區分每個資料項目。</span><span class="sxs-lookup"><span data-stu-id="e498b-110">The second methodology, known as delimited, uses one or more special characters to separate items of data from each other.</span></span> <span data-ttu-id="e498b-111">此方法能避免多餘的填補字元，但在資料本身包含用來當作分隔符號的字元或字元序列時，需要一些特殊考量。</span><span class="sxs-lookup"><span data-stu-id="e498b-111">This methodology avoids the need for otherwise superfluous pad characters, but introduces some special considerations when the data itself contains the character or sequence of characters being used as a delimiter.</span></span>  
  
 <span data-ttu-id="e498b-112">接下來將提供 BizTalk Server 如何處理一般檔案執行個體訊息之標題、內文及結尾的簡要說明，尤其是它如何判斷選擇性的部分是否存在，以及如何分隔輸入一般檔案執行個體訊息，以及結合輸出一般檔案執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="e498b-112">The remainder of this section provides a high-level overview of how BizTalk Server handles headers, bodies, and trailers in flat file instance messages, and specifically, how it decides whether the optional parts are present, and how it separates the parts of inbound flat file instance messages and combines the parts of outbound flat file instance messages.</span></span> <span data-ttu-id="e498b-113">本節也會提供採用位置記錄及欄位的一般檔案執行個體訊息，與採用分隔記錄及欄位的一般檔案執行個體訊息之間相異處的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="e498b-113">This section also provides additional information about the differences between flat file instance messages that employ positional records and fields and flat file instance messages that employ delimited records and fields.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e498b-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="e498b-114">In This Section</span></span>  
  
-   [<span data-ttu-id="e498b-115">一般檔案訊息標頭</span><span class="sxs-lookup"><span data-stu-id="e498b-115">Flat File Message Headers</span></span>](../core/flat-file-message-headers.md)  
  
-   [<span data-ttu-id="e498b-116">一般檔案訊息內文</span><span class="sxs-lookup"><span data-stu-id="e498b-116">Flat File Message Bodies</span></span>](../core/flat-file-message-bodies.md)  
  
-   [<span data-ttu-id="e498b-117">一般檔案訊息結尾</span><span class="sxs-lookup"><span data-stu-id="e498b-117">Flat File Message Trailers</span></span>](../core/flat-file-message-trailers.md)  
  
-   [<span data-ttu-id="e498b-118">具有位置記錄的一般檔案訊息</span><span class="sxs-lookup"><span data-stu-id="e498b-118">Flat File Messages with Positional Records</span></span>](../core/flat-file-messages-with-positional-records.md)  
  
-   [<span data-ttu-id="e498b-119">具有分隔記錄的一般檔案訊息</span><span class="sxs-lookup"><span data-stu-id="e498b-119">Flat File Messages with Delimited Records</span></span>](../core/flat-file-messages-with-delimited-records.md)  
  
-   [<span data-ttu-id="e498b-120">移轉一般檔案記錄</span><span class="sxs-lookup"><span data-stu-id="e498b-120">Migrating Flat File Records</span></span>](../core/migrating-flat-file-records.md)