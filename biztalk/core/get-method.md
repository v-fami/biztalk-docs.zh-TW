---
title: "Get 方法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Get method
ms.assetid: 0e621077-f0ef-495c-ba6b-0c6154f48113
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d56b060cc261f707a4aa7b0d6a496a62707c4dca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-method"></a><span data-ttu-id="3996b-102">Get 方法</span><span class="sxs-lookup"><span data-stu-id="3996b-102">Get Method</span></span>
<span data-ttu-id="3996b-103">用來擷取屬性，根據輸入金鑰參數 (key1、 key2、...</span><span class="sxs-lookup"><span data-stu-id="3996b-103">Used to retrieve properties based on the input key parameters (key1, key2, …</span></span> <span data-ttu-id="3996b-104">...keyn)。</span><span class="sxs-lookup"><span data-stu-id="3996b-104">keyn).</span></span> <span data-ttu-id="3996b-105">輸出參數是一個結構，裡面包含符合索引鍵參數之記錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="3996b-105">The output parameter is a structure containing the properties of the record that matches the key parameters.</span></span> <span data-ttu-id="3996b-106">如果元件介面只有一個執行個體 （也就是沒有任何索引鍵），Get 函式不包含任何索引鍵參數。</span><span class="sxs-lookup"><span data-stu-id="3996b-106">If the component interface has only one instance (that is, there is no key), the Get function does not contain any key parameter.</span></span> <span data-ttu-id="3996b-107">另請參閱[Find 方法](../core/find-method.md)。</span><span class="sxs-lookup"><span data-stu-id="3996b-107">Also see [Find Method](../core/find-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3996b-108">語法</span><span class="sxs-lookup"><span data-stu-id="3996b-108">Syntax</span></span>  
  
```  
Get (key1, key2, ... keyn, properties)  
Get (key1, key2, ... keyn, getHistoryItems, properties)  
```  
  
## <a name="parameters"></a><span data-ttu-id="3996b-109">參數</span><span class="sxs-lookup"><span data-stu-id="3996b-109">Parameters</span></span>  
  
|<span data-ttu-id="3996b-110">參數</span><span class="sxs-lookup"><span data-stu-id="3996b-110">Parameter</span></span>|<span data-ttu-id="3996b-111">Description</span><span class="sxs-lookup"><span data-stu-id="3996b-111">Description</span></span>|  
|---------------|-----------------|  
|`key`|<span data-ttu-id="3996b-112">一組必須存在於伺服器資料庫中的參數；若不存在這些參數，將會出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="3996b-112">A set of parameters that must exist in the server database; otherwise an error occurs.</span></span> <span data-ttu-id="3996b-113">這些索引鍵對應至針對特定元件介面所定義的一組 Get 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="3996b-113">These keys correspond to the set of Get Keys as defined for the particular Component Interface.</span></span>|  
|`properties`|<span data-ttu-id="3996b-114">內含完整的元件介面屬性結構，完成呼叫時即會傳回這個結構。</span><span class="sxs-lookup"><span data-stu-id="3996b-114">Contains a complete structure of the component interface properties, which is returned upon completion of the call.</span></span>|  
|`getHistoryItems`|<span data-ttu-id="3996b-115">布林值。</span><span class="sxs-lookup"><span data-stu-id="3996b-115">A Boolean value.</span></span> <span data-ttu-id="3996b-116">如果元件介面的屬性包含層級低於 0 且帶有生效日期 (亦即，索引鍵欄位名稱為 EFFDT) 的項目，則需要額外的 `getHistoryItems` 參數。</span><span class="sxs-lookup"><span data-stu-id="3996b-116">If the properties of the component interface contain effective-dated items below level 0 (that is, a key field with a name of EFFDT) the `getHistoryItems` additional parameter is required.</span></span><br /><br /> <span data-ttu-id="3996b-117">如果值為：</span><span class="sxs-lookup"><span data-stu-id="3996b-117">If the value is:</span></span><br /><br /> <span data-ttu-id="3996b-118">-為 true，所有的生效日期項目會傳回做為序列 （它可以在任何層級內嵌）。</span><span class="sxs-lookup"><span data-stu-id="3996b-118">-   True—All effective dated items are returned as a sequence (which could be embedded in any level).</span></span> <span data-ttu-id="3996b-119">這些項目包括所有帶有過去、現在與未來生效日期的項目</span><span class="sxs-lookup"><span data-stu-id="3996b-119">These include all past effective dated items, the current effective dated item, as well as all future effective dated items</span></span><br /><span data-ttu-id="3996b-120">-False，會傳回的目前和所有未來生效日期項目。</span><span class="sxs-lookup"><span data-stu-id="3996b-120">-   False—Only the current and all future effective dated items are returned.</span></span> <span data-ttu-id="3996b-121">如果以後會在同一個執行個體上進行更新呼叫，則 `getHistoryItems` 應設為 False。</span><span class="sxs-lookup"><span data-stu-id="3996b-121">If subsequent calls to update on the same instance will be made, then `getHistoryItems` should be set to False.</span></span>|  
  
### <a name="remarks"></a><span data-ttu-id="3996b-122">備註</span><span class="sxs-lookup"><span data-stu-id="3996b-122">Remarks</span></span>  
 <span data-ttu-id="3996b-123">如果元件介面的屬性包含層級低於 0 且帶有生效日期 (亦即，索引鍵欄位名稱為 EFFDT) 的項目，則需要額外的 `getHistoryItems` 參數。</span><span class="sxs-lookup"><span data-stu-id="3996b-123">If the properties of the component interface contain effective dated items below level 0 (that is, a key field with a name of EFFDT), an additional parameter, `getHistoryItems`, is required.</span></span> <span data-ttu-id="3996b-124">此參數類型為布林值，</span><span class="sxs-lookup"><span data-stu-id="3996b-124">This parameter is of type Boolean.</span></span> <span data-ttu-id="3996b-125">而且一旦設為 True，即會傳回所有帶有生效日期的項目的序列 (可以以任何層級內嵌)。</span><span class="sxs-lookup"><span data-stu-id="3996b-125">If it is set to True, all effective dated items are returned as a sequence (which could be embedded in any level).</span></span> <span data-ttu-id="3996b-126">這些項目包括所有帶有過去、現在與未來生效日期的項目。</span><span class="sxs-lookup"><span data-stu-id="3996b-126">These include all past effective dated items, the current effective dated item, as well as all future effective dated items.</span></span> <span data-ttu-id="3996b-127">如果將 `getHistoryItems` 參數設為 False，則只會傳回所有帶有現在與未來生效日期的項目。</span><span class="sxs-lookup"><span data-stu-id="3996b-127">If the `getHistoryItems` parameter is set to False, only the current and all future effective dated items are returned.</span></span> <span data-ttu-id="3996b-128">如果以後會在同一個執行個體上進行更新呼叫，則 `getHistoryItems` 應設為 False。</span><span class="sxs-lookup"><span data-stu-id="3996b-128">If subsequent calls to update on the same instance are to be made, then `getHistoryItems` should be set to False.</span></span> <span data-ttu-id="3996b-129">另請參閱[UpdateEx 方法](../core/updateex-method.md)。</span><span class="sxs-lookup"><span data-stu-id="3996b-129">See also [UpdateEx Method](../core/updateex-method.md).</span></span>  
  
 <span data-ttu-id="3996b-130">如果元件介面沒有索引鍵 (就像只可存在一個執行個體一樣)，則 `Get()` 方法的形式如下：</span><span class="sxs-lookup"><span data-stu-id="3996b-130">If the component interface does not have a key, as in the case where only one instance can exist, then the `Get()` method has the form:</span></span>  
  
```  
Get(properties)  
```  
  
 <span data-ttu-id="3996b-131">如需帶有生效日期之項目的詳細資訊，請參閱 PeopleSoft Enterprise 文件。</span><span class="sxs-lookup"><span data-stu-id="3996b-131">For more information on effective dated items, see the PeopleSoft Enterprise documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3996b-132">只有在元件介面中有啟用 PeopleSoft `Get()` 函式時，才會提供 BizTalk Adapter for PeopleSoft Enterprise `Get` 方法。</span><span class="sxs-lookup"><span data-stu-id="3996b-132">The BizTalk Adapter for PeopleSoft Enterprise `Get()` method is provided if the PeopleSoft `Get` function in the component interface is enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3996b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3996b-133">See Also</span></span>  
 [<span data-ttu-id="3996b-134">附錄 a： 元件介面方法</span><span class="sxs-lookup"><span data-stu-id="3996b-134">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)