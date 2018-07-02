---
title: DeleteOnly 方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DeleteOnly method
ms.assetid: 99e1d7af-1450-439b-882f-de677e593bee
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42366a273fd65348daa9364a39c57c3fec3dff90
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983447"
---
# <a name="deleteonly-method"></a><span data-ttu-id="15bc5-102">DeleteOnly 方法</span><span class="sxs-lookup"><span data-stu-id="15bc5-102">DeleteOnly Method</span></span>
<span data-ttu-id="15bc5-103">可讓您刪除集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="15bc5-103">Allows you to delete items in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15bc5-104">語法</span><span class="sxs-lookup"><span data-stu-id="15bc5-104">Syntax</span></span>  
  
```  
DeleteOnly(key1, key2, ..., keyn, correctionMode, interactiveMode,  
    properties)  
```  
  
## <a name="parameters"></a><span data-ttu-id="15bc5-105">參數</span><span class="sxs-lookup"><span data-stu-id="15bc5-105">Parameters</span></span>  
  
|<span data-ttu-id="15bc5-106">參數</span><span class="sxs-lookup"><span data-stu-id="15bc5-106">Parameter</span></span>|<span data-ttu-id="15bc5-107">描述</span><span class="sxs-lookup"><span data-stu-id="15bc5-107">Description</span></span>|  
|---------------|-----------------|  
|`key`|<span data-ttu-id="15bc5-108">是一組必須提供的參數。</span><span class="sxs-lookup"><span data-stu-id="15bc5-108">Is a set of parameters that must be supplied.</span></span> <span data-ttu-id="15bc5-109">這組索引鍵必須存在於伺服器資料庫中，否則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="15bc5-109">This set of keys must exist in the server database, or an error occurs.</span></span> <span data-ttu-id="15bc5-110">這些金鑰對應至 Get Keys 集合，如為特定元件介面所定義：</span><span class="sxs-lookup"><span data-stu-id="15bc5-110">These keys correspond to the set of Get Keys as defined for the particular component interface.</span></span>|  
|`correctionMode`|<span data-ttu-id="15bc5-111">一個布林值旗標。</span><span class="sxs-lookup"><span data-stu-id="15bc5-111">A Boolean flag.</span></span> <span data-ttu-id="15bc5-112">若 設定為 True，則允許刪除集合中帶有過去有效日期的項目 。</span><span class="sxs-lookup"><span data-stu-id="15bc5-112">When set to true, allows deletion of past effective-dated items in a collection.</span></span> <span data-ttu-id="15bc5-113">特別是，允許刪除其 EFFDT 在目前有效日期前的項目。</span><span class="sxs-lookup"><span data-stu-id="15bc5-113">Specifically, it allows the deletion of items that have EFFDT prior to the current effective date.</span></span> <span data-ttu-id="15bc5-114">此旗標若未設定為 TRUE，對這些項目所做的任何修改都會導致 PeopleSoft 伺服器傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="15bc5-114">Without this flag set to TRUE, any modification to these items results in an error returned from PeopleSoft server.</span></span> <span data-ttu-id="15bc5-115">**注意︰** `correctionMode`引數只公開包含生效日期項目的那些元件介面。</span><span class="sxs-lookup"><span data-stu-id="15bc5-115">**Note:**  The `correctionMode` argument is only exposed for those component interfaces that contain effective-dated items.</span></span> <span data-ttu-id="15bc5-116">否則，該引數不會顯示為引數的一部分。</span><span class="sxs-lookup"><span data-stu-id="15bc5-116">Otherwise it is not shown as part of the argument.</span></span>|  
|`interactiveMode`|<span data-ttu-id="15bc5-117">用於錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="15bc5-117">Used for error handling.</span></span><br /><br /> <span data-ttu-id="15bc5-118">在存取元件介面中的屬性時，BizTalk Adapter for PeopleSoft Enterprise 會使用 PeopleSoft 提供的 API，這些 API 會讀取及寫入元件介面中的個別欄位；但這些變更並不會逐一傳播至 PeopleSoft 伺服器。</span><span class="sxs-lookup"><span data-stu-id="15bc5-118">When accessing properties in a component interface, the BizTalk Adapter for PeopleSoft Enterprise uses PeopleSoft-provided APIs, which read and write individual fields in the component interface; however, these changes are not propagated to the PeopleSoft server one at a time.</span></span> <span data-ttu-id="15bc5-119">psjoa.jar (BizTalk Adapter for PeopleSoft Enterprise 的互動對象) 會先封裝所有變更，再以這個單一封裝將變更傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="15bc5-119">Instead, the psjoa.jar (with which the BizTalk Adapter for PeopleSoft Enterprise interacts) packages all the changes and sends the changes to the server in one package.</span></span> <span data-ttu-id="15bc5-120">如果有任何個別的更新失敗，將會傳回一般錯誤，而不會指出實際錯誤。</span><span class="sxs-lookup"><span data-stu-id="15bc5-120">If any of the individual updates fail, a generic error is returned, which does not pinpoint the actual error.</span></span> <span data-ttu-id="15bc5-121">在互動模式設為 TRUE 的情況下，每個欄位更新都會個別傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="15bc5-121">With the interactive mode set to TRUE, every field update is sent to the server individually.</span></span> <span data-ttu-id="15bc5-122">雖然這對效能會有相當程度的影響，但卻能在更新失敗時 (例如用以設定欄位的值無效時) 提供具體的錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="15bc5-122">This has a substantial impact on performance, but it does provide specific error information if the update fails (for example, if an invalid value is used for setting a field).</span></span><br /><br /> <span data-ttu-id="15bc5-123">`interactiveMode` 參數可提供最大效能，並可提供欄位更新層級的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="15bc5-123">The `interactiveMode` parameter provides maximum performance and provides error reporting at the field-update level.</span></span> <span data-ttu-id="15bc5-124">若要適當使用此功能，建議您平常進行呼叫時，將 `interactiveMode` 設為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="15bc5-124">To use this feature properly, it is recommended that you make normal calls with `interactiveMode` set to FALSE.</span></span> <span data-ttu-id="15bc5-125">這樣效能應該不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="15bc5-125">There should be no impact on performance.</span></span> <span data-ttu-id="15bc5-126">如果傳回錯誤，您可以將 interactiveMode 旗標設為 TRUE，再重試相同的呼叫。</span><span class="sxs-lookup"><span data-stu-id="15bc5-126">If an error is returned, the same call can be retried with the interactiveMode flag set to TRUE.</span></span> <span data-ttu-id="15bc5-127">當呼叫失敗時，伺服器會傳回更精確的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="15bc5-127">When the call fails, the server returns a more precise error message.</span></span>|  
|`properties`|<span data-ttu-id="15bc5-128">包含伺服器上現有結構的子集。</span><span class="sxs-lookup"><span data-stu-id="15bc5-128">Contains a subset of the structure that exists on the server.</span></span> <span data-ttu-id="15bc5-129">所有 分葉項目都會被刪除 。</span><span class="sxs-lookup"><span data-stu-id="15bc5-129">All items that are leaves are deleted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15bc5-130">備註</span><span class="sxs-lookup"><span data-stu-id="15bc5-130">Remarks</span></span>  
 <span data-ttu-id="15bc5-131">屬性具有與此元件介面的 `CreateEx` 或 `UpdateEx` 方法相同的資料型別，但是，只有索引鍵值比較重要。</span><span class="sxs-lookup"><span data-stu-id="15bc5-131">The properties have the same data type as the `CreateEx` or `UpdateEx` methods of this component interface; however, only the key values are important.</span></span> <span data-ttu-id="15bc5-132">會忽略 非索引鍵值 。</span><span class="sxs-lookup"><span data-stu-id="15bc5-132">The non-key values are ignored.</span></span> <span data-ttu-id="15bc5-133">這些 索引鍵值必須符合伺服器上的索引鍵值，否則會引發例外狀況 。</span><span class="sxs-lookup"><span data-stu-id="15bc5-133">The key values must match those on the server, otherwise an exception is raised.</span></span>  
  
 <span data-ttu-id="15bc5-134">以下示範索引鍵值的使用方式。</span><span class="sxs-lookup"><span data-stu-id="15bc5-134">The following demonstrates the use of the key values.</span></span> <span data-ttu-id="15bc5-135">如果集合包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="15bc5-135">If a collection contains the items:</span></span>  
  
