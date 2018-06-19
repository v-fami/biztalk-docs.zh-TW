---
title: 限制查詢及擷取清單 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, querying limitations
- querying, limitations [JD Edwards OneWorld adapters]
ms.assetid: 1b6f5d2a-d1e2-4c78-8f4a-f00d10f008b9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f2e0f813a793aa05756ef52925081375203f2f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262334"
---
# <a name="limitations-when-querying-and-retrieving-lists"></a><span data-ttu-id="dba42-102">查詢及擷取清單的限制</span><span class="sxs-lookup"><span data-stu-id="dba42-102">Limitations When Querying and Retrieving Lists</span></span>
<span data-ttu-id="dba42-103">JD Edwards OneWorld 通訊架構是單一訊息、單一回應的架構。</span><span class="sxs-lookup"><span data-stu-id="dba42-103">The JD Edwards OneWorld communication architecture is a single-message, single-reply architecture.</span></span> <span data-ttu-id="dba42-104">您不能傳回訊息清單或陣列。</span><span class="sxs-lookup"><span data-stu-id="dba42-104">You cannot return a list of messages or an array.</span></span> <span data-ttu-id="dba42-105">基底程式碼是 C++，它會以單一結構的指標呼叫、在結構中進行變更，然後再結束。</span><span class="sxs-lookup"><span data-stu-id="dba42-105">The underlying code is C++, which calls with a pointer to a single structure, makes changes in the structure, and then exits.</span></span>  
  
## <a name="querying-and-retrieving-lists"></a><span data-ttu-id="dba42-106">查詢及擷取清單</span><span class="sxs-lookup"><span data-stu-id="dba42-106">Querying and Retrieving Lists</span></span>  
 <span data-ttu-id="dba42-107">由於 JD Edwards OneWorld 商務功能架構的限制，因此您不能使用 Microsoft BizTalk Adapter for JD Edwards OneWorld 根據搜尋準則來查詢及擷取記錄清單。</span><span class="sxs-lookup"><span data-stu-id="dba42-107">You cannot query and retrieve lists of records based on search criteria using Microsoft BizTalk Adapter for JD Edwards OneWorld due to a limitation with the JD Edwards OneWorld business function architecture.</span></span>  
  
 <span data-ttu-id="dba42-108">在 JD Edwards OneWorld 中，資料庫連線是利用一組專屬 (且複雜) 的內部功能呼叫來提供。</span><span class="sxs-lookup"><span data-stu-id="dba42-108">In JD Edwards OneWorld, database connectivity is provided by using a set of proprietary (and complex) internal function calls.</span></span> <span data-ttu-id="dba42-109">這些呼叫會透過要求非常明確及低階的呼叫建立要擷取或更新的資料行清單，以遮罩基底資料庫版本，並建立適用於排序或選擇的特定結構。</span><span class="sxs-lookup"><span data-stu-id="dba42-109">These calls mask the underlying database version by requiring very explicit and low-level calls to create lists of columns to retrieve or update, and create specialized structures for sorting or selection.</span></span> <span data-ttu-id="dba42-110">API 的集合不會透過 Java 或其他任何連線方法公開，因此記錄集無法透過商務功能來處理。</span><span class="sxs-lookup"><span data-stu-id="dba42-110">The sets of APIs are not exposed through the Java (or any other) connectivity method; therefore, record sets cannot be handled through business functions.</span></span>  
  
 <span data-ttu-id="dba42-111">在 JD Edwards OneWorld 工具組內，您可以建立處理單一記錄或操作一組記錄的商務功能；不過，存取 JD Edwards OneWorld 工具外部的項目清單更為困難。</span><span class="sxs-lookup"><span data-stu-id="dba42-111">Within the JD Edwards OneWorld toolset, you can create business functions that handle a single record or operate on a group of records; however, accessing lists of items outside the JD Edwards OneWorld tools is more difficult.</span></span>  
  
 <span data-ttu-id="dba42-112">若要解決此問題，您可以建立根據查詢傳回記錄索引鍵清單的自訂商務功能。</span><span class="sxs-lookup"><span data-stu-id="dba42-112">To work around this issue, you can create a custom business function that returns a list of record keys based on a query.</span></span> <span data-ttu-id="dba42-113">您必須分割清單，因為 JDENET (JD Edwards OneWorld 內部專屬訊息 API) 對管理大型或未繫結結果集的訊息緩衝區大小有限制。</span><span class="sxs-lookup"><span data-stu-id="dba42-113">You must segment the lists, because JDENET (the JD Edwards OneWorld internal proprietary messaging API) has a limitation on the message buffer size for managing large or unbounded result sets.</span></span> <span data-ttu-id="dba42-114">用戶端程式碼必須逐一查看對商務功能的後續呼叫 (或對其執行迴圈)，直到傳回指標，指出清單是完整的為止。</span><span class="sxs-lookup"><span data-stu-id="dba42-114">The client code must iterate (loop) through successive calls to the business function, until an indicator is returned stating that the list is complete.</span></span>  
  
