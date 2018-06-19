---
title: 包含的交易集數目不相符 |Microsoft 文件
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
ms.openlocfilehash: 16a28544757c3e9ae75dd7230673c4526fc2c8f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263158"
---
# <a name="number-of-included-transaction-sets-do-not-match"></a><span data-ttu-id="73439-102">包含的交易集數目不相符</span><span class="sxs-lookup"><span data-stu-id="73439-102">Number of included transaction sets do not match</span></span>
## <a name="details"></a><span data-ttu-id="73439-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="73439-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73439-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="73439-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="73439-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="73439-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="73439-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="73439-106">Event ID</span></span>|-|  
|<span data-ttu-id="73439-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="73439-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="73439-108">EDI</span><span class="sxs-lookup"><span data-stu-id="73439-108"> EDI</span></span>|  
|<span data-ttu-id="73439-109">元件</span><span class="sxs-lookup"><span data-stu-id="73439-109">Component</span></span>|<span data-ttu-id="73439-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="73439-110">EDI Engine</span></span>|  
|<span data-ttu-id="73439-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="73439-111">Symbolic Name</span></span>|<span data-ttu-id="73439-112">X12FaNumberOfTsMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="73439-112">X12FaNumberOfTsMismatchDescription</span></span>|  
|<span data-ttu-id="73439-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="73439-113">Message Text</span></span>|<span data-ttu-id="73439-114">包含的交易集數目不相符</span><span class="sxs-lookup"><span data-stu-id="73439-114">Number of included transaction sets do not match</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="73439-115">說明</span><span class="sxs-lookup"><span data-stu-id="73439-115">Explanation</span></span>  
 <span data-ttu-id="73439-116">這個錯誤/警告/資訊事件表示交易的數目設定群組中的 x12 交換不等於群組結尾 （GE01 欄位） 中的數字。</span><span class="sxs-lookup"><span data-stu-id="73439-116">This Error/Warning/Information event indicates that the number of transaction sets in the group of the X12 interchange does not equal the number in the group trailer (GE01 field).</span></span> <span data-ttu-id="73439-117">會發生這種情況時保留交換，並發生錯誤時暫停交換。</span><span class="sxs-lookup"><span data-stu-id="73439-117">This occurs when the interchange is preserved and the interchange is suspended on an error.</span></span> <span data-ttu-id="73439-118">（錯誤訊息不張貼如果保留交換和交易集發生錯誤時，就會暫停，或是在交換分割。）</span><span class="sxs-lookup"><span data-stu-id="73439-118">(The error message is not posted if the interchange is preserved and the transaction sets are suspended on an error, or if the interchange is split.)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="73439-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="73439-119">User Action</span></span>  
 <span data-ttu-id="73439-120">若要解決此錯誤，確定群組結尾之 GE01 欄位中的數目與交換之群組中的交易集數目相同，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="73439-120">To resolve this error, make sure that the number in the GE01 field of the group trailer is the same as the number of transaction sets in the group of the interchange, and then resend the interchange.</span></span>