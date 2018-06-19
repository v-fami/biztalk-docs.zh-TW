---
title: 批次項目已超過設定的最大字元數 |Microsoft 文件
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
ms.openlocfilehash: dac259db250a88e434efb649a2baf2e75b805a40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278342"
---
# <a name="the-batch-element-exceeded-the-maximum-configured-character-count"></a><span data-ttu-id="76473-102">批次項目已超過設定的最大字元數</span><span class="sxs-lookup"><span data-stu-id="76473-102">The batch element exceeded the maximum configured character count</span></span>
## <a name="details"></a><span data-ttu-id="76473-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="76473-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76473-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="76473-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="76473-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="76473-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="76473-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="76473-106">Event ID</span></span>|-|  
|<span data-ttu-id="76473-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="76473-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="76473-108">EDI</span><span class="sxs-lookup"><span data-stu-id="76473-108"> EDI</span></span>|  
|<span data-ttu-id="76473-109">元件</span><span class="sxs-lookup"><span data-stu-id="76473-109">Component</span></span>|<span data-ttu-id="76473-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="76473-110">Batching Engine</span></span>|  
|<span data-ttu-id="76473-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="76473-111">Symbolic Name</span></span>|<span data-ttu-id="76473-112">MessageExceededCharacterCount</span><span class="sxs-lookup"><span data-stu-id="76473-112">MessageExceededCharacterCount</span></span>|  
|<span data-ttu-id="76473-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="76473-113">Message Text</span></span>|<span data-ttu-id="76473-114">批次項目已超過設定的最大字元數</span><span class="sxs-lookup"><span data-stu-id="76473-114">The batch element exceeded the maximum configured character count</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="76473-115">說明</span><span class="sxs-lookup"><span data-stu-id="76473-115">Explanation</span></span>  
 <span data-ttu-id="76473-116">這個錯誤/警告/資訊事件表示，批次處理協調流程無法產生批次的交換因為批次處理協調流程收取批次項目中的字元數超過所指定的字元數批次釋放準則 「 最大的交換中的字元數 」 屬性。</span><span class="sxs-lookup"><span data-stu-id="76473-116">This Error/Warning/Information event indicates that the batching orchestration could not generate the batched interchange because the number of characters in a batch element picked up by the batching orchestration exceeds the number of characters specified by the "Maximum number of characters in an interchange" property of the batch release criteria.</span></span> <span data-ttu-id="76473-117">會產生此錯誤訊息的批次項目不會挑選要批次，但是批次元素之後的第一個元素已經批次處理的第一個批次元素。</span><span class="sxs-lookup"><span data-stu-id="76473-117">The batch element that generates this error message will not be the first batch element picked up for a batch, but a batch element after the first element has already been batched.</span></span> <span data-ttu-id="76473-118">請注意相較於最大值的字元數不在信封中包含的字元數。</span><span class="sxs-lookup"><span data-stu-id="76473-118">Note that the number of characters compared to the maximum does not include the number of characters in the envelope.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="76473-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="76473-119">User Action</span></span>  
 <span data-ttu-id="76473-120">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="76473-120">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="76473-121">增加做為交換接收者的合作對象的交換批次建立設定 頁面的 EDI 屬性 對話方塊中的 「 最大的交換中的字元數 」 屬性。</span><span class="sxs-lookup"><span data-stu-id="76473-121">Increase the "Maximum number of characters in an interchange" property in the Interchange Batch Creation Settings Page of the EDI Properties dialog box for the party as interchange receiver.</span></span> <span data-ttu-id="76473-122">若要這樣做，您必須停止協調流程執行個體中，增加的屬性中的字元數上限，然後重新啟動協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="76473-122">To do so, you must stop the orchestration instance, increase the maximum number of characters in the property, and then restart the orchestration instance.</span></span>  
  
2.  <span data-ttu-id="76473-123">需要寄件者傳送具有字元少於最大字元數的交易集。</span><span class="sxs-lookup"><span data-stu-id="76473-123">Have the sender send transaction sets that have fewer characters than the maximum number of characters.</span></span>