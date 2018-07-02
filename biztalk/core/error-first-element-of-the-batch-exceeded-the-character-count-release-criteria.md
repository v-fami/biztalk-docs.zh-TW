---
title: 批次的第一個項目已超過字元計數釋放準則集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4b06f8f-247d-4e93-8c4e-5e86e4ad70c9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 880e29ceb2be1c574aeaec248ce47317e332e5a6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972655"
---
# <a name="the-first-element-of-the-batch-exceeded-the-character-count-release-criteria-set"></a><span data-ttu-id="1be3d-102">批次的第一個項目已超過字元計數釋放準則集</span><span class="sxs-lookup"><span data-stu-id="1be3d-102">The first element of the batch exceeded the character count release criteria set</span></span>
## <a name="details"></a><span data-ttu-id="1be3d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1be3d-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="1be3d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1be3d-104">Product Name</span></span>   |                                                                                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                         |
| <span data-ttu-id="1be3d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1be3d-105">Product Version</span></span> |                                                                                                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                                     |
|    <span data-ttu-id="1be3d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1be3d-106">Event ID</span></span>     |                                                                                                                                 -                                                                                                                                  |
|  <span data-ttu-id="1be3d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="1be3d-107">Event Source</span></span>   |                                                                                       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1be3d-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="1be3d-108"> EDI</span></span>                                                                                       |
|    <span data-ttu-id="1be3d-109">元件</span><span class="sxs-lookup"><span data-stu-id="1be3d-109">Component</span></span>    |                                                                                                                          <span data-ttu-id="1be3d-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="1be3d-110">Batching Engine</span></span>                                                                                                                           |
|  <span data-ttu-id="1be3d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1be3d-111">Symbolic Name</span></span>  |                                                                                                                   <span data-ttu-id="1be3d-112">FirstElementExceededCharCount</span><span class="sxs-lookup"><span data-stu-id="1be3d-112">FirstElementExceededCharCount</span></span>                                                                                                                    |
|  <span data-ttu-id="1be3d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1be3d-113">Message Text</span></span>   | <span data-ttu-id="1be3d-114">批次的第一個項目已超過字元計數釋放準則集。</span><span class="sxs-lookup"><span data-stu-id="1be3d-114">The first element of the batch exceeded the character count release criteria set.</span></span> <span data-ttu-id="1be3d-115">請變更要能夠處理此訊息的字元計數釋放準則。</span><span class="sxs-lookup"><span data-stu-id="1be3d-115">Please change the character count release criteria to be able to process this message.</span></span> <span data-ttu-id="1be3d-116">訊息將會需要修改設定之後重新傳送至批次處理系統</span><span class="sxs-lookup"><span data-stu-id="1be3d-116">The message will need to be resent to the batching system after the settings are modified</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="1be3d-117">說明</span><span class="sxs-lookup"><span data-stu-id="1be3d-117">Explanation</span></span>  
 <span data-ttu-id="1be3d-118">這個錯誤/警告/資訊事件表示，批次處理協調流程無法產生批次的交換因為揀取批次處理協調流程的第一個批次項目中的字元數超過字元數屬性所指定 「 最大的交換中的字元數 」 的批次釋放準則。</span><span class="sxs-lookup"><span data-stu-id="1be3d-118">This Error/Warning/Information event indicates that the batching orchestration could not generate the batched interchange because the number of characters in the first batch element picked up by the batching orchestration exceeded the number of characters specified by the "Maximum number of characters in an interchange" property of the batch release criteria.</span></span> <span data-ttu-id="1be3d-119">請注意相較於最大值的字元數目不在信封中包含的字元數。</span><span class="sxs-lookup"><span data-stu-id="1be3d-119">Note that the number of characters compared to the maximum does not include the number of characters in the envelope.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1be3d-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1be3d-120">User Action</span></span>  
 <span data-ttu-id="1be3d-121">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="1be3d-121">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="1be3d-122">增加做為交換接收者的合作對象的交換批次建立設定 頁面中的 EDI 屬性 對話方塊中的 「 最大的交換中的字元數 」 屬性。</span><span class="sxs-lookup"><span data-stu-id="1be3d-122">Increase the "Maximum number of characters in an interchange" property in the Interchange Batch Creation Settings Page of the EDI Properties dialog box for the party as interchange receiver.</span></span> <span data-ttu-id="1be3d-123">若要這樣做，您必須先停止協調流程執行個體中，增加最大的在屬性中的字元數，然後重新啟動協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="1be3d-123">To do so, you must stop the orchestration instance, increase the maximum number of characters in the property, and then restart the orchestration instance.</span></span> <span data-ttu-id="1be3d-124">已重新傳送訊息的寄件者。</span><span class="sxs-lookup"><span data-stu-id="1be3d-124">Have the sender resend the message.</span></span>  
  
2.  <span data-ttu-id="1be3d-125">已傳送的交易集具有較少的字元，最大字元數比寄件者。</span><span class="sxs-lookup"><span data-stu-id="1be3d-125">Have the sender send transaction sets that have fewer characters than the maximum number of characters.</span></span>