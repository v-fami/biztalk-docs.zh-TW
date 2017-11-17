---
title: "在序列化期間根節點不放在開始項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ea4aa6f-0f9c-4b7b-b7f6-24a5ce954048
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3dced7e36802dd9d9ec9620272fc8a96bd6b590
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="during-serialization-root-node-is-not-placed-at-start-element"></a><span data-ttu-id="659cb-102">在序列化期間根節點不被放在開始項目</span><span class="sxs-lookup"><span data-stu-id="659cb-102">During serialization root node is not placed at start element</span></span>
## <a name="details"></a><span data-ttu-id="659cb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="659cb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="659cb-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="659cb-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="659cb-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="659cb-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="659cb-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="659cb-106">Event ID</span></span>|-|  
|<span data-ttu-id="659cb-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="659cb-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="659cb-108">EDI</span><span class="sxs-lookup"><span data-stu-id="659cb-108"> EDI</span></span>|  
|<span data-ttu-id="659cb-109">元件</span><span class="sxs-lookup"><span data-stu-id="659cb-109">Component</span></span>|<span data-ttu-id="659cb-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="659cb-110">EDI Engine</span></span>|  
|<span data-ttu-id="659cb-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="659cb-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="659cb-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="659cb-112">Message Text</span></span>|<span data-ttu-id="659cb-113">在序列化期間根節點不被放在開始項目</span><span class="sxs-lookup"><span data-stu-id="659cb-113">During serialization root node is not placed at start element</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="659cb-114">說明</span><span class="sxs-lookup"><span data-stu-id="659cb-114">Explanation</span></span>  
 <span data-ttu-id="659cb-115">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交易集的開頭不是 ST 或 UNH 標頭。</span><span class="sxs-lookup"><span data-stu-id="659cb-115">This Error/Warning/Information event indicates that the receive pipeline could not process an incoming interchange because the transaction set does not start with an ST or UNH header.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="659cb-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="659cb-116">User Action</span></span>  
 <span data-ttu-id="659cb-117">若要解決這個錯誤，請確定每個交換中交易集開頭 ST 區段 （對於 X12 交換） 或 UNH 區段 （EDIFACT 交換），然後再重新提交交換。</span><span class="sxs-lookup"><span data-stu-id="659cb-117">To resolve this error, ensure that each of the transaction sets in an interchange starts with an ST segment (for X12 interchanges) or an UNH segment (for EDIFACT interchanges), and then resubmit the interchange.</span></span>