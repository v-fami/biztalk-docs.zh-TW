---
title: 日期和時間運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2e2d49f5-1aaf-4e4d-8da1-e8605304dccb
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5224c409a6d705806cccc493009ce2c32062f0a1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010663"
---
# <a name="date-and-time-functoids"></a><span data-ttu-id="26aa7-102">日期和時間運算質</span><span class="sxs-lookup"><span data-stu-id="26aa7-102">Date and Time Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="26aa7-103">概觀</span><span class="sxs-lookup"><span data-stu-id="26aa7-103">Overview</span></span>
<span data-ttu-id="26aa7-104">**日期 / 時間**運算質可分為兩類。</span><span class="sxs-lookup"><span data-stu-id="26aa7-104">**Date / Time** functoids can be divided into two categories.</span></span> <span data-ttu-id="26aa7-105">第一個類別包含單一運算質**加上天數**，用來將指定的天數新增至指定的日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="26aa7-105">The first category contains a single functoid, **Add Days**, which is used to add a specified number of days to a specified date and time value.</span></span> <span data-ttu-id="26aa7-106">在輸出執行個體訊息未來應該會加入預估日期和時間時，這類運算質相當有用。</span><span class="sxs-lookup"><span data-stu-id="26aa7-106">This can be useful when a field in the output instance message is supposed to include a date and time estimate in the future.</span></span> <span data-ttu-id="26aa7-107">例如，**加上天數**運算質可以用來產生估計出貨日期，根據從收到訂單日期的固定的差異。</span><span class="sxs-lookup"><span data-stu-id="26aa7-107">For example, the **Add Days** functoid can be used to generate an estimated shipping date based a fixed delta from the date that an order was received.</span></span>  

 <span data-ttu-id="26aa7-108">第二個類別包含所有中的其餘運算質**日期和時間**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="26aa7-108">The second category includes all of the remaining functoids in the **Date and Time** category.</span></span> <span data-ttu-id="26aa7-109">它們可提供時間戳記在執行階段，以便可以在輸出執行個體訊息中包含的日期和時間在哪一個訊息執行轉換。</span><span class="sxs-lookup"><span data-stu-id="26aa7-109">They are used to provide a timestamp at run time, so that the date and time at which message transformation is being performed can be included in the output instance message.</span></span>  

 <span data-ttu-id="26aa7-110">**加上天數**運算質接受兩個輸入參數，而**日期**，**日期和時間**，以及**時間**運算質有沒有輸入參數。</span><span class="sxs-lookup"><span data-stu-id="26aa7-110">The **Add Days** functoid accepts two input parameters, whereas the **Date**, **Date and Time**, and **Time** functoids have no input parameters.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="26aa7-111">可用的運算質</span><span class="sxs-lookup"><span data-stu-id="26aa7-111">Available functoids</span></span>  
 <span data-ttu-id="26aa7-112">**日期 / 時間**運算質為：</span><span class="sxs-lookup"><span data-stu-id="26aa7-112">The **Date / Time** functoids are:</span></span> 

* <span data-ttu-id="26aa7-113">加上天數</span><span class="sxs-lookup"><span data-stu-id="26aa7-113">Add Days</span></span>
* <span data-ttu-id="26aa7-114">date</span><span class="sxs-lookup"><span data-stu-id="26aa7-114">Date</span></span>
* <span data-ttu-id="26aa7-115">日期及時間</span><span class="sxs-lookup"><span data-stu-id="26aa7-115">Date and Time</span></span>
* <span data-ttu-id="26aa7-116">Time</span><span class="sxs-lookup"><span data-stu-id="26aa7-116">Time</span></span>

<span data-ttu-id="26aa7-117">更多有關這些運算質可**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="26aa7-117">More details on these functoids are available **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="26aa7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26aa7-118">See Also</span></span>  
- [<span data-ttu-id="26aa7-119">如何新增基本運算質至對應</span><span class="sxs-lookup"><span data-stu-id="26aa7-119">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
- <span data-ttu-id="26aa7-120">**日期和時間運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="26aa7-120">**Date and Time Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
