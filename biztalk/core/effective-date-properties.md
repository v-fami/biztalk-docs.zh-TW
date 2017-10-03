---
title: "Effective Date 屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- effective-dated items
- getHistoryItems parameter
- Effective Date
- EFFDT
- planned items, scheduling and tracking
ms.assetid: 0d9a153c-7ea5-41cf-9e4e-055e1c18f64b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34f1c4cf3579a3381c846ddbb9896b2e5be26f6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="effective-date-properties"></a><span data-ttu-id="60bc5-102">Effective Date 屬性</span><span class="sxs-lookup"><span data-stu-id="60bc5-102">Effective Date Properties</span></span>
<span data-ttu-id="60bc5-103">PeopleSoft Enterprise 藉由名為 Effective Date (縮寫為 EFFDT) 的特殊屬性，讓您排定與追蹤計畫項目。</span><span class="sxs-lookup"><span data-stu-id="60bc5-103">PeopleSoft Enterprise provides the ability to schedule and keep track of planned items by using a special property called Effective Date (abbreviated EFFDT).</span></span> <span data-ttu-id="60bc5-104">這類項目可能已生效或是單純為計畫階段，端賴其日期比 PeopleSoft 目前日期早還是晚。</span><span class="sxs-lookup"><span data-stu-id="60bc5-104">Such items are either in effect or merely planned, depending on whether their date is before or after the PeopleSoft current date.</span></span>  
  
 <span data-ttu-id="60bc5-105">如果元件介面的屬性包含這類帶有生效日期 (亦即，欄位名稱為 EFFDT) 的項目，配接器會讓呼叫者能夠擷取整組值，或是僅擷取尚未生效 (而仍能變更) 的值。</span><span class="sxs-lookup"><span data-stu-id="60bc5-105">If the properties of a component interface contain such effective-dated items (that is, a field with a name of EFFDT), the adapter makes it possible for callers to retrieve the complete set of values or only those values not yet effective—those that can still be changed.</span></span>  
  
## <a name="gethistoryitems-parameter"></a><span data-ttu-id="60bc5-106">getHistoryItems 參數</span><span class="sxs-lookup"><span data-stu-id="60bc5-106">getHistoryItems Parameter</span></span>  
 <span data-ttu-id="60bc5-107">如果元件介面具有帶有生效日期的屬性，配接器會提供名為 `getHistoryItems` 的額外參數給 Get 運算。</span><span class="sxs-lookup"><span data-stu-id="60bc5-107">For component interfaces with properties that include an effective date, the adapter provides an additional parameter, called `getHistoryItems`, to the Get operations.</span></span> <span data-ttu-id="60bc5-108">此參數為布林值類型，而且一旦設為 True，就會傳回所有帶有生效日期的項目。</span><span class="sxs-lookup"><span data-stu-id="60bc5-108">This parameter is of type Boolean, and if it is set to True, all effective-dated items are returned.</span></span> <span data-ttu-id="60bc5-109">這些項目包括所有帶有過去、現在與未來生效日期的項目。</span><span class="sxs-lookup"><span data-stu-id="60bc5-109">These include all past, current, and future effective-dated items.</span></span>  
  
 <span data-ttu-id="60bc5-110">如果將 `getHistoryItems` 參數設為 False，則只會傳回帶有現在與未來生效日期的項目。</span><span class="sxs-lookup"><span data-stu-id="60bc5-110">If the `getHistoryItems` parameter is set to False, only the current and future effective-dated items are returned.</span></span> <span data-ttu-id="60bc5-111">如果您打算新增或變更這些項目 (因為過去項目已無法變更)，請選擇 False。</span><span class="sxs-lookup"><span data-stu-id="60bc5-111">Choose False if your intention is to add or change these items (because past items cannot be changed).</span></span>  
  
 <span data-ttu-id="60bc5-112">多個帶有生效日期的項目，其生效日期可能有相同的時候。</span><span class="sxs-lookup"><span data-stu-id="60bc5-112">It is also possible to have multiple effective-dated items having the same effective date.</span></span> <span data-ttu-id="60bc5-113">碰到這種情況時，則必須同時提供額外的 Effective Sequence (EFFSEQ) 屬性。</span><span class="sxs-lookup"><span data-stu-id="60bc5-113">In this situation, an additional property, Effective Sequence (EFFSEQ), must also be provided.</span></span> <span data-ttu-id="60bc5-114">EFFSEQ 的值必須是唯一的，以便和帶有相同生效日期的項目有所區隔。</span><span class="sxs-lookup"><span data-stu-id="60bc5-114">The values of the EFFSEQ must be unique to differentiate items with the same effective date.</span></span> <span data-ttu-id="60bc5-115">如需詳細資訊，請參閱 PeopleSoft 文件。</span><span class="sxs-lookup"><span data-stu-id="60bc5-115">See the PeopleSoft documentation for more information.</span></span>  
  
## <a name="modifying-past-effective-dated-items"></a><span data-ttu-id="60bc5-116">修改帶有過去生效日期的項目</span><span class="sxs-lookup"><span data-stu-id="60bc5-116">Modifying Past Effective-Dated Items</span></span>  
 <span data-ttu-id="60bc5-117">`correctionMode`引數中同時[UpdateEx](../core/updateex-method.md)和[DeleteOnly](../core/deleteonly-method.md)方法可讓您控制是否可以修改過去生效日期項目。</span><span class="sxs-lookup"><span data-stu-id="60bc5-117">The `correctionMode` argument in both the [UpdateEx](../core/updateex-method.md) and [DeleteOnly](../core/deleteonly-method.md) methods control whether past effective dated items can be modified.</span></span> <span data-ttu-id="60bc5-118">如果設為 true，則所有項目都可以修改。</span><span class="sxs-lookup"><span data-stu-id="60bc5-118">If it is set to true, all items can be modified.</span></span> <span data-ttu-id="60bc5-119">否則，修改帶有生效日期的過去項目會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="60bc5-119">Otherwise, modifying past effective dated item generates an exception.</span></span>  
  
 <span data-ttu-id="60bc5-120">在元件介面上呼叫 `Update` 方法 (此方法已不再使用)，而該元件介面具有帶有生效日期的項目時，請務必注意您所加入的生效日期值不得比 PeopleSoft 目前的生效日期還早，否則呼叫會失敗並傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="60bc5-120">When calling the deprecated `Update` method on a component interface that has effective-dated items, you must take care not to include any effective dates of a value earlier than the PeopleSoft current effective date, or the call fails with an exception.</span></span> <span data-ttu-id="60bc5-121">不過，您可以加入帶有目前生效日期的項目，這是因為設定屬性時會略過這類項目。</span><span class="sxs-lookup"><span data-stu-id="60bc5-121">However, the current effective-dated item can be included as it is bypassed when setting properties.</span></span> <span data-ttu-id="60bc5-122">如果 Effective Sequence 屬性存在，則設定屬性期間會略過伺服器中所有具有相符 Effective Sequences 的帶有目前生效日期的項目。</span><span class="sxs-lookup"><span data-stu-id="60bc5-122">If Effective Sequence exists, then all current effective-dated items with matching Effective Sequences in the server are skipped when setting properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60bc5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60bc5-123">See Also</span></span>  
 [<span data-ttu-id="60bc5-124">附錄 a： 元件介面方法</span><span class="sxs-lookup"><span data-stu-id="60bc5-124">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)