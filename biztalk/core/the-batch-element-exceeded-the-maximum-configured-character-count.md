---
title: 批次項目已超過設定的最大字元計數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ad12733-295a-43ba-8147-34c8716c2d37
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 689ba342affa3ed4f246e9aa963f8ea4e22704af
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992415"
---
# <a name="the-batch-element-exceeded-the-maximum-configured-character-count"></a><span data-ttu-id="60f2c-102">批次項目已超過設定的最大字元計數</span><span class="sxs-lookup"><span data-stu-id="60f2c-102">The batch element exceeded the maximum configured character count</span></span>
## <a name="details"></a><span data-ttu-id="60f2c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="60f2c-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="60f2c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="60f2c-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="60f2c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="60f2c-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="60f2c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="60f2c-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="60f2c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="60f2c-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="60f2c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="60f2c-108"> EDI</span></span> |
|    <span data-ttu-id="60f2c-109">元件</span><span class="sxs-lookup"><span data-stu-id="60f2c-109">Component</span></span>    |                                    <span data-ttu-id="60f2c-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="60f2c-110">Batching Engine</span></span>                                     |
|  <span data-ttu-id="60f2c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="60f2c-111">Symbolic Name</span></span>  |                             <span data-ttu-id="60f2c-112">MessageExceededCharacterCount</span><span class="sxs-lookup"><span data-stu-id="60f2c-112">MessageExceededCharacterCount</span></span>                              |
|  <span data-ttu-id="60f2c-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="60f2c-113">Message Text</span></span>   |           <span data-ttu-id="60f2c-114">批次項目已超過設定的最大字元計數</span><span class="sxs-lookup"><span data-stu-id="60f2c-114">The batch element exceeded the maximum configured character count</span></span>            |
  
## <a name="explanation"></a><span data-ttu-id="60f2c-115">說明</span><span class="sxs-lookup"><span data-stu-id="60f2c-115">Explanation</span></span>  
 <span data-ttu-id="60f2c-116">這個錯誤/警告/資訊事件表示，批次處理協調流程無法產生批次的交換因為的批次處理協調流程收取批次項目中的字元數超過指定的字元數目批次釋放準則的 「 最大的交換中的字元數 」 屬性。</span><span class="sxs-lookup"><span data-stu-id="60f2c-116">This Error/Warning/Information event indicates that the batching orchestration could not generate the batched interchange because the number of characters in a batch element picked up by the batching orchestration exceeds the number of characters specified by the "Maximum number of characters in an interchange" property of the batch release criteria.</span></span> <span data-ttu-id="60f2c-117">會產生此錯誤訊息的批次項目不會挑選要批次，但是批次元素已批次處理的第一個元素之後的第一個批次元素。</span><span class="sxs-lookup"><span data-stu-id="60f2c-117">The batch element that generates this error message will not be the first batch element picked up for a batch, but a batch element after the first element has already been batched.</span></span> <span data-ttu-id="60f2c-118">請注意相較於最大值的字元數目不在信封中包含的字元數。</span><span class="sxs-lookup"><span data-stu-id="60f2c-118">Note that the number of characters compared to the maximum does not include the number of characters in the envelope.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="60f2c-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="60f2c-119">User Action</span></span>  
 <span data-ttu-id="60f2c-120">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="60f2c-120">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="60f2c-121">增加做為交換接收者的合作對象的交換批次建立設定 頁面中的 EDI 屬性 對話方塊中的 「 最大的交換中的字元數 」 屬性。</span><span class="sxs-lookup"><span data-stu-id="60f2c-121">Increase the "Maximum number of characters in an interchange" property in the Interchange Batch Creation Settings Page of the EDI Properties dialog box for the party as interchange receiver.</span></span> <span data-ttu-id="60f2c-122">若要這樣做，您必須先停止協調流程執行個體中，增加最大的在屬性中的字元數，然後重新啟動協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="60f2c-122">To do so, you must stop the orchestration instance, increase the maximum number of characters in the property, and then restart the orchestration instance.</span></span>  
  
2.  <span data-ttu-id="60f2c-123">已傳送的交易集具有較少的字元，最大字元數比寄件者。</span><span class="sxs-lookup"><span data-stu-id="60f2c-123">Have the sender send transaction sets that have fewer characters than the maximum number of characters.</span></span>