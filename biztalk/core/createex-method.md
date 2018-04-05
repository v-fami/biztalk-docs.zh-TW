---
title: CreateEx 方法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CreateEx method
ms.assetid: b62bbe25-b24d-42a7-a44c-c83521a6f0a6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b163bfbe7811c37208297aa0a61bfe91cabacde4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="createex-method"></a><span data-ttu-id="ae9af-102">CreateEx 方法</span><span class="sxs-lookup"><span data-stu-id="ae9af-102">CreateEx Method</span></span>
<span data-ttu-id="ae9af-103">建立新的記錄，使用一組的唯一索引鍵和指定的內容。</span><span class="sxs-lookup"><span data-stu-id="ae9af-103">Creates a new record using a set of unique keys and specified properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae9af-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae9af-104">Syntax</span></span>  
  
```  
CreateEx  
(key1, key2, ..., keyn, interactiveMode, properties)  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae9af-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae9af-105">Parameters</span></span>  
  
|<span data-ttu-id="ae9af-106">參數</span><span class="sxs-lookup"><span data-stu-id="ae9af-106">Parameter</span></span>|<span data-ttu-id="ae9af-107">Description</span><span class="sxs-lookup"><span data-stu-id="ae9af-107">Description</span></span>|  
|---------------|-----------------|  
|`Key in/out parameter`|<span data-ttu-id="ae9af-108">個別索引鍵參數 (key1、key2、...keyn)，這些是必須提供的參數。</span><span class="sxs-lookup"><span data-stu-id="ae9af-108">Individual key parameters (key1, key2, ... keyn), which must be supplied.</span></span><br /><br /> <span data-ttu-id="ae9af-109">這組索引鍵不得存在於伺服器資料庫中，也就是說，它們必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="ae9af-109">This set of keys must not exist in the server database, that is, they must be unique.</span></span><br /><br /> <span data-ttu-id="ae9af-110">這些索引鍵對應於針對特定元件介面所定義的 CreateEx 索引鍵集。</span><span class="sxs-lookup"><span data-stu-id="ae9af-110">These keys correspond to the set of CreateEx Keys as defined for the particular component interface.</span></span>|  
|`interactiveMode`|<span data-ttu-id="ae9af-111">處理時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ae9af-111">Error handling.</span></span><br /><br /> <span data-ttu-id="ae9af-112">在存取元件介面中的屬性時，Microsoft BizTalk Adapter for PeopleSoft Enterprise 會使用 PeopleSoft 提供的 API，這些 API 會讀取及寫入元件介面中的個別欄位；但這些變更並不會逐一傳播至 PeopleSoft 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ae9af-112">When accessing properties in a component interface, Microsoft BizTalk Adapter for PeopleSoft Enterprise uses PeopleSoft-provided APIs, which read and write individual fields in the component interface; however, these changes are not propagated to the PeopleSoft server one at a time.</span></span> <span data-ttu-id="ae9af-113">psjoa.jar (BizTalk Adapter for PeopleSoft Enterprise 的互動對象) 會先封裝所有變更，再以這個單一封裝將變更傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="ae9af-113">Instead, the psjoa.jar (with which the BizTalk Adapter for PeopleSoft Enterprise interacts) packages all the changes and sends the changes to the server in one package.</span></span><br /><br /> <span data-ttu-id="ae9af-114">如果有任何個別的更新失敗，將會傳回一般錯誤，而不會指出實際錯誤。</span><span class="sxs-lookup"><span data-stu-id="ae9af-114">If any of the individual updates fail, a generic error is returned, which does not pinpoint the actual error.</span></span> <span data-ttu-id="ae9af-115">在互動模式設為 TRUE 的情況下，每個欄位更新都會個別傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="ae9af-115">With the interactive mode set to TRUE, every field update is sent to the server individually.</span></span> <span data-ttu-id="ae9af-116">雖然這對效能會有相當程度的影響，但卻能在更新失敗時 (例如用以設定欄位的值無效時) 提供具體的錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="ae9af-116">This has a substantial impact on performance, but it does provide specific error information if the update fails (for example, if an invalid value is used for setting a field).</span></span><br /><br /> <span data-ttu-id="ae9af-117">interactiveMode 可提供最大效能，並可提供欄位更新層級的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="ae9af-117">The interactiveMode provides maximum performance and provides error reporting at the field update level.</span></span> <span data-ttu-id="ae9af-118">若要適當使用此功能，建議您平常進行呼叫時，將 interactiveMode 設為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="ae9af-118">To use this feature properly, it is recommended that normal calls be made with the interactiveMode set to FALSE.</span></span> <span data-ttu-id="ae9af-119">這樣效能應該不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="ae9af-119">There should be no impact on performance.</span></span> <span data-ttu-id="ae9af-120">如果傳回錯誤，您可以將 interactiveMode 旗標設為 TRUE，再重試相同的呼叫。</span><span class="sxs-lookup"><span data-stu-id="ae9af-120">If an error is returned, the same call can be retried with the interactiveMode flag set to TRUE.</span></span> <span data-ttu-id="ae9af-121">當呼叫失敗時，伺服器會傳回更精確的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="ae9af-121">When the call fails, the server returns a more precise error message.</span></span>|  
|`properties`|<span data-ttu-id="ae9af-122">結構，包含元件介面的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="ae9af-122">A structure that contains all the properties of the component interface.</span></span> <span data-ttu-id="ae9af-123">呼叫 `CreateEx` 方法時，這些屬性即會插入到以指定索引鍵建立的記錄中。</span><span class="sxs-lookup"><span data-stu-id="ae9af-123">When the `CreateEx` method is called, these properties are inserted into the record created with the specified key(s).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae9af-124">備註</span><span class="sxs-lookup"><span data-stu-id="ae9af-124">Remarks</span></span>  
 <span data-ttu-id="ae9af-125">在某些情況下，呼叫 `CreateEx()` 時不使用明確的索引鍵集是很常見的做法，但 `CreateEx` 函式會傳回索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ae9af-125">In some situations, it is common practice to call `CreateEx()` without a set of explicit keys, but the `CreateEx` function returns the keys.</span></span> <span data-ttu-id="ae9af-126">在伺服器上觸發的 PeopleCode 支援這種行為。</span><span class="sxs-lookup"><span data-stu-id="ae9af-126">This behavior is supported with PeopleCode that gets triggered on the server.</span></span> <span data-ttu-id="ae9af-127">例如，在建立訂單時，客戶可能不知道下一個可用的訂單編號為何。</span><span class="sxs-lookup"><span data-stu-id="ae9af-127">For example, to create a purchase order, the client may not know what the next available PO number is.</span></span> <span data-ttu-id="ae9af-128">指定 NEXT 做為訂單編號索引鍵，呼叫即會觸發 PeopleCode 來決定下一個可用的訂單編號。</span><span class="sxs-lookup"><span data-stu-id="ae9af-128">By specifying NEXT as the PO number key, the call triggers PeopleCode, which determines the next available PO number.</span></span> <span data-ttu-id="ae9af-129">這項資訊必須以 in/out 索引鍵參數傳回給呼叫端客戶。</span><span class="sxs-lookup"><span data-stu-id="ae9af-129">This information must be returned to the calling client, using the in/out key parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae9af-130">若要讓此機制順利運作，索引鍵也必須是層級 0 的屬性。</span><span class="sxs-lookup"><span data-stu-id="ae9af-130">For this mechanism to work, the key must also be a property at level 0.</span></span> <span data-ttu-id="ae9af-131">否則將會傳回原始索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ae9af-131">Otherwise, the original key is returned.</span></span>  
  
 <span data-ttu-id="ae9af-132">如果在元件介面中啟用了 PeopleSoft Create 與 Save 函式，則會提供 BizTalk Adapter for PeopleSoft Enterprise `CreateEx()` 方法。</span><span class="sxs-lookup"><span data-stu-id="ae9af-132">The BizTalk Adapter for PeopleSoft Enterprise `CreateEx()` method is provided if the PeopleSoft Create and Save functions in the component interface are enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae9af-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae9af-133">See Also</span></span>  
 [<span data-ttu-id="ae9af-134">附錄 a： 元件介面方法</span><span class="sxs-lookup"><span data-stu-id="ae9af-134">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)