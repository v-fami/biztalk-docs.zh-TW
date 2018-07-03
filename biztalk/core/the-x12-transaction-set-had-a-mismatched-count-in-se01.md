---
title: X12 交易集在 SE01 中有不相符的計數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a90079f5-5939-40b6-9756-d7943240c125
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 947a557a81c6857b5d31f447acb2ec5a46cfcef9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993343"
---
# <a name="the-x12-transaction-set-had-a-mismatched-count-in-se01"></a><span data-ttu-id="51638-102">X12 交易集在 SE01 中有不相符的計數</span><span class="sxs-lookup"><span data-stu-id="51638-102">The X12 Transaction set had a mismatched count in SE01</span></span>
## <a name="details"></a><span data-ttu-id="51638-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="51638-103">Details</span></span>  
  
|                 |                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="51638-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="51638-104">Product Name</span></span>   |                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                       |
| <span data-ttu-id="51638-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="51638-105">Product Version</span></span> |                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                   |
|    <span data-ttu-id="51638-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="51638-106">Event ID</span></span>     |                                                               -                                                               |
|  <span data-ttu-id="51638-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="51638-107">Event Source</span></span>   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="51638-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="51638-108"> EDI</span></span>                     |
|    <span data-ttu-id="51638-109">元件</span><span class="sxs-lookup"><span data-stu-id="51638-109">Component</span></span>    |                                                          <span data-ttu-id="51638-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="51638-110">EDI Engine</span></span>                                                           |
|  <span data-ttu-id="51638-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="51638-111">Symbolic Name</span></span>  |                                                     <span data-ttu-id="51638-112">X12StSeCountMismatch</span><span class="sxs-lookup"><span data-stu-id="51638-112">X12StSeCountMismatch</span></span>                                                      |
|  <span data-ttu-id="51638-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="51638-113">Message Text</span></span>   | <span data-ttu-id="51638-114">X12 交易集在 SE01 中有不相符的計數。</span><span class="sxs-lookup"><span data-stu-id="51638-114">The X12 Transaction set had a mismatched count in SE01.</span></span> <span data-ttu-id="51638-115">SE01 已{0}，但它應該是{1}。</span><span class="sxs-lookup"><span data-stu-id="51638-115">SE01 was {0}, whereas it should have been {1}.</span></span> <span data-ttu-id="51638-116">已更正。</span><span class="sxs-lookup"><span data-stu-id="51638-116">It has been corrected.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="51638-117">說明</span><span class="sxs-lookup"><span data-stu-id="51638-117">Explanation</span></span>  
 <span data-ttu-id="51638-118">這則警告表示交易集結尾 （SE01 欄位） 中的數字，不符合交換的交易集中的區段數目。</span><span class="sxs-lookup"><span data-stu-id="51638-118">This Warning indicates that the number in the transaction set trailer (SE01 field) did not match the number of segments in the transaction set of the interchange.</span></span> <span data-ttu-id="51638-119">傳送管線會更正 SE01 欄位中的計數，並將張貼警告。</span><span class="sxs-lookup"><span data-stu-id="51638-119">The send pipeline corrects the count in the SE01 field and posts the warning.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="51638-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="51638-120">User Action</span></span>  
 <span data-ttu-id="51638-121">不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="51638-121">No action is necessary.</span></span>