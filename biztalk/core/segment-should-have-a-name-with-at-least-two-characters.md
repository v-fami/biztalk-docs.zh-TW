---
title: "區段應該有至少兩個字元的名稱 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f80bbc4a-151a-4094-8640-1944e8812730
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70d4b39aa9421e4b60fd9e0c4415c69862c00526
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="segment-should-have-a-name-with-at-least-two-characters"></a><span data-ttu-id="d017a-102">區段應該有至少兩個字元的名稱</span><span class="sxs-lookup"><span data-stu-id="d017a-102">Segment should have a name with at least two characters</span></span>
## <a name="details"></a><span data-ttu-id="d017a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d017a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d017a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d017a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d017a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d017a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d017a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d017a-106">Event ID</span></span>|-|  
|<span data-ttu-id="d017a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d017a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d017a-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d017a-108"> EDI</span></span>|  
|<span data-ttu-id="d017a-109">元件</span><span class="sxs-lookup"><span data-stu-id="d017a-109">Component</span></span>|<span data-ttu-id="d017a-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d017a-110">EDI Engine</span></span>|  
|<span data-ttu-id="d017a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d017a-111">Symbolic Name</span></span>|<span data-ttu-id="d017a-112">SchemaCode103EInvalidTagLength</span><span class="sxs-lookup"><span data-stu-id="d017a-112">SchemaCode103EInvalidTagLength</span></span>|  
|<span data-ttu-id="d017a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d017a-113">Message Text</span></span>|<span data-ttu-id="d017a-114">區段應該有至少 2 個字元的名稱</span><span class="sxs-lookup"><span data-stu-id="d017a-114">Segment should have a name with at least 2 characters</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d017a-115">說明</span><span class="sxs-lookup"><span data-stu-id="d017a-115">Explanation</span></span>  
 <span data-ttu-id="d017a-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，因為交換中的區段名稱沒有至少 2 個字元。</span><span class="sxs-lookup"><span data-stu-id="d017a-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the name of a segment in the interchange does not have at least two characters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d017a-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d017a-117">User Action</span></span>  
 <span data-ttu-id="d017a-118">若要解決此錯誤，請指示交換的傳送者確定交換的每個區段名稱都有至少 2 個字元，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="d017a-118">To resolve this error, have the sender of the interchange ensure that the name of each segment in the interchange has at least two characters, and then resend the interchange.</span></span>