- <span data-ttu-id="15bc5-136">item0</span><span class="sxs-lookup"><span data-stu-id="15bc5-136">item0</span></span>  
  
- <span data-ttu-id="15bc5-137">item1</span><span class="sxs-lookup"><span data-stu-id="15bc5-137">item1</span></span>  
  
- <span data-ttu-id="15bc5-138">item2</span><span class="sxs-lookup"><span data-stu-id="15bc5-138">item2</span></span>  
  
- <span data-ttu-id="15bc5-139">item3</span><span class="sxs-lookup"><span data-stu-id="15bc5-139">item3</span></span>  
  
  <span data-ttu-id="15bc5-140">您可以在屬性中提供 item1 和 item3 的索引鍵，以刪除 item1 和 item3。</span><span class="sxs-lookup"><span data-stu-id="15bc5-140">You can delete item1 and item3 by providing the keys of item1 and item3 in the properties:</span></span>  
  
- <span data-ttu-id="15bc5-141">item1</span><span class="sxs-lookup"><span data-stu-id="15bc5-141">item1</span></span>  
  
- <span data-ttu-id="15bc5-142">item3</span><span class="sxs-lookup"><span data-stu-id="15bc5-142">item3</span></span>  
  
  <span data-ttu-id="15bc5-143">呼叫之後，伺服器在集合中就會剩下下列項目：</span><span class="sxs-lookup"><span data-stu-id="15bc5-143">After the call, the server has the remaining items in the collection:</span></span>  
  
