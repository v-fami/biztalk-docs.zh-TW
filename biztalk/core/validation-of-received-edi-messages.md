---
title: 驗證收到的 EDI 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c56a3c0-042e-4611-8131-d51098064f0f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dcc48b343332ea6b402841ec5ed1f5c9af49b2dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288054"
---
# <a name="validation-of-received-edi-messages"></a><span data-ttu-id="80e29-102">驗證已接收的 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="80e29-102">Validation of Received EDI Messages</span></span>
<span data-ttu-id="80e29-103">EDI 接收管線處理內送訊息時，會對信封和訊息資料執行一系列驗證。</span><span class="sxs-lookup"><span data-stu-id="80e29-103">When the EDI receive pipeline processes an incoming message, it performs a series of validations on the envelope and message data.</span></span> <span data-ttu-id="80e29-104">有些驗證處理是固定會執行的，而有些需經啟用才會執行。</span><span class="sxs-lookup"><span data-stu-id="80e29-104">Some of these processes are always performed; some are performed only if you enable them.</span></span> <span data-ttu-id="80e29-105">這些驗證包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="80e29-105">These validations include the following:</span></span>  
  
-   <span data-ttu-id="80e29-106">**一律會執行驗證都**:</span><span class="sxs-lookup"><span data-stu-id="80e29-106">**The validations that are always performed are**:</span></span>  
  
    -   <span data-ttu-id="80e29-107">驗證交換信封的結構。</span><span class="sxs-lookup"><span data-stu-id="80e29-107">Validation of the structure of the interchange envelope.</span></span>  
  
    -   <span data-ttu-id="80e29-108">根據交易夥伴協議 (若未定義協議，則根據後援協議) 對信封執行的驗證。</span><span class="sxs-lookup"><span data-stu-id="80e29-108">Validation of the envelope against trading partner agreement (or fallback agreement if no agreement is defined).</span></span>  
  
    -   <span data-ttu-id="80e29-109">對信封和控制結構描執行的結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="80e29-109">Schema validation of the envelope against the control schema.</span></span>  
  
    -   <span data-ttu-id="80e29-110">對交易集資料元素和訊息結構描述執行的結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="80e29-110">Schema validation of the transaction-set data elements against the message schema.</span></span>  
  
    -   <span data-ttu-id="80e29-111">根據 X12 標準所提供的「交易集-群組」對應，對單一群組內的交易集類型執行的驗證。</span><span class="sxs-lookup"><span data-stu-id="80e29-111">Validation of the types of transaction sets within a single group based on the transaction set -group mapping provided by X12 standards.</span></span>  
  
-   <span data-ttu-id="80e29-112">**啟用時，才會執行驗證都**:</span><span class="sxs-lookup"><span data-stu-id="80e29-112">**The validations that are performed only if enabled are**:</span></span>  
  
    -   <span data-ttu-id="80e29-113">對交易集資料項目執行的 EDI 驗證。</span><span class="sxs-lookup"><span data-stu-id="80e29-113">EDI validation performed on transaction-set data elements.</span></span> <span data-ttu-id="80e29-114">需在協議屬性中啟用才會執行。</span><span class="sxs-lookup"><span data-stu-id="80e29-114">This is performed if enabled in the agreement properties.</span></span>  
  
    -   <span data-ttu-id="80e29-115">對交易集資料元素執行的擴充驗證。</span><span class="sxs-lookup"><span data-stu-id="80e29-115">Extended validation performed on transaction-set data elements.</span></span> <span data-ttu-id="80e29-116">需在協議屬性中啟用才會執行。</span><span class="sxs-lookup"><span data-stu-id="80e29-116">This is performed if enabled in the agreement properties.</span></span>  
  
    -   <span data-ttu-id="80e29-117">交易集資料項目的欄位交互驗證 (僅限 X12 編碼訊息)。</span><span class="sxs-lookup"><span data-stu-id="80e29-117">Cross-field validation on transaction set data elements (X12-encoded messages only).</span></span> <span data-ttu-id="80e29-118">需在訊息結構描述中啟用才會執行。</span><span class="sxs-lookup"><span data-stu-id="80e29-118">This is performed if enabled in the message schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e29-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80e29-119">See Also</span></span>  
 <span data-ttu-id="80e29-120">[EDI 結構驗證](../core/edi-structural-validation.md) </span><span class="sxs-lookup"><span data-stu-id="80e29-120">[EDI Structural Validation](../core/edi-structural-validation.md) </span></span>  
 <span data-ttu-id="80e29-121">[協議屬性驗證](../core/agreement-properties-validation.md) </span><span class="sxs-lookup"><span data-stu-id="80e29-121">[Agreement Properties Validation](../core/agreement-properties-validation.md) </span></span>  
 <span data-ttu-id="80e29-122">[EDI 類型 （資料元素） 驗證](../core/edi-type-data-element-validation.md) </span><span class="sxs-lookup"><span data-stu-id="80e29-122">[EDI Type (Data Element) Validation](../core/edi-type-data-element-validation.md) </span></span>  
 <span data-ttu-id="80e29-123">[擴充 (BTS-XSD) 驗證](../core/extended-bts-xsd-validation.md) </span><span class="sxs-lookup"><span data-stu-id="80e29-123">[Extended (BTS-XSD) Validation](../core/extended-bts-xsd-validation.md) </span></span>  
 <span data-ttu-id="80e29-124">[結構描述驗證](../core/schema-validation2.md) </span><span class="sxs-lookup"><span data-stu-id="80e29-124">[Schema Validation](../core/schema-validation2.md) </span></span>  
 [<span data-ttu-id="80e29-125">交叉驗證欄位區段</span><span class="sxs-lookup"><span data-stu-id="80e29-125">Cross Field-Segment Validation</span></span>](../core/cross-field-segment-validation.md)