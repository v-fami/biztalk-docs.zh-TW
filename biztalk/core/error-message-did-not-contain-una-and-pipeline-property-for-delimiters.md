---
title: 訊息未包含 UNA 和分隔符號的管線屬性是格式不正確 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b761d820-e09d-4949-bb41-da9e66054c60
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6310c96f897126a498772f2147a20c84f7e926a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241838"
---
# <a name="message-did-not-contain-una-and-pipeline-property-for-delimiters-was-incorrect-format"></a><span data-ttu-id="e53c8-102">訊息未包含 UNA 和分隔符號的管線屬性是格式不正確</span><span class="sxs-lookup"><span data-stu-id="e53c8-102">Message did not contain UNA and pipeline property for delimiters was incorrect format</span></span>
## <a name="details"></a><span data-ttu-id="e53c8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e53c8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e53c8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e53c8-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e53c8-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e53c8-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="e53c8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e53c8-106">Event ID</span></span>|-|  
|<span data-ttu-id="e53c8-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e53c8-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e53c8-108">EDI</span><span class="sxs-lookup"><span data-stu-id="e53c8-108"> EDI</span></span>|  
|<span data-ttu-id="e53c8-109">元件</span><span class="sxs-lookup"><span data-stu-id="e53c8-109">Component</span></span>|<span data-ttu-id="e53c8-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e53c8-110">EDI Engine</span></span>|  
|<span data-ttu-id="e53c8-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e53c8-111">Symbolic Name</span></span>|<span data-ttu-id="e53c8-112">EfactDelimiterIncorrectFormat</span><span class="sxs-lookup"><span data-stu-id="e53c8-112">EfactDelimiterIncorrectFormat</span></span>|  
|<span data-ttu-id="e53c8-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e53c8-113">Message Text</span></span>|<span data-ttu-id="e53c8-114">訊息未包含 UNA 和分隔符號的管線屬性是格式不正確 '{0}'</span><span class="sxs-lookup"><span data-stu-id="e53c8-114">Message did not contain UNA and pipeline property for delimiters was incorrect format '{0}'</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e53c8-115">說明</span><span class="sxs-lookup"><span data-stu-id="e53c8-115">Explanation</span></span>  
 <span data-ttu-id="e53c8-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送 EDIFACT 交換因為它無法判斷用來處理交換所需的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e53c8-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming EDIFACT interchange because it could not determine the separators required to process the interchange.</span></span> <span data-ttu-id="e53c8-117">如果交換沒有 UNA 區段和 EfactDelimiters 管線屬性並未適當定義的分隔符號，這可能會發生。</span><span class="sxs-lookup"><span data-stu-id="e53c8-117">This can occur if the interchange does not have a UNA segment and the EfactDelimiters pipeline property does not adequately define the separators.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e53c8-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e53c8-118">User Action</span></span>  
 <span data-ttu-id="e53c8-119">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="e53c8-119">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="e53c8-120">請確定交換已定義的交換，分隔符號的 UNA 區段，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="e53c8-120">Make sure that the interchange has a UNA segment that defines the separators for the interchange, and then resend the interchange.</span></span>  
  
2.  <span data-ttu-id="e53c8-121">EfactDelimiters 管線屬性的傳送管線藉由開啟 BizTalk Server 管理主控台，以滑鼠右鍵按一下接收位置，將接收交換、 按一下 [內容]，按一下省略符號的管線，來設定和然後輸入字串，包含分隔符號的值。</span><span class="sxs-lookup"><span data-stu-id="e53c8-121">Set the EfactDelimiters pipeline property for the send pipeline by opening the BizTalk Server Administration Console, right-clicking the receive location that will be receiving the interchange, clicking Properties, clicking the ellipsis for the pipeline, and then entering a string containing the values of the separators.</span></span>