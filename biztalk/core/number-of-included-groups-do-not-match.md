---
title: 包含群組數目不符合 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d61ac17-92cd-4a5e-81e6-e2c6fc4085bb
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf61012de6ba864d6f0ff4e553b4c74e1d501c20
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988167"
---
# <a name="number-of-included-groups-do-not-match"></a><span data-ttu-id="a87ea-102">包括的群組數目不相符</span><span class="sxs-lookup"><span data-stu-id="a87ea-102">Number of included groups do not match</span></span>
## <a name="details"></a><span data-ttu-id="a87ea-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a87ea-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="a87ea-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a87ea-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="a87ea-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a87ea-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="a87ea-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a87ea-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="a87ea-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="a87ea-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a87ea-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a87ea-108"> EDI</span></span> |
|    <span data-ttu-id="a87ea-109">元件</span><span class="sxs-lookup"><span data-stu-id="a87ea-109">Component</span></span>    |                                       <span data-ttu-id="a87ea-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="a87ea-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="a87ea-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a87ea-111">Symbolic Name</span></span>  |                     <span data-ttu-id="a87ea-112">X12Ta1InvalidNumberOfIncludedGroupsDescription</span><span class="sxs-lookup"><span data-stu-id="a87ea-112">X12Ta1InvalidNumberOfIncludedGroupsDescription</span></span>                     |
|  <span data-ttu-id="a87ea-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a87ea-113">Message Text</span></span>   |                         <span data-ttu-id="a87ea-114">包括的群組數目不相符</span><span class="sxs-lookup"><span data-stu-id="a87ea-114">Number Of included groups do not match</span></span>                         |
  
## <a name="explanation"></a><span data-ttu-id="a87ea-115">說明</span><span class="sxs-lookup"><span data-stu-id="a87ea-115">Explanation</span></span>  
 <span data-ttu-id="a87ea-116">這個錯誤/警告/資訊事件表示交換中的群組數目不等於交換結尾 （IEA01 欄位） 中的數字。</span><span class="sxs-lookup"><span data-stu-id="a87ea-116">This Error/Warning/Information event indicates that the number of groups in the interchange does not equal the number in the interchange trailer (IEA01 field).</span></span> <span data-ttu-id="a87ea-117">會發生這種情況時保留交換，並發生錯誤時暫停交換。</span><span class="sxs-lookup"><span data-stu-id="a87ea-117">This occurs when the interchange is preserved and the interchange is suspended on an error.</span></span> <span data-ttu-id="a87ea-118">（錯誤訊息是不會張貼如果保留交換，且會暫停交易集發生錯誤時，或者如果在交換分割。）</span><span class="sxs-lookup"><span data-stu-id="a87ea-118">(The error message is not posted if the interchange is preserved and the transaction sets are suspended on an error, or if the interchange is split.)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a87ea-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a87ea-119">User Action</span></span>  
 <span data-ttu-id="a87ea-120">若要解決這個錯誤，確定交換結尾 IEA01 欄位中的號碼是在交換中，群組數目相同，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="a87ea-120">To resolve this error, make sure that the number in the IEA01 field of the interchange trailer is the same as the number of groups in the interchange, and then resend the interchange.</span></span>