## <a name="controlling-iteration"></a><span data-ttu-id="dba42-115">控制反覆項目</span><span class="sxs-lookup"><span data-stu-id="dba42-115">Controlling Iteration</span></span>  
 <span data-ttu-id="dba42-116">JD Edwards OneWorld 商務功能的所有呼叫都沒有狀態，因此商務功能無法因應要求維護開啟的資料指標並傳回其他資料列。</span><span class="sxs-lookup"><span data-stu-id="dba42-116">All calls to JD Edwards OneWorld business functions are stateless; therefore, the business function cannot maintain an open cursor and return more rows on request.</span></span> <span data-ttu-id="dba42-117">每次呼叫時都必須將位置資訊傳遞至 JD Edwards OneWorld XE 商務功能。</span><span class="sxs-lookup"><span data-stu-id="dba42-117">Positioning information must be passed to the JD Edwards OneWorld XE business function on each call.</span></span>  
  
 <span data-ttu-id="dba42-118">以下列出用來控制反覆項目的技術：</span><span class="sxs-lookup"><span data-stu-id="dba42-118">The following is a list of techniques for controlling iteration:</span></span>  
  
-   <span data-ttu-id="dba42-119">在 JD Edwards OneWorld 端，將結果集寫入暫存儲存檔案，這個檔案會傳回可在後續呼叫中提供的 ID (例如檔案名稱或工作號碼)，以及用來放置資料指標的記錄編號。</span><span class="sxs-lookup"><span data-stu-id="dba42-119">On the JD Edwards OneWorld side, write the result set to a temporary storage file, which returns an ID (such as a file name or job number) that can be given on successive calls, along with the record number to position the cursor.</span></span> <span data-ttu-id="dba42-120">任何後續呼叫都會依據傳入的記錄編號放入清單內。</span><span class="sxs-lookup"><span data-stu-id="dba42-120">Any successive call is positioned within the list based on the passed-in record number.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dba42-121">透過 BizTalk Adapter for JD Edwards OneWorld 呼叫可以保持負載平衡；不過，這些呼叫最後會由單一應用程式伺服器根據認證和呼叫的商務功能來處理。</span><span class="sxs-lookup"><span data-stu-id="dba42-121">Calls through BizTalk Adapter for JD Edwards OneWorld can be load-balanced; however, they are eventually served by a single application server based on the credentials and business function being called.</span></span> <span data-ttu-id="dba42-122">因此，如果呼叫在伺服器上建立了暫存儲存檔案，其他呼叫都會由相同的伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="dba42-122">Therefore, if a call creates a temporary file on a server, additional calls are served by the same server.</span></span> <span data-ttu-id="dba42-123">如需詳細資訊，請參閱《JD Edwards OneWorld CNC 指南》(JD Edwards OneWorld CNC Guides) 中的＜物件組態對應＞(Object Configuration Mapping)。</span><span class="sxs-lookup"><span data-stu-id="dba42-123">For more information, see Object Configuration Mapping in the JD Edwards OneWorld CNC Guides.</span></span>  
  
