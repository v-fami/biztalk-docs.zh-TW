---
title: TA1 交換中包含發生下列錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2d63fe9-63ef-44b3-8cb9-45a7abf8d0e4
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03bd7486d25e2c94fc809e6dc50c43359c152b70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278630"
---
# <a name="the-ta1-contained-in-interchange-had-the-following-errors"></a><span data-ttu-id="083ce-102">TA1 交換中包含發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="083ce-102">The TA1 contained in interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="083ce-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="083ce-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="083ce-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="083ce-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="083ce-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="083ce-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="083ce-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="083ce-106">Event ID</span></span>|-|  
|<span data-ttu-id="083ce-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="083ce-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="083ce-108">EDI</span><span class="sxs-lookup"><span data-stu-id="083ce-108"> EDI</span></span>|  
|<span data-ttu-id="083ce-109">元件</span><span class="sxs-lookup"><span data-stu-id="083ce-109">Component</span></span>|<span data-ttu-id="083ce-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="083ce-110">EDI Engine</span></span>|  
|<span data-ttu-id="083ce-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="083ce-111">Symbolic Name</span></span>|<span data-ttu-id="083ce-112">X12TA1Error</span><span class="sxs-lookup"><span data-stu-id="083ce-112">X12TA1Error</span></span>|  
|<span data-ttu-id="083ce-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="083ce-113">Message Text</span></span>|<span data-ttu-id="083ce-114">在識別碼為 '{1}'，寄件者 id '{2}' 交換中包含 {0} TA1、 接收者識別碼 '{3}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="083ce-114">The {0} TA1 contained in interchange with id '{1}', sender id '{2}', receiver id '{3}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="083ce-115">說明</span><span class="sxs-lookup"><span data-stu-id="083ce-115">Explanation</span></span>  
 <span data-ttu-id="083ce-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送的 TA1 通知發生指出的錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="083ce-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming TA1 acknowledgment because of the indicated error condition.</span></span> <span data-ttu-id="083ce-117">這可能表示通知不符合 TA1Schema。</span><span class="sxs-lookup"><span data-stu-id="083ce-117">This may indicate that the acknowledgment does not conform to the TA1Schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="083ce-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="083ce-118">User Action</span></span>  
 <span data-ttu-id="083ce-119">若要解決這個錯誤，讓傳送者的通知解決問題的通知，確保該通知符合 TA1Schema，然後再重新傳送通知。</span><span class="sxs-lookup"><span data-stu-id="083ce-119">To resolve this error, have the sender of the acknowledgment resolve the issue with the acknowledgment, ensuring that the acknowledgment conforms to the TA1Schema, and then resend the acknowledgment.</span></span>