- <span data-ttu-id="15bc5-144">item0</span><span class="sxs-lookup"><span data-stu-id="15bc5-144">item0</span></span>  
  
- <span data-ttu-id="15bc5-145">item2</span><span class="sxs-lookup"><span data-stu-id="15bc5-145">item2</span></span>  
  
  <span data-ttu-id="15bc5-146">第二個範例顯示底下包含其他集合的項目：</span><span class="sxs-lookup"><span data-stu-id="15bc5-146">The second example shows the items containing other collections:</span></span>  
  
- <span data-ttu-id="15bc5-147">item0</span><span class="sxs-lookup"><span data-stu-id="15bc5-147">item0</span></span>  
  
  -   <span data-ttu-id="15bc5-148">item0a</span><span class="sxs-lookup"><span data-stu-id="15bc5-148">item0a</span></span>  
  
- <span data-ttu-id="15bc5-149">item1</span><span class="sxs-lookup"><span data-stu-id="15bc5-149">item1</span></span>  
  
  -   <span data-ttu-id="15bc5-150">item1a</span><span class="sxs-lookup"><span data-stu-id="15bc5-150">item1a</span></span>  
  
  -   <span data-ttu-id="15bc5-151">item1b</span><span class="sxs-lookup"><span data-stu-id="15bc5-151">item1b</span></span>  
  
  -   <span data-ttu-id="15bc5-152">item1c</span><span class="sxs-lookup"><span data-stu-id="15bc5-152">item1c</span></span>  
  
- <span data-ttu-id="15bc5-153">item2</span><span class="sxs-lookup"><span data-stu-id="15bc5-153">item2</span></span>  
  
  -   <span data-ttu-id="15bc5-154">item2a</span><span class="sxs-lookup"><span data-stu-id="15bc5-154">item2a</span></span>  
  
  -   <span data-ttu-id="15bc5-155">item2b</span><span class="sxs-lookup"><span data-stu-id="15bc5-155">item2b</span></span>  
  
  <span data-ttu-id="15bc5-156">您可以提供 item1b 和 item2 的索引鍵，以刪除 item1b 與全部的 item2。</span><span class="sxs-lookup"><span data-stu-id="15bc5-156">You can delete item1b and all of item2 by giving the keys to item1b and item2:</span></span>  
  
- <span data-ttu-id="15bc5-157">item1</span><span class="sxs-lookup"><span data-stu-id="15bc5-157">item1</span></span>  
  
  -   <span data-ttu-id="15bc5-158">item1b</span><span class="sxs-lookup"><span data-stu-id="15bc5-158">item1b</span></span>  
  
- <span data-ttu-id="15bc5-159">item2</span><span class="sxs-lookup"><span data-stu-id="15bc5-159">item2</span></span>  
  
  <span data-ttu-id="15bc5-160">為 item2 提供空白子集合，會將 item2 變成分葉，而使整個子分支都遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="15bc5-160">By providing an empty sub-collection for item2, you turn it into a leaf and that entire sub-branch is deleted.</span></span> <span data-ttu-id="15bc5-161">呼叫之後，伺服器中會剩下下列項目：</span><span class="sxs-lookup"><span data-stu-id="15bc5-161">After the call, the server has the remaining items:</span></span>  
  
- <span data-ttu-id="15bc5-162">item0</span><span class="sxs-lookup"><span data-stu-id="15bc5-162">item0</span></span>  
  
  -   <span data-ttu-id="15bc5-163">item0a</span><span class="sxs-lookup"><span data-stu-id="15bc5-163">item0a</span></span>  
  
- <span data-ttu-id="15bc5-164">item1</span><span class="sxs-lookup"><span data-stu-id="15bc5-164">item1</span></span>  
  
  -   <span data-ttu-id="15bc5-165">item1a</span><span class="sxs-lookup"><span data-stu-id="15bc5-165">item1a</span></span>  
  
  -   <span data-ttu-id="15bc5-166">item1c</span><span class="sxs-lookup"><span data-stu-id="15bc5-166">item1c</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15bc5-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15bc5-167">See Also</span></span>  
 [<span data-ttu-id="15bc5-168">附錄 A：元件介面方法</span><span class="sxs-lookup"><span data-stu-id="15bc5-168">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)