---
title: 小於允許的最小的次數執行迴圈重複 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0be21d1d-86da-456b-83e6-c91f1dc9fb48
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00d9b38712d8b8336daa9357bd20eb34148691b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261982"
---
# <a name="loop-repeats-less-than-the-minimum-allowed-number-of-times"></a><span data-ttu-id="99258-102">迴圈重複次數少於允許次數下限</span><span class="sxs-lookup"><span data-stu-id="99258-102">Loop repeats less than the minimum allowed number of times</span></span>
## <a name="details"></a><span data-ttu-id="99258-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="99258-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="99258-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="99258-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="99258-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="99258-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="99258-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="99258-106">Event ID</span></span>|-|  
|<span data-ttu-id="99258-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="99258-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="99258-108">EDI</span><span class="sxs-lookup"><span data-stu-id="99258-108"> EDI</span></span>|  
|<span data-ttu-id="99258-109">元件</span><span class="sxs-lookup"><span data-stu-id="99258-109">Component</span></span>|<span data-ttu-id="99258-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="99258-110">EDI Engine</span></span>|  
|<span data-ttu-id="99258-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="99258-111">Symbolic Name</span></span>|<span data-ttu-id="99258-112">X12SeLoopRepeatsLessTimesDescription</span><span class="sxs-lookup"><span data-stu-id="99258-112">X12SeLoopRepeatsLessTimesDescription</span></span>|  
|<span data-ttu-id="99258-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="99258-113">Message Text</span></span>|<span data-ttu-id="99258-114">迴圈重複次數少於允許次數下限</span><span class="sxs-lookup"><span data-stu-id="99258-114">Loop repeats less than the minimum allowed number of times</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="99258-115">說明</span><span class="sxs-lookup"><span data-stu-id="99258-115">Explanation</span></span>  
 <span data-ttu-id="99258-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換包含迴圈，重複次數少於所需的訊息結構描述的最少次數。</span><span class="sxs-lookup"><span data-stu-id="99258-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained a loop that repeated fewer times than the minimum number of times required by the message schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="99258-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="99258-117">User Action</span></span>  
 <span data-ttu-id="99258-118">若要解決這個錯誤，請確定迴圈重複交換中至少指定訊息結構描述中迴圈的 minOccurs 屬性中的次數，並再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="99258-118">To resolve this error, make sure that the loop repeats in the interchange at least the number of times in the minOccurs property specified for the loop in the message schema, and then have the interchange resent.</span></span>