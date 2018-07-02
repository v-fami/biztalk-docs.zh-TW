---
title: 序列化期間發生的錯誤。 X12 交易集包含在功能群組下列錯誤而擱置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49b13038-2637-4435-91e9-d6fe2b80ca7a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 745fee9f48d534b750b605268ce63b1c685e3231
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988935"
---
# <a name="error-encountered-during-serialization-the-x12-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a><span data-ttu-id="8072b-103">序列化期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8072b-103">Error encountered during serialization.</span></span> <span data-ttu-id="8072b-104">X12 交易集包含在功能群組下列錯誤而擱置</span><span class="sxs-lookup"><span data-stu-id="8072b-104">The X12 transaction set contained in functional group is being suspended with following errors</span></span>
## <a name="details"></a><span data-ttu-id="8072b-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8072b-105">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="8072b-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8072b-106">Product Name</span></span>   |                                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                             |
| <span data-ttu-id="8072b-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="8072b-107">Product Version</span></span> |                                                                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                         |
|    <span data-ttu-id="8072b-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8072b-108">Event ID</span></span>     |                                                                                                                     -                                                                                                                      |
|  <span data-ttu-id="8072b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="8072b-109">Event Source</span></span>   |                                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8072b-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="8072b-110"> EDI</span></span>                                                                           |
|    <span data-ttu-id="8072b-111">元件</span><span class="sxs-lookup"><span data-stu-id="8072b-111">Component</span></span>    |                                                                                                                 <span data-ttu-id="8072b-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="8072b-112">EDI Engine</span></span>                                                                                                                 |
|  <span data-ttu-id="8072b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8072b-113">Symbolic Name</span></span>  |                                                                                                         <span data-ttu-id="8072b-114">X12TransactionSetSendError</span><span class="sxs-lookup"><span data-stu-id="8072b-114">X12TransactionSetSendError</span></span>                                                                                                         |
|  <span data-ttu-id="8072b-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8072b-115">Message Text</span></span>   | <span data-ttu-id="8072b-116">序列化期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8072b-116">Error encountered during serialization.</span></span> <span data-ttu-id="8072b-117">X12 交易集識別碼為 '{0}'包含在功能群組識別碼'{1}'，在交換識別碼'{2}'，寄件者識別碼為 '{3}'，接收者識別碼'{4}' 而遭到擱置下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="8072b-117">The X12 transaction set with id '{0}' contained in functional group with id '{1}', in interchange with id '{2}', with sender id '{3}', receiver id '{4}' is being suspended with following errors:</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="8072b-118">說明</span><span class="sxs-lookup"><span data-stu-id="8072b-118">Explanation</span></span>  
 <span data-ttu-id="8072b-119">這個錯誤/警告/資訊事件表示 EDI 傳送管線時發生錯誤序列化 X12 外寄交換，因為識別的交易集與敘述的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8072b-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing X12 interchange because of the stated errors with the identified transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8072b-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8072b-120">User Action</span></span>  
 <span data-ttu-id="8072b-121">若要解決這個錯誤，錯誤訊息中使用的資訊來識別交易集合中的錯誤訊息，然後決定產品說明中的問題解決方法。</span><span class="sxs-lookup"><span data-stu-id="8072b-121">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the product help.</span></span>