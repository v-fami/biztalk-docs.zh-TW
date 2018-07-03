---
title: 包括的區段數目不符合 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c868de02-fda7-4d84-be50-2c08cde0450c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0d2b91ba8ddecfe4926cbc21834b239eedc4547
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009383"
---
# <a name="number-of-included-segments-do-not-match"></a><span data-ttu-id="25fe0-102">包含的區段數目不相符</span><span class="sxs-lookup"><span data-stu-id="25fe0-102">Number of included segments do not match</span></span>
## <a name="details"></a><span data-ttu-id="25fe0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="25fe0-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="25fe0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="25fe0-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="25fe0-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="25fe0-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="25fe0-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="25fe0-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="25fe0-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="25fe0-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="25fe0-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="25fe0-108"> EDI</span></span> |
|    <span data-ttu-id="25fe0-109">元件</span><span class="sxs-lookup"><span data-stu-id="25fe0-109">Component</span></span>    |                                       <span data-ttu-id="25fe0-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="25fe0-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="25fe0-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="25fe0-111">Symbolic Name</span></span>  |                        <span data-ttu-id="25fe0-112">X12TsIncludedSegCountMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="25fe0-112">X12TsIncludedSegCountMismatchDescription</span></span>                        |
|  <span data-ttu-id="25fe0-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="25fe0-113">Message Text</span></span>   |                        <span data-ttu-id="25fe0-114">包含的區段數目不相符</span><span class="sxs-lookup"><span data-stu-id="25fe0-114">Number of included segments do not match</span></span>                        |
  
## <a name="explanation"></a><span data-ttu-id="25fe0-115">說明</span><span class="sxs-lookup"><span data-stu-id="25fe0-115">Explanation</span></span>  
 <span data-ttu-id="25fe0-116">這個錯誤/警告/資訊事件表示 X12 交換的交易集的區段數目與交易集結尾 (SE01 欄位) 中的數目不相等。</span><span class="sxs-lookup"><span data-stu-id="25fe0-116">This Error/Warning/Information event indicates that the number of segments in the transaction set of the X12 interchange does not equal the number in the transaction set trailer (SE01 field).</span></span> <span data-ttu-id="25fe0-117">會發生這種情況時保留交換，並發生錯誤時暫停交換。</span><span class="sxs-lookup"><span data-stu-id="25fe0-117">This occurs when the interchange is preserved and the interchange is suspended on an error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="25fe0-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="25fe0-118">User Action</span></span>  
 <span data-ttu-id="25fe0-119">若要解決此錯誤，確定交換結尾的 SE01 欄位中的數目與交換集中的區段數目相同，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="25fe0-119">To resolve this error, make sure that the number in the SE01 field of the interchange trailer is the same as the number of segments in the transaction set, and then resend the interchange.</span></span>