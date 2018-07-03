---
title: 區段不在定義的交易集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914e333f-96e4-4094-880d-51a5f25915c3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3db84f1ae6fda183799b0344d95da7b395aaee8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991695"
---
# <a name="segment-not-in-defined-transaction-set"></a><span data-ttu-id="62b28-102">區段不在定義的交易集中</span><span class="sxs-lookup"><span data-stu-id="62b28-102">Segment Not In Defined Transaction set</span></span>
## <a name="details"></a><span data-ttu-id="62b28-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="62b28-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="62b28-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="62b28-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="62b28-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="62b28-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="62b28-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="62b28-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="62b28-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="62b28-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="62b28-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="62b28-108"> EDI</span></span> |
|    <span data-ttu-id="62b28-109">元件</span><span class="sxs-lookup"><span data-stu-id="62b28-109">Component</span></span>    |                                       <span data-ttu-id="62b28-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="62b28-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="62b28-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="62b28-111">Symbolic Name</span></span>  |                          <span data-ttu-id="62b28-112">X12SegmentNotInDefinedTSDescription</span><span class="sxs-lookup"><span data-stu-id="62b28-112">X12SegmentNotInDefinedTSDescription</span></span>                           |
|  <span data-ttu-id="62b28-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="62b28-113">Message Text</span></span>   |                         <span data-ttu-id="62b28-114">區段不在定義的交易集中</span><span class="sxs-lookup"><span data-stu-id="62b28-114">Segment Not In Defined Transaction set</span></span>                         |
  
## <a name="explanation"></a><span data-ttu-id="62b28-115">說明</span><span class="sxs-lookup"><span data-stu-id="62b28-115">Explanation</span></span>  
 <span data-ttu-id="62b28-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換中該交換的交易集因為不包含文件結構描述所需的區段。</span><span class="sxs-lookup"><span data-stu-id="62b28-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because a transaction set in that interchange does not contain a segment required by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="62b28-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="62b28-117">User Action</span></span>  
 <span data-ttu-id="62b28-118">若要解決這個錯誤，有 寄件者的交換至交易集在交換中，新增必要的區段，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="62b28-118">To resolve this error, have the sender of the interchange add the required segment to the transaction set in the interchange, and then resend the interchange.</span></span>