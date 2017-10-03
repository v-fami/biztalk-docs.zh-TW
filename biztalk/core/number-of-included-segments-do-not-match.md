---
title: "包括的區段數目不相符 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c868de02-fda7-4d84-be50-2c08cde0450c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01878c11c8464968b31a7f34ff75b5b494309f90
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="number-of-included-segments-do-not-match"></a><span data-ttu-id="3acd2-102">包含的區段數目不相符</span><span class="sxs-lookup"><span data-stu-id="3acd2-102">Number of included segments do not match</span></span>
## <a name="details"></a><span data-ttu-id="3acd2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3acd2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3acd2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3acd2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3acd2-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3acd2-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3acd2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3acd2-106">Event ID</span></span>|-|  
|<span data-ttu-id="3acd2-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="3acd2-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3acd2-108">EDI</span><span class="sxs-lookup"><span data-stu-id="3acd2-108"> EDI</span></span>|  
|<span data-ttu-id="3acd2-109">元件</span><span class="sxs-lookup"><span data-stu-id="3acd2-109">Component</span></span>|<span data-ttu-id="3acd2-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="3acd2-110">EDI Engine</span></span>|  
|<span data-ttu-id="3acd2-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3acd2-111">Symbolic Name</span></span>|<span data-ttu-id="3acd2-112">X12TsIncludedSegCountMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="3acd2-112">X12TsIncludedSegCountMismatchDescription</span></span>|  
|<span data-ttu-id="3acd2-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3acd2-113">Message Text</span></span>|<span data-ttu-id="3acd2-114">包含的區段數目不相符</span><span class="sxs-lookup"><span data-stu-id="3acd2-114">Number of included segments do not match</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3acd2-115">說明</span><span class="sxs-lookup"><span data-stu-id="3acd2-115">Explanation</span></span>  
 <span data-ttu-id="3acd2-116">這個錯誤/警告/資訊事件表示 X12 交換的交易集的區段數目與交易集結尾 (SE01 欄位) 中的數目不相等。</span><span class="sxs-lookup"><span data-stu-id="3acd2-116">This Error/Warning/Information event indicates that the number of segments in the transaction set of the X12 interchange does not equal the number in the transaction set trailer (SE01 field).</span></span> <span data-ttu-id="3acd2-117">會發生這種情況時保留交換，並發生錯誤時暫停交換。</span><span class="sxs-lookup"><span data-stu-id="3acd2-117">This occurs when the interchange is preserved and the interchange is suspended on an error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3acd2-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3acd2-118">User Action</span></span>  
 <span data-ttu-id="3acd2-119">若要解決此錯誤，確定交換結尾的 SE01 欄位中的數目與交換集中的區段數目相同，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="3acd2-119">To resolve this error, make sure that the number in the SE01 field of the interchange trailer is the same as the number of segments in the transaction set, and then resend the interchange.</span></span>