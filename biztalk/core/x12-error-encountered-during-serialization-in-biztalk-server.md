---
title: 序列化期間發生的錯誤。 X12 功能群組發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dad987c3-92f3-4a6b-ba1a-b60f6ea2fbe4
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b972993026822aa66b2863a3409e35f0a1b3f434
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009615"
---
# <a name="error-encountered-during-serialization-the-x12-functional-group-had-the-following-errors"></a><span data-ttu-id="10e53-103">序列化期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="10e53-103">Error encountered during serialization.</span></span> <span data-ttu-id="10e53-104">X12 功能群組發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="10e53-104">The X12 functional group had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="10e53-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="10e53-105">Details</span></span>  
  
|                 |                                                                                                                                                                                 |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="10e53-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="10e53-106">Product Name</span></span>   |                                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                |
| <span data-ttu-id="10e53-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="10e53-107">Product Version</span></span> |                                                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                            |
|    <span data-ttu-id="10e53-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="10e53-108">Event ID</span></span>     |                                                                                        -                                                                                        |
|  <span data-ttu-id="10e53-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="10e53-109">Event Source</span></span>   |                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="10e53-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="10e53-110"> EDI</span></span>                                              |
|    <span data-ttu-id="10e53-111">元件</span><span class="sxs-lookup"><span data-stu-id="10e53-111">Component</span></span>    |                                                                                   <span data-ttu-id="10e53-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="10e53-112">EDI Engine</span></span>                                                                                    |
|  <span data-ttu-id="10e53-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="10e53-113">Symbolic Name</span></span>  |                                                                           <span data-ttu-id="10e53-114">X12FunctionalGroupSendError</span><span class="sxs-lookup"><span data-stu-id="10e53-114">X12FunctionalGroupSendError</span></span>                                                                           |
|  <span data-ttu-id="10e53-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="10e53-115">Message Text</span></span>   | <span data-ttu-id="10e53-116">序列化期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="10e53-116">Error encountered during serialization.</span></span> <span data-ttu-id="10e53-117">X12 功能群組識別碼 '{0}'，在交換識別碼'{1}'，寄件者識別碼為 '{2}'，接收者識別碼'{3}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="10e53-117">The X12 functional group with id '{0}', in interchange with id '{1}', with sender id '{2}', receiver id '{3}' had the following errors:</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="10e53-118">說明</span><span class="sxs-lookup"><span data-stu-id="10e53-118">Explanation</span></span>  
 <span data-ttu-id="10e53-119">這個錯誤/警告/資訊事件表示 EDI 傳送管線時發生錯誤序列化 X12 外寄交換，因為識別的功能群組所述的錯誤。</span><span class="sxs-lookup"><span data-stu-id="10e53-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing X12 interchange because of the stated errors with the identified functional group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="10e53-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="10e53-120">User Action</span></span>  
 <span data-ttu-id="10e53-121">若要解決這個錯誤，錯誤訊息中使用的資訊來識別功能群組中的錯誤訊息，然後決定產品說明中的問題解決方法。</span><span class="sxs-lookup"><span data-stu-id="10e53-121">To resolve this error, use the information in the error message to identify the error in the functional group and then determine the problem resolution in the product help.</span></span>