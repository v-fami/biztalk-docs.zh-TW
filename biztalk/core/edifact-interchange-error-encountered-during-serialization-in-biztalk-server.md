---
title: 序列化期間發生的錯誤。 Edifact 交換發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc933ac-161a-41e5-b67d-9f15e569d5c9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb97be1be3c623673d2429a20598c748a8d73de7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000823"
---
# <a name="error-encountered-during-serialization-the-edifact-interchange-had-the-following-errors"></a><span data-ttu-id="0331b-103">序列化期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0331b-103">Error encountered during serialization.</span></span> <span data-ttu-id="0331b-104">Edifact 交換發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="0331b-104">The Edifact interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="0331b-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0331b-105">Details</span></span>  
  
|                 |                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="0331b-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0331b-106">Product Name</span></span>   |                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                |
| <span data-ttu-id="0331b-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="0331b-107">Product Version</span></span> |                                            [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                            |
|    <span data-ttu-id="0331b-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0331b-108">Event ID</span></span>     |                                                                        -                                                                         |
|  <span data-ttu-id="0331b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="0331b-109">Event Source</span></span>   |                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0331b-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="0331b-110"> EDI</span></span>                              |
|    <span data-ttu-id="0331b-111">元件</span><span class="sxs-lookup"><span data-stu-id="0331b-111">Component</span></span>    |                                                                    <span data-ttu-id="0331b-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="0331b-112">EDI Engine</span></span>                                                                    |
|  <span data-ttu-id="0331b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0331b-113">Symbolic Name</span></span>  |                                                            <span data-ttu-id="0331b-114">EfactInterchangeSendError</span><span class="sxs-lookup"><span data-stu-id="0331b-114">EfactInterchangeSendError</span></span>                                                             |
|  <span data-ttu-id="0331b-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0331b-115">Message Text</span></span>   | <span data-ttu-id="0331b-116">序列化期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0331b-116">Error encountered during serialization.</span></span> <span data-ttu-id="0331b-117">Edifact 交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="0331b-117">The Edifact interchange with id '{0}', with sender id '{1}', receiver id '{2}' had the following errors:</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="0331b-118">說明</span><span class="sxs-lookup"><span data-stu-id="0331b-118">Explanation</span></span>  
 <span data-ttu-id="0331b-119">這個錯誤/警告/資訊事件表示 EDI 傳送管線在序列化傳出的 EDIFACT 交換因為識別的交換所述的錯誤時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0331b-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing EDIFACT interchange because of the stated errors with the identified interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0331b-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0331b-120">User Action</span></span>  
 <span data-ttu-id="0331b-121">若要解決這個錯誤，找出交換中的錯誤訊息，並接著決定產品說明中的問題解決方法需要使用錯誤訊息中的資訊。</span><span class="sxs-lookup"><span data-stu-id="0331b-121">To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.</span></span>