---
title: 序列化期間發生的錯誤。 X12 交換發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9ca3314-6c66-4400-816a-f9c7c7915122
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96c1a186e56fb5c04364187784522f0ba5832581
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008135"
---
# <a name="error-encountered-during-serialization-the-x12-interchange-had-the-following-errors"></a><span data-ttu-id="6d462-103">序列化期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d462-103">Error encountered during serialization.</span></span> <span data-ttu-id="6d462-104">X12 交換發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="6d462-104">The X12 interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="6d462-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6d462-105">Details</span></span>  
  
|                 |                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="6d462-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6d462-106">Product Name</span></span>   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                              |
| <span data-ttu-id="6d462-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="6d462-107">Product Version</span></span> |                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                          |
|    <span data-ttu-id="6d462-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6d462-108">Event ID</span></span>     |                                                                      -                                                                      |
|  <span data-ttu-id="6d462-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="6d462-109">Event Source</span></span>   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6d462-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="6d462-110"> EDI</span></span>                            |
|    <span data-ttu-id="6d462-111">元件</span><span class="sxs-lookup"><span data-stu-id="6d462-111">Component</span></span>    |                                                                 <span data-ttu-id="6d462-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="6d462-112">EDI Engine</span></span>                                                                  |
|  <span data-ttu-id="6d462-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6d462-113">Symbolic Name</span></span>  |                                                           <span data-ttu-id="6d462-114">X12InterchangeSendError</span><span class="sxs-lookup"><span data-stu-id="6d462-114">X12InterchangeSendError</span></span>                                                           |
|  <span data-ttu-id="6d462-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6d462-115">Message Text</span></span>   | <span data-ttu-id="6d462-116">序列化期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d462-116">Error encountered during serialization.</span></span> <span data-ttu-id="6d462-117">X12 交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="6d462-117">The X12 interchange with id '{0}', with sender id '{1}', receiver id '{2}' had the following errors</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="6d462-118">說明</span><span class="sxs-lookup"><span data-stu-id="6d462-118">Explanation</span></span>  
 <span data-ttu-id="6d462-119">這個錯誤/警告/資訊事件表示 EDI 傳送管線時發生錯誤序列化 X12 外寄交換，因為敘述的錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d462-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing X12 interchange because of the stated errors.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6d462-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6d462-120">User Action</span></span>  
 <span data-ttu-id="6d462-121">若要解決這個錯誤，找出交換中的錯誤訊息，並接著決定產品說明中的問題解決方法需要使用錯誤訊息中的資訊。</span><span class="sxs-lookup"><span data-stu-id="6d462-121">To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.</span></span>