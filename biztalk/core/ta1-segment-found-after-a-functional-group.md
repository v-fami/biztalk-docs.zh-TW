---
title: TA1 區段功能群組後，仍找到 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3d090a-0916-4a0e-82dc-2c9af9f97683
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86e9ac6e1e0c3a3b76dbc144739f3a16fddd0d67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278518"
---
# <a name="ta1-segment-found-after-a-functional-group"></a><span data-ttu-id="7dc7c-102">功能群組後，仍找到 TA1 區段</span><span class="sxs-lookup"><span data-stu-id="7dc7c-102">TA1 segment found after a functional group</span></span>
## <a name="details"></a><span data-ttu-id="7dc7c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7dc7c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7dc7c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7dc7c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7dc7c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7dc7c-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7dc7c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7dc7c-106">Event ID</span></span>|-|  
|<span data-ttu-id="7dc7c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="7dc7c-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7dc7c-108">EDI</span><span class="sxs-lookup"><span data-stu-id="7dc7c-108"> EDI</span></span>|  
|<span data-ttu-id="7dc7c-109">元件</span><span class="sxs-lookup"><span data-stu-id="7dc7c-109">Component</span></span>|<span data-ttu-id="7dc7c-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="7dc7c-110">EDI Engine</span></span>|  
|<span data-ttu-id="7dc7c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7dc7c-111">Symbolic Name</span></span>|<span data-ttu-id="7dc7c-112">TA1FoundAfterFunctionalGroup</span><span class="sxs-lookup"><span data-stu-id="7dc7c-112">TA1FoundAfterFunctionalGroup</span></span>|  
|<span data-ttu-id="7dc7c-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7dc7c-113">Message Text</span></span>|<span data-ttu-id="7dc7c-114">功能群組後，仍找到 TA1 區段。</span><span class="sxs-lookup"><span data-stu-id="7dc7c-114">TA1 segment found after a functional group.</span></span> <span data-ttu-id="7dc7c-115">因此，訊息已被拒絕</span><span class="sxs-lookup"><span data-stu-id="7dc7c-115">So, the message is being rejected</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7dc7c-116">說明</span><span class="sxs-lookup"><span data-stu-id="7dc7c-116">Explanation</span></span>  
 <span data-ttu-id="7dc7c-117">這個錯誤/警告/資訊事件表示，接收管線無法處理內送通知因為通知所包含的功能群組，然後 TA1 區段。</span><span class="sxs-lookup"><span data-stu-id="7dc7c-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming acknowledgment because the acknowledgment contained a functional group and then a TA1 segment.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7dc7c-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7dc7c-118">User Action</span></span>  
 <span data-ttu-id="7dc7c-119">若要解決這個錯誤，有的 TA1 通知會確認該交換不包含之前 TA1 區段中，功能群組，然後再重新傳送通知的寄件者。</span><span class="sxs-lookup"><span data-stu-id="7dc7c-119">To resolve this error, have the sender of the TA1 acknowledgment ensure that the interchange does not contain a functional group before the TA1 segment, and then resend the acknowledgment.</span></span>