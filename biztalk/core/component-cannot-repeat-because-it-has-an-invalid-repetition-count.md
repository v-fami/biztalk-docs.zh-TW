---
title: 元件無法重複，因為它有無效的重複計數 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 040d7ea4-60a9-495f-91d7-b5b868957e2d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d535d72b5f265f07e6ae3fb468ed56efdc7975b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231678"
---
# <a name="component-cannot-repeat-because-it-has-an-invalid-repetition-count"></a><span data-ttu-id="27f2d-102">元件無法重複，因為它有無效的重複計數</span><span class="sxs-lookup"><span data-stu-id="27f2d-102">Component cannot repeat because it has an invalid repetition count</span></span>
## <a name="details"></a><span data-ttu-id="27f2d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="27f2d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="27f2d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="27f2d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="27f2d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="27f2d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="27f2d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="27f2d-106">Event ID</span></span>|-|  
|<span data-ttu-id="27f2d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="27f2d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="27f2d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="27f2d-108"> EDI</span></span>|  
|<span data-ttu-id="27f2d-109">元件</span><span class="sxs-lookup"><span data-stu-id="27f2d-109">Component</span></span>|<span data-ttu-id="27f2d-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="27f2d-110">EDI Engine</span></span>|  
|<span data-ttu-id="27f2d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="27f2d-111">Symbolic Name</span></span>|<span data-ttu-id="27f2d-112">SchemaCode118EInvalidRepetition</span><span class="sxs-lookup"><span data-stu-id="27f2d-112">SchemaCode118EInvalidRepetition</span></span>|  
|<span data-ttu-id="27f2d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="27f2d-113">Message Text</span></span>|<span data-ttu-id="27f2d-114">元件無法重複，它的重複計數 {0} 無效</span><span class="sxs-lookup"><span data-stu-id="27f2d-114">Component cannot repeat, it has an invalid repetition count of {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="27f2d-115">說明</span><span class="sxs-lookup"><span data-stu-id="27f2d-115">Explanation</span></span>  
 <span data-ttu-id="27f2d-116">這個錯誤/警告/資訊事件表示，由於交換中的元素元件、元素、區段或迴圈重複，但結構描述不允許重複，因此接收管線無法處理內送交換，或傳送管線無法處理外寄交換。</span><span class="sxs-lookup"><span data-stu-id="27f2d-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because an element component, element, segment, or loop was repeated in the interchange while the schema does not allow the repetition.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="27f2d-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="27f2d-117">User Action</span></span>  
 <span data-ttu-id="27f2d-118">若要解決這個錯誤，請確認交換中的元素元件、元素、區段或迴圈未重複 (如結構描述要求)，然後再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="27f2d-118">To resolve this error, ensure that the element component, element, segment, or loop does not repeat in the interchange, as required by the schema, and have the message resent.</span></span>