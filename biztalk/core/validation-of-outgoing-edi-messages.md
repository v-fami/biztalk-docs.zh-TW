---
title: 驗證外寄 EDI 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 491303c0-b585-409e-a289-a2f6f9f82469
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 946e90eb58c9b81e0cd7fa9bf2c02cc49af021ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287990"
---
# <a name="validation-of-outgoing-edi-messages"></a><span data-ttu-id="f6fc0-102">驗證外寄 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="f6fc0-102">Validation of Outgoing EDI Messages</span></span>
<span data-ttu-id="f6fc0-103">EDI 傳送管線處理外寄訊息時，會對信封和訊息資料執行一系列驗證。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-103">When the EDI send pipeline processes a message to be sent, it performs a series of validations on the envelope and message data.</span></span> <span data-ttu-id="f6fc0-104">有些驗證處理是固定會執行的，而有些需經啟用才會執行。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-104">Some of these processes are always performed; some are performed only if you enable them.</span></span> <span data-ttu-id="f6fc0-105">這些驗證包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="f6fc0-105">These validations include the following:</span></span>  
  
-   <span data-ttu-id="f6fc0-106">對交易集資料元素和訊息結構描述執行的結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-106">Schema validation of the transaction-set data elements against the message schema.</span></span> <span data-ttu-id="f6fc0-107">此項目固定會執行。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-107">This is always performed.</span></span>  
  
-   <span data-ttu-id="f6fc0-108">交易集資料項目的欄位交互驗證 (僅限 X12 編碼訊息)。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-108">Cross-field validation on transaction set data elements (X12-encoded messages only).</span></span> <span data-ttu-id="f6fc0-109">需在訊息結構描述中啟用才會執行。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-109">This is performed if it is enabled in the message schema.</span></span>  
  
-   <span data-ttu-id="f6fc0-110">對交易集資料項目執行的 EDI 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-110">EDI validation performed on transaction-set data elements.</span></span> <span data-ttu-id="f6fc0-111">需在協議屬性中啟用才會執行。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-111">This is performed if enabled in agreement properties.</span></span>  
  
-   <span data-ttu-id="f6fc0-112">對交易集資料元素執行的擴充驗證。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-112">Extended validation performed on transaction-set data elements.</span></span> <span data-ttu-id="f6fc0-113">需在協議屬性中啟用才會執行。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-113">This is performed if enabled in agreement properties.</span></span>  
  
-   <span data-ttu-id="f6fc0-114">依據 X12 標準，驗證單一群組 (以交易集 – 群組對應為基礎) 中的交易集。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-114">Validation of the transaction sets within a single group based on the transaction set – group mapping, according to X12 standards.</span></span> <span data-ttu-id="f6fc0-115">這執行時，才**輸入批次處理選項**屬性設定為**保留交換-發生錯誤時暫停交換**或**保留交換-暫止交易設定錯誤**。</span><span class="sxs-lookup"><span data-stu-id="f6fc0-115">This is performed only when the **Inbound batch processing option** property is set to **Preserve Interchange - suspend Interchange on Error** or **Preserve Interchange - suspend Transaction Sets on Error**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6fc0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6fc0-116">See Also</span></span>  
 <span data-ttu-id="f6fc0-117">[EDI 結構驗證](../core/edi-structural-validation.md) </span><span class="sxs-lookup"><span data-stu-id="f6fc0-117">[EDI Structural Validation](../core/edi-structural-validation.md) </span></span>  
 <span data-ttu-id="f6fc0-118">[協議屬性驗證](../core/agreement-properties-validation.md) </span><span class="sxs-lookup"><span data-stu-id="f6fc0-118">[Agreement Properties Validation](../core/agreement-properties-validation.md) </span></span>  
 <span data-ttu-id="f6fc0-119">[EDI 類型 （資料元素） 驗證](../core/edi-type-data-element-validation.md) </span><span class="sxs-lookup"><span data-stu-id="f6fc0-119">[EDI Type (Data Element) Validation](../core/edi-type-data-element-validation.md) </span></span>  
 <span data-ttu-id="f6fc0-120">[擴充 (BTS-XSD) 驗證](../core/extended-bts-xsd-validation.md) </span><span class="sxs-lookup"><span data-stu-id="f6fc0-120">[Extended (BTS-XSD) Validation](../core/extended-bts-xsd-validation.md) </span></span>  
 <span data-ttu-id="f6fc0-121">[結構描述驗證](../core/schema-validation2.md) </span><span class="sxs-lookup"><span data-stu-id="f6fc0-121">[Schema Validation](../core/schema-validation2.md) </span></span>  
 [<span data-ttu-id="f6fc0-122">交叉驗證欄位區段</span><span class="sxs-lookup"><span data-stu-id="f6fc0-122">Cross Field-Segment Validation</span></span>](../core/cross-field-segment-validation.md)