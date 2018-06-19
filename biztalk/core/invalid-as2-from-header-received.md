---
title: 無效的 AS2-從收到的標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d773e09-8526-4533-9066-8e743e65a688
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f20a74e60a6365c0c16e139e8b2caca1bc33646
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256886"
---
# <a name="invalid-as2-from-header-received"></a><span data-ttu-id="668cc-102">收到無效的 AS2-From 標頭</span><span class="sxs-lookup"><span data-stu-id="668cc-102">Invalid AS2-From header received</span></span>
## <a name="details"></a><span data-ttu-id="668cc-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="668cc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="668cc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="668cc-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="668cc-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="668cc-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="668cc-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="668cc-106">Event ID</span></span>|-|  
|<span data-ttu-id="668cc-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="668cc-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="668cc-108">EDI</span><span class="sxs-lookup"><span data-stu-id="668cc-108"> EDI</span></span>|  
|<span data-ttu-id="668cc-109">元件</span><span class="sxs-lookup"><span data-stu-id="668cc-109">Component</span></span>|<span data-ttu-id="668cc-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="668cc-110">AS2 Engine</span></span>|  
|<span data-ttu-id="668cc-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="668cc-111">Symbolic Name</span></span>|<span data-ttu-id="668cc-112">InvalidAS2FromNameHeaderReceivedError</span><span class="sxs-lookup"><span data-stu-id="668cc-112">InvalidAS2FromNameHeaderReceivedError</span></span>|  
|<span data-ttu-id="668cc-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="668cc-113">Message Text</span></span>|<span data-ttu-id="668cc-114">收到無效的 AS2-From 標頭。</span><span class="sxs-lookup"><span data-stu-id="668cc-114">Invalid AS2-From header received.</span></span>  <span data-ttu-id="668cc-115">值： {0}</span><span class="sxs-lookup"><span data-stu-id="668cc-115">Value: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="668cc-116">說明</span><span class="sxs-lookup"><span data-stu-id="668cc-116">Explanation</span></span>  
 <span data-ttu-id="668cc-117">這個錯誤/警告/資訊事件表示，由於訊息中的 AS2-From 標頭值不符合 AS2 RFC 4130 中的規格，因此接收管線無法處理內送交換。</span><span class="sxs-lookup"><span data-stu-id="668cc-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the AS2-From header in the message did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="668cc-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="668cc-118">User Action</span></span>  
 <span data-ttu-id="668cc-119">若要解決這個錯誤，請確認訊息之 AS2-From 標頭中的值符合 AS2 RFC 4130 第 6.2 節的規格，然後再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="668cc-119">To resolve this error, make sure that the value in the AS2-From header of the message conforms to the specifications in section 6.2 of AS2 RFC 4130, and then have the message resent.</span></span>