---
title: Find 方法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Find method
ms.assetid: 676827a6-82af-4922-bf9e-aca5bd23624b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a5432c68c36dcf8e769351af6d57f3cd3ed712b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245966"
---
# <a name="find-method"></a><span data-ttu-id="26da1-102">Find 方法</span><span class="sxs-lookup"><span data-stu-id="26da1-102">Find Method</span></span>
<span data-ttu-id="26da1-103">用來傳回滿足提供的部分搜尋索引鍵的索引鍵清單。</span><span class="sxs-lookup"><span data-stu-id="26da1-103">Used to return a list of keys that satisfy the supplied partial search keys.</span></span> <span data-ttu-id="26da1-104">請注意，對於只有一個執行個體的元件介面 (即沒有索引鍵)，則不會產生 `Find()` 函數。</span><span class="sxs-lookup"><span data-stu-id="26da1-104">Note that for a component interface that has only one instance, that is, there is no key, the `Find()` function is not generated.</span></span> <span data-ttu-id="26da1-105">另請參閱[Get 方法](../core/get-method.md)。</span><span class="sxs-lookup"><span data-stu-id="26da1-105">See also [Get Method](../core/get-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26da1-106">語法</span><span class="sxs-lookup"><span data-stu-id="26da1-106">Syntax</span></span>  
  
```  
Find (partialKey, keyList)  
```  
  
## <a name="parameters"></a><span data-ttu-id="26da1-107">參數</span><span class="sxs-lookup"><span data-stu-id="26da1-107">Parameters</span></span>  
  
|<span data-ttu-id="26da1-108">參數</span><span class="sxs-lookup"><span data-stu-id="26da1-108">Parameter</span></span>|<span data-ttu-id="26da1-109">Description</span><span class="sxs-lookup"><span data-stu-id="26da1-109">Description</span></span>|  
|---------------|-----------------|  
|`partialKey`|<span data-ttu-id="26da1-110">一種結構，其中個別的索引鍵是選擇性的</span><span class="sxs-lookup"><span data-stu-id="26da1-110">A structure where the individual keys are optional.</span></span>|  
|`keyList`|<span data-ttu-id="26da1-111">符合 `partialKey` 的索引鍵清單。</span><span class="sxs-lookup"><span data-stu-id="26da1-111">A list of keys that matches the `partialKey`.</span></span> <span data-ttu-id="26da1-112">這是輸出參數。</span><span class="sxs-lookup"><span data-stu-id="26da1-112">It is an output parameter.</span></span><br /><br /> <span data-ttu-id="26da1-113">與為特定的元件介面定義的「尋找索引鍵」集合對應的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="26da1-113">The keys correspond to the set of Find Keys as defined for the particular component interface.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26da1-114">備註</span><span class="sxs-lookup"><span data-stu-id="26da1-114">Remarks</span></span>  
 <span data-ttu-id="26da1-115">當您指定部分索引鍵時，可以使用 PeopleSoft 內部的 `Find()` 函數所提供相同的萬用字元搜尋。</span><span class="sxs-lookup"><span data-stu-id="26da1-115">When you specify the partial keys, it is possible to use the same wildcard search available from the PeopleSoft internal `Find()` function.</span></span> <span data-ttu-id="26da1-116">例如，"11" 的部分 ACCOUNT 索引鍵會傳回開頭為 "11" 的所有 ACCOUNT 索引鍵，而 "%40" 則會傳回索引鍵中的任何部分包含 "40" 的所有 ACCOUNT 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="26da1-116">For example, the partial ACCOUNT key of "11" returns all ACCOUNT keys that start with "11", whereas "%40" returns all ACCOUNT keys that contain "40" anywhere within the key.</span></span> <span data-ttu-id="26da1-117">部分索引鍵 "_4_4" 會傳回第二個和第四個位置中含有字元 "4" 的所有 ACCOUNT 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="26da1-117">A partial key "_4_4" returns all ACCOUNT keys with the character "4" in the 2nd and 4th positions.</span></span>  
  
 <span data-ttu-id="26da1-118">注意： 與目前的 PeopleSoft Server 實作，超過 300 個項目符合搜尋條件，如果呼叫失敗。</span><span class="sxs-lookup"><span data-stu-id="26da1-118">Note: With the current implementation of the PeopleSoft Server, if more than 300 items match the search criteria, the call fails.</span></span> <span data-ttu-id="26da1-119">這是 PeopleSoft Server 的限制。</span><span class="sxs-lookup"><span data-stu-id="26da1-119">This is a restriction of the PeopleSoft server.</span></span> <span data-ttu-id="26da1-120">如果在元件介面中啟用 PeopleSoft `Find()` 函數，並且可以使用 Get 索引鍵，就提供 Microsoft BizTalk Adapter for PeopleSoft Enterprise `Find` 方法。</span><span class="sxs-lookup"><span data-stu-id="26da1-120">The Microsoft BizTalk Adapter for PeopleSoft Enterprise `Find()` method is provided if the PeopleSoft `Find` function in the component interface is enabled and Get keys are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26da1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26da1-121">See Also</span></span>  
 [<span data-ttu-id="26da1-122">附錄 a： 元件介面方法</span><span class="sxs-lookup"><span data-stu-id="26da1-122">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)