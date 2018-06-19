---
title: 最大的時間內發生的迴圈 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ac9f5d3-04ec-4c40-8a1f-17ef0b143cda
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 827ab88a2676cd052ee1ea3ba3a4bd7bd80f1912
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261878"
---
# <a name="loop-occurs-over-maximum-times"></a><span data-ttu-id="e1896-102">最大的時間內發生的迴圈</span><span class="sxs-lookup"><span data-stu-id="e1896-102">Loop Occurs Over Maximum Times</span></span>
## <a name="details"></a><span data-ttu-id="e1896-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e1896-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1896-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e1896-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e1896-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e1896-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="e1896-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e1896-106">Event ID</span></span>|-|  
|<span data-ttu-id="e1896-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e1896-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e1896-108">EDI</span><span class="sxs-lookup"><span data-stu-id="e1896-108"> EDI</span></span>|  
|<span data-ttu-id="e1896-109">元件</span><span class="sxs-lookup"><span data-stu-id="e1896-109">Component</span></span>|<span data-ttu-id="e1896-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e1896-110">EDI Engine</span></span>|  
|<span data-ttu-id="e1896-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e1896-111">Symbolic Name</span></span>|<span data-ttu-id="e1896-112">X12LoopOccursOverMaximumTimesDescription</span><span class="sxs-lookup"><span data-stu-id="e1896-112">X12LoopOccursOverMaximumTimesDescription</span></span>|  
|<span data-ttu-id="e1896-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e1896-113">Message Text</span></span>|<span data-ttu-id="e1896-114">最高次數內發生的迴圈</span><span class="sxs-lookup"><span data-stu-id="e1896-114">Loops Occurs Over Maximum Times</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e1896-115">說明</span><span class="sxs-lookup"><span data-stu-id="e1896-115">Explanation</span></span>  
 <span data-ttu-id="e1896-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換包含迴圈，重複多次的訊息結構描述所需的時間的最大數目。</span><span class="sxs-lookup"><span data-stu-id="e1896-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained a loop that repeated more times than the maximum number of times required by the message schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e1896-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e1896-117">User Action</span></span>  
 <span data-ttu-id="e1896-118">若要解決這個錯誤，請確定迴圈重複交換中不超過指定的訊息結構描述中迴圈 maxOccurs 屬性中的次數，並再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="e1896-118">To resolve this error, make sure that the loop repeats in the interchange no more than the number of times in the maxOccurs property specified for the loop in the message schema, and then have the interchange resent.</span></span>