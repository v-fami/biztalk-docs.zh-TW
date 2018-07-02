---
title: 最高次數內發生的迴圈 |Microsoft Docs
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
ms.openlocfilehash: 6587e5b5dcef641f37f24005fe594a084e5de12d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979599"
---
# <a name="loop-occurs-over-maximum-times"></a><span data-ttu-id="c83b3-102">最高次數內發生的迴圈</span><span class="sxs-lookup"><span data-stu-id="c83b3-102">Loop Occurs Over Maximum Times</span></span>
## <a name="details"></a><span data-ttu-id="c83b3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c83b3-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="c83b3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c83b3-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="c83b3-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c83b3-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="c83b3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c83b3-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="c83b3-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="c83b3-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c83b3-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c83b3-108"> EDI</span></span> |
|    <span data-ttu-id="c83b3-109">元件</span><span class="sxs-lookup"><span data-stu-id="c83b3-109">Component</span></span>    |                                       <span data-ttu-id="c83b3-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="c83b3-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="c83b3-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c83b3-111">Symbolic Name</span></span>  |                        <span data-ttu-id="c83b3-112">X12LoopOccursOverMaximumTimesDescription</span><span class="sxs-lookup"><span data-stu-id="c83b3-112">X12LoopOccursOverMaximumTimesDescription</span></span>                        |
|  <span data-ttu-id="c83b3-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c83b3-113">Message Text</span></span>   |                            <span data-ttu-id="c83b3-114">最高次數內發生的迴圈</span><span class="sxs-lookup"><span data-stu-id="c83b3-114">Loops Occurs Over Maximum Times</span></span>                             |
  
## <a name="explanation"></a><span data-ttu-id="c83b3-115">說明</span><span class="sxs-lookup"><span data-stu-id="c83b3-115">Explanation</span></span>  
 <span data-ttu-id="c83b3-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換包含迴圈的數目超過上限的訊息結構描述所需的次數重複多次。</span><span class="sxs-lookup"><span data-stu-id="c83b3-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained a loop that repeated more times than the maximum number of times required by the message schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c83b3-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c83b3-117">User Action</span></span>  
 <span data-ttu-id="c83b3-118">若要解決這個錯誤，請確定迴圈重複的交換中不超過指定的訊息結構描述中迴圈 maxOccurs 屬性中的次數，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="c83b3-118">To resolve this error, make sure that the loop repeats in the interchange no more than the number of times in the maxOccurs property specified for the loop in the message schema, and then have the interchange resent.</span></span>