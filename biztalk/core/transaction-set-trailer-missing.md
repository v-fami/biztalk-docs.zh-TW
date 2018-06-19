---
title: 交易集結尾遺失 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07753300-fe47-47a6-a947-6abec10c1c90
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7f1c153aa0bb62b6c62f4eeebf9d1fb9bea004b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279286"
---
# <a name="transaction-set-trailer-missing"></a><span data-ttu-id="6daf1-102">交易集結尾遺失</span><span class="sxs-lookup"><span data-stu-id="6daf1-102">Transaction Set Trailer Missing</span></span>
## <a name="details"></a><span data-ttu-id="6daf1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6daf1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6daf1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6daf1-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6daf1-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="6daf1-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="6daf1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6daf1-106">Event ID</span></span>|-|  
|<span data-ttu-id="6daf1-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="6daf1-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6daf1-108">EDI</span><span class="sxs-lookup"><span data-stu-id="6daf1-108"> EDI</span></span>|  
|<span data-ttu-id="6daf1-109">元件</span><span class="sxs-lookup"><span data-stu-id="6daf1-109">Component</span></span>|<span data-ttu-id="6daf1-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="6daf1-110">EDI Engine</span></span>|  
|<span data-ttu-id="6daf1-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6daf1-111">Symbolic Name</span></span>|<span data-ttu-id="6daf1-112">X12TsTrailerMissingDescription</span><span class="sxs-lookup"><span data-stu-id="6daf1-112">X12TsTrailerMissingDescription</span></span>|  
|<span data-ttu-id="6daf1-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6daf1-113">Message Text</span></span>|<span data-ttu-id="6daf1-114">交易集結尾遺失</span><span class="sxs-lookup"><span data-stu-id="6daf1-114">Transaction Set Trailer Missing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6daf1-115">說明</span><span class="sxs-lookup"><span data-stu-id="6daf1-115">Explanation</span></span>  
 <span data-ttu-id="6daf1-116">這個錯誤/警告/資訊事件表示，由於交易集不含 SE 交易集結尾 (針對 X12 交易集) 或 UNT 訊息結尾 (針對 EDIFACT 交易集)，因此接收管線無法處理內送交易集，亦或是傳送管線無法處理外寄交易集。</span><span class="sxs-lookup"><span data-stu-id="6daf1-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming transaction set or the send pipeline could not process the outgoing transaction set because the transaction set did not include the SE transaction set trailer (for X12 transaction sets) or the UNT message trailer (for EDIFACT transaction sets).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6daf1-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6daf1-117">User Action</span></span>  
 <span data-ttu-id="6daf1-118">若要解決這個錯誤，有交易集合寄件者新增至交易集 SE 交易集結尾 (x12 交易集) 或 UNT 訊息結尾 （針對 EDIFACT 交易集），然後再重新傳送交易集。</span><span class="sxs-lookup"><span data-stu-id="6daf1-118">To resolve this error, have the sender of the transaction set add to the transaction set an SE transaction set trailer (for X12 transaction sets) or the UNT message trailer (for EDIFACT transaction sets), and then resend the transaction set.</span></span>