---
title: "空白的 AS2 訊息已接收並暫停 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 349f7134-d039-44ab-b2b3-d378d38dfd38
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90c8221c7e0bd5b297b33118b8672fbe55612244
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="an-empty-as2-message-was-received-and-suspended"></a><span data-ttu-id="945fe-102">空白的 AS2 訊息已接收並暫停</span><span class="sxs-lookup"><span data-stu-id="945fe-102">An empty AS2 message was received and suspended</span></span>
## <a name="details"></a><span data-ttu-id="945fe-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="945fe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="945fe-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="945fe-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="945fe-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="945fe-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="945fe-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="945fe-106">Event ID</span></span>|-|  
|<span data-ttu-id="945fe-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="945fe-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="945fe-108">EDI</span><span class="sxs-lookup"><span data-stu-id="945fe-108"> EDI</span></span>|  
|<span data-ttu-id="945fe-109">元件</span><span class="sxs-lookup"><span data-stu-id="945fe-109">Component</span></span>|<span data-ttu-id="945fe-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="945fe-110">AS2 Engine</span></span>|  
|<span data-ttu-id="945fe-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="945fe-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="945fe-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="945fe-112">Message Text</span></span>|<span data-ttu-id="945fe-113">收到空白的 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="945fe-113">An empty AS2 message was received.</span></span>  <span data-ttu-id="945fe-114">將擱置此訊息。</span><span class="sxs-lookup"><span data-stu-id="945fe-114">The message will be suspended.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="945fe-115">說明</span><span class="sxs-lookup"><span data-stu-id="945fe-115">Explanation</span></span>  
 <span data-ttu-id="945fe-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法處理內送 AS2 訊息，因為訊息不包含主體。</span><span class="sxs-lookup"><span data-stu-id="945fe-116">This Error/Warning/Information event indicates BizTalk Server could not process the incoming AS2 message because the message does not contain a body.</span></span> <span data-ttu-id="945fe-117">主體必須以兩個歸位字元 / 摘要分隔標頭。</span><span class="sxs-lookup"><span data-stu-id="945fe-117">The body must be separated from the headers by two carriage return/line feeds.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="945fe-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="945fe-118">User Action</span></span>  
 <span data-ttu-id="945fe-119">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="945fe-119">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="945fe-120">請確定傳送合作對象將 AS2 訊息內文 （從標頭以兩個歸位字元 / 摘要分隔），再將它傳送。</span><span class="sxs-lookup"><span data-stu-id="945fe-120">Ensure the sending party adds a body (separated from the headers by two carriage return/line feeds) to the AS2 message before sending it.</span></span>