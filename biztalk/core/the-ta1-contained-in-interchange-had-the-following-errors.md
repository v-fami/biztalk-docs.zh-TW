---
title: 包含在交換中的 TA1 發生下列錯誤 |Microsoft Docs
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
ms.openlocfilehash: 23bc06cd5f7a7b1e46b34daf5cac2106dcbd543a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002135"
---
# <a name="the-ta1-contained-in-interchange-had-the-following-errors"></a><span data-ttu-id="4ab7a-102">包含在交換中的 TA1 發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="4ab7a-102">The TA1 contained in interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="4ab7a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4ab7a-103">Details</span></span>  
  
|                 |                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="4ab7a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4ab7a-104">Product Name</span></span>   |                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                |
| <span data-ttu-id="4ab7a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="4ab7a-105">Product Version</span></span> |                            [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                            |
|    <span data-ttu-id="4ab7a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4ab7a-106">Event ID</span></span>     |                                                        -                                                         |
|  <span data-ttu-id="4ab7a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="4ab7a-107">Event Source</span></span>   |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4ab7a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="4ab7a-108"> EDI</span></span>              |
|    <span data-ttu-id="4ab7a-109">元件</span><span class="sxs-lookup"><span data-stu-id="4ab7a-109">Component</span></span>    |                                                    <span data-ttu-id="4ab7a-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="4ab7a-110">EDI Engine</span></span>                                                    |
|  <span data-ttu-id="4ab7a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4ab7a-111">Symbolic Name</span></span>  |                                                   <span data-ttu-id="4ab7a-112">X12TA1Error</span><span class="sxs-lookup"><span data-stu-id="4ab7a-112">X12TA1Error</span></span>                                                    |
|  <span data-ttu-id="4ab7a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4ab7a-113">Message Text</span></span>   | <span data-ttu-id="4ab7a-114">{0} TA1 包含在交換識別碼 '{1}'，寄件者識別碼'{2}'，接收者識別碼 '{3}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="4ab7a-114">The {0} TA1 contained in interchange with id '{1}', sender id '{2}', receiver id '{3}' had the following errors:</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="4ab7a-115">說明</span><span class="sxs-lookup"><span data-stu-id="4ab7a-115">Explanation</span></span>  
 <span data-ttu-id="4ab7a-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送的 TA1 通知因為指定的錯誤情況。</span><span class="sxs-lookup"><span data-stu-id="4ab7a-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming TA1 acknowledgment because of the indicated error condition.</span></span> <span data-ttu-id="4ab7a-117">這可能表示通知不符合 TA1Schema。</span><span class="sxs-lookup"><span data-stu-id="4ab7a-117">This may indicate that the acknowledgment does not conform to the TA1Schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4ab7a-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4ab7a-118">User Action</span></span>  
 <span data-ttu-id="4ab7a-119">若要解決這個錯誤，讓傳送者的通知解決的問題與通知，確保該通知會符合 TA1Schema，然後再重新傳送通知。</span><span class="sxs-lookup"><span data-stu-id="4ab7a-119">To resolve this error, have the sender of the acknowledgment resolve the issue with the acknowledgment, ensuring that the acknowledgment conforms to the TA1Schema, and then resend the acknowledgment.</span></span>