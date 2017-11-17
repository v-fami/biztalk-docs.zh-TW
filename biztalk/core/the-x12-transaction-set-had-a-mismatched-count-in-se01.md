---
title: "X12 交易集 SE01 中有不相符的計數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90079f5-5939-40b6-9756-d7943240c125
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41539f0492f90d3f7276b0d80af28c568593ef4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-x12-transaction-set-had-a-mismatched-count-in-se01"></a><span data-ttu-id="3cd3d-102">X12 交易集 SE01 中有不相符的計數</span><span class="sxs-lookup"><span data-stu-id="3cd3d-102">The X12 Transaction set had a mismatched count in SE01</span></span>
## <a name="details"></a><span data-ttu-id="3cd3d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3cd3d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3cd3d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3cd3d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3cd3d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3cd3d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3cd3d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3cd3d-106">Event ID</span></span>|-|  
|<span data-ttu-id="3cd3d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="3cd3d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3cd3d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="3cd3d-108"> EDI</span></span>|  
|<span data-ttu-id="3cd3d-109">元件</span><span class="sxs-lookup"><span data-stu-id="3cd3d-109">Component</span></span>|<span data-ttu-id="3cd3d-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="3cd3d-110">EDI Engine</span></span>|  
|<span data-ttu-id="3cd3d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3cd3d-111">Symbolic Name</span></span>|<span data-ttu-id="3cd3d-112">X12StSeCountMismatch</span><span class="sxs-lookup"><span data-stu-id="3cd3d-112">X12StSeCountMismatch</span></span>|  
|<span data-ttu-id="3cd3d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3cd3d-113">Message Text</span></span>|<span data-ttu-id="3cd3d-114">X12 交易集 SE01 中有不相符的計數。</span><span class="sxs-lookup"><span data-stu-id="3cd3d-114">The X12 Transaction set had a mismatched count in SE01.</span></span> <span data-ttu-id="3cd3d-115">SE01 為 {0}，而它應該已被 {1}。</span><span class="sxs-lookup"><span data-stu-id="3cd3d-115">SE01 was {0}, whereas it should have been {1}.</span></span> <span data-ttu-id="3cd3d-116">已更正。</span><span class="sxs-lookup"><span data-stu-id="3cd3d-116">It has been corrected.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3cd3d-117">說明</span><span class="sxs-lookup"><span data-stu-id="3cd3d-117">Explanation</span></span>  
 <span data-ttu-id="3cd3d-118">這個警告表示交易集結尾 （SE01 欄位） 中的數字，不符合交換的交易集中的區段數目。</span><span class="sxs-lookup"><span data-stu-id="3cd3d-118">This Warning indicates that the number in the transaction set trailer (SE01 field) did not match the number of segments in the transaction set of the interchange.</span></span> <span data-ttu-id="3cd3d-119">傳送管線會更正 SE01 欄位中的計數，而且將公佈警告。</span><span class="sxs-lookup"><span data-stu-id="3cd3d-119">The send pipeline corrects the count in the SE01 field and posts the warning.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3cd3d-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3cd3d-120">User Action</span></span>  
 <span data-ttu-id="3cd3d-121">不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="3cd3d-121">No action is necessary.</span></span>