-   <span data-ttu-id="dba42-124">位置資訊 (例如主索引鍵值) 可在第二個和後續的呼叫中傳回，而且查詢可以根據索引鍵重新發出，做為額外的參數。</span><span class="sxs-lookup"><span data-stu-id="dba42-124">Position information (such as a primary key value) can be returned on the second and subsequent calls, and the query can be reissued based on the key as an additional parameter.</span></span> <span data-ttu-id="dba42-125">這個方法可用於 BizTalk Adapter for JD Edwards OneWorld 的儲存機制瀏覽程式碼。</span><span class="sxs-lookup"><span data-stu-id="dba42-125">This method is used in the repository browsing code for BizTalk Adapter for JD Edwards OneWorld.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dba42-126">在前兩項技術中，建議的方法是使用主索引鍵值並重新發出查詢。</span><span class="sxs-lookup"><span data-stu-id="dba42-126">Of the first two techniques, the recommended method is to use primary key values and reissue the query.</span></span> <span data-ttu-id="dba42-127">這種方法需要最少量的程式碼，而且會對資料庫造成最佳化和快取負荷。</span><span class="sxs-lookup"><span data-stu-id="dba42-127">This method requires the smallest amount of code and places the optimization and caching burden on the database.</span></span>  
  
-   <span data-ttu-id="dba42-128">呼叫端應用程式可以儲存一份主索引鍵 (例如交互參照).的清單。</span><span class="sxs-lookup"><span data-stu-id="dba42-128">The calling application can store a list of primary keys (such as a cross reference).</span></span> <span data-ttu-id="dba42-129">例如，如果客戶關係管理 (CRM) 系統建立了客戶記錄，然後使用商務功能呼叫將它加入到 JD Edwards OneWorld 中，則加入客戶記錄的商務功能將會設定 AN8 欄位 (簡短的位址編號) 的值，並顯示在傳回緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="dba42-129">For example, if a customer relationship management (CRM) system creates a customer record and then adds it to JD Edwards OneWorld using a business function call, the business function that adds a customer record sets the value for the AN8 field (short address number) and is visible in the return buffer.</span></span> <span data-ttu-id="dba42-130">接著這個編號就可以寫入原始客戶記錄上的參考欄位，或是儲存在自訂的交互參照資料表中。</span><span class="sxs-lookup"><span data-stu-id="dba42-130">This number can then be written to a reference field on the original customer record, or stored into a customized cross-reference table.</span></span>  
  
-   <span data-ttu-id="dba42-131">JD Edwards OneWorld 中的所有主要記錄大部分都有尋查或替代索引鍵的概念。</span><span class="sxs-lookup"><span data-stu-id="dba42-131">The majority of all master records in JD Edwards OneWorld have a concept of a lookup, or alternate key.</span></span> <span data-ttu-id="dba42-132">這個索引鍵可以用來儲存呼叫端系統的索引鍵資訊。</span><span class="sxs-lookup"><span data-stu-id="dba42-132">This key can be used to store the key information from the calling system.</span></span> <span data-ttu-id="dba42-133">商務功能可以在 JD Edwards OneWorld 端執行尋查作業。</span><span class="sxs-lookup"><span data-stu-id="dba42-133">Business functions can perform the lookup on the JD Edwards OneWorld side.</span></span> <span data-ttu-id="dba42-134">將參數傳遞到商務功能以建立客戶記錄時，將會設定完整的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="dba42-134">When parameters are passed to the business function to create a customer record, the long key value is set.</span></span>  
  
 <span data-ttu-id="dba42-135">如需這些概念的詳細資訊，請參閱 JD Edwards OneWorld 說明系統中的＜互通性＞(Interoperability) 主題。</span><span class="sxs-lookup"><span data-stu-id="dba42-135">For more information on these concepts, see the Interoperability topic in the JD Edwards OneWorld Help system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba42-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dba42-136">See Also</span></span>  
 [<span data-ttu-id="dba42-137">規劃與架構</span><span class="sxs-lookup"><span data-stu-id="dba42-137">Planning and Architecture</span></span>](../core/planning-and-architecture17.md)