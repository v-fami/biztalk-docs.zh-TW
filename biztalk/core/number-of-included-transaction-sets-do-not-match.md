---
title: 包含的交易集數目不符合 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db958803-4667-4558-81a6-70c62d6fe8bf
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93d2f51abc20f9cb790d2e6df62443f428c03dc8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970103"
---
# <a name="number-of-included-transaction-sets-do-not-match"></a><span data-ttu-id="73063-102">包含的交易集數目不相符</span><span class="sxs-lookup"><span data-stu-id="73063-102">Number of included transaction sets do not match</span></span>
## <a name="details"></a><span data-ttu-id="73063-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="73063-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="73063-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="73063-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="73063-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="73063-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="73063-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="73063-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="73063-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="73063-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="73063-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="73063-108"> EDI</span></span> |
|    <span data-ttu-id="73063-109">元件</span><span class="sxs-lookup"><span data-stu-id="73063-109">Component</span></span>    |                                       <span data-ttu-id="73063-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="73063-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="73063-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="73063-111">Symbolic Name</span></span>  |                           <span data-ttu-id="73063-112">X12FaNumberOfTsMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="73063-112">X12FaNumberOfTsMismatchDescription</span></span>                           |
|  <span data-ttu-id="73063-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="73063-113">Message Text</span></span>   |                    <span data-ttu-id="73063-114">包含的交易集數目不相符</span><span class="sxs-lookup"><span data-stu-id="73063-114">Number of included transaction sets do not match</span></span>                    |
  
## <a name="explanation"></a><span data-ttu-id="73063-115">說明</span><span class="sxs-lookup"><span data-stu-id="73063-115">Explanation</span></span>  
 <span data-ttu-id="73063-116">這個錯誤/警告/資訊事件表示交易的數目設定群組中的 x12 交換不等於群組結尾 （GE01 欄位） 中的數字。</span><span class="sxs-lookup"><span data-stu-id="73063-116">This Error/Warning/Information event indicates that the number of transaction sets in the group of the X12 interchange does not equal the number in the group trailer (GE01 field).</span></span> <span data-ttu-id="73063-117">會發生這種情況時保留交換，並發生錯誤時暫停交換。</span><span class="sxs-lookup"><span data-stu-id="73063-117">This occurs when the interchange is preserved and the interchange is suspended on an error.</span></span> <span data-ttu-id="73063-118">（錯誤訊息是不會張貼如果保留交換，且會暫停交易集發生錯誤時，或者如果在交換分割。）</span><span class="sxs-lookup"><span data-stu-id="73063-118">(The error message is not posted if the interchange is preserved and the transaction sets are suspended on an error, or if the interchange is split.)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="73063-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="73063-119">User Action</span></span>  
 <span data-ttu-id="73063-120">若要解決此錯誤，確定群組結尾之 GE01 欄位中的數目與交換之群組中的交易集數目相同，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="73063-120">To resolve this error, make sure that the number in the GE01 field of the group trailer is the same as the number of transaction sets in the group of the interchange, and then resend the interchange.</span></span>