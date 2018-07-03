---
title: 對 SAP 中的 Bapi 的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAPI, operations
- BAPIs, operations on
- Business Application Programming Interface
- BAPIs
- BAPI, transactions
- BAPI transactions, limitations on
ms.assetid: 6be26641-e8d3-4e11-8d82-4fdb13076580
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a319626f23b825187d65e01d687be5a1079df53a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993167"
---
# <a name="operations-on-bapis-in-sap"></a><span data-ttu-id="b6293-102">對 SAP 中的 Bapi 的作業</span><span class="sxs-lookup"><span data-stu-id="b6293-102">Operations on BAPIs in SAP</span></span>
<span data-ttu-id="b6293-103">商務應用程式發展介面 (BAPI) 是一種方法可以由外部處理序呼叫的 SAP 商務物件。</span><span class="sxs-lookup"><span data-stu-id="b6293-103">A Business Application Programming Interface (BAPI) is a method of a SAP business object that can be called by an external process.</span></span> <span data-ttu-id="b6293-104">Bapi 是 SAP 系統上的交易。</span><span class="sxs-lookup"><span data-stu-id="b6293-104">BAPIs are transactional on the SAP system.</span></span>  
  
 <span data-ttu-id="b6293-105">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] BAPI 呼叫的輸出方向的支援。</span><span class="sxs-lookup"><span data-stu-id="b6293-105">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports BAPI calls in the outbound direction.</span></span> <span data-ttu-id="b6293-106">它會呈現 Bapi 有兩種：</span><span class="sxs-lookup"><span data-stu-id="b6293-106">It surfaces BAPIs in two ways:</span></span>  
  
- <span data-ttu-id="b6293-107">**以 RFC**。</span><span class="sxs-lookup"><span data-stu-id="b6293-107">**As an RFC**.</span></span> <span data-ttu-id="b6293-108">您可以叫用 BAPI 直接叫用適當的 RFC。</span><span class="sxs-lookup"><span data-stu-id="b6293-108">You can invoke a BAPI directly by invoking the appropriate RFC.</span></span>  
  
- <span data-ttu-id="b6293-109">**為商務物件方法**。</span><span class="sxs-lookup"><span data-stu-id="b6293-109">**As methods of business objects**.</span></span> <span data-ttu-id="b6293-110">配接器為了方便起見，可協助您擷取中繼資料，當您使用商務物件方法呈現 Bapi[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b6293-110">The adapter surfaces BAPIs as methods of business objects as a convenience to help you retrieve metadata when you use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b6293-111">以 RFC 或商務物件; 方法，您可以叫用的介面卡上的 BAPI但是，不論您如何叫用 BAPI 的介面卡上，它一律會叫用 BAPI SAP 上的透過 RFC 介面。</span><span class="sxs-lookup"><span data-stu-id="b6293-111">You can invoke a BAPI on the adapter as an RFC or as a method of a business object; but regardless of how you invoke the BAPI on the adapter, it always invokes the BAPI on SAP through the RFC interface.</span></span>  
  
 <span data-ttu-id="b6293-112">配接器支援 BAPI 交易。</span><span class="sxs-lookup"><span data-stu-id="b6293-112">The adapter supports BAPI transactions.</span></span> <span data-ttu-id="b6293-113">SAP 的 BAPI 交易模型可讓使用者結合的工作 (LUW) 的一個邏輯單元的數個的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="b6293-113">The BAPI transaction model on SAP enables users to combine several BAPIs into one logical unit of work (LUW).</span></span> <span data-ttu-id="b6293-114">SAP LUW 包含參與交易，包括更新資料庫的所有步驟。</span><span class="sxs-lookup"><span data-stu-id="b6293-114">An SAP LUW consists of all the steps involved in a transaction including updating the database.</span></span>  
  
 <span data-ttu-id="b6293-115">在本節中的主題將說明 Bapi 商務物件的呈現方式和配接器如何支援 BAPI 交易 (LUWs)。</span><span class="sxs-lookup"><span data-stu-id="b6293-115">The topics in this section explain how BAPIs are surfaced as business objects and how BAPI transactions (LUWs) are supported by the adapter.</span></span>  
 
  
## <a name="bapi-operations-as-business-object-methods"></a><span data-ttu-id="b6293-116">BAPI 作業 （如商務物件方法）</span><span class="sxs-lookup"><span data-stu-id="b6293-116">BAPI Operations (as Business Object Methods)</span></span>  
 <span data-ttu-id="b6293-117">因為商務物件方法，以便於協助您擷取中繼資料，當您使用配接器瀏覽 Bapi[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b6293-117">The adapter surfaces BAPIs as business objects methods as a convenience to help you retrieve metadata when you use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span> <span data-ttu-id="b6293-118">配接器一定會使用 RFC 介面的 SAP 系統上的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="b6293-118">The adapter always invokes BAPIs on the SAP system using the RFC interface.</span></span>  
  
 <span data-ttu-id="b6293-119">配接器會呈現 Bapi 依名稱做為在適當的商務物件的作業輸出的作業。</span><span class="sxs-lookup"><span data-stu-id="b6293-119">The adapter surfaces BAPIs by name as operations under the appropriate business object for outbound operations.</span></span> <span data-ttu-id="b6293-120">商務物件會收集由配接器的 BAPI 類別目錄節點下的功能群組。</span><span class="sxs-lookup"><span data-stu-id="b6293-120">Business objects are collected by functional group under the BAPI category node by the adapter.</span></span> <span data-ttu-id="b6293-121">(您可以瀏覽或搜尋商務物件和之下的 Bapi **BAPI**當您使用的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。)</span><span class="sxs-lookup"><span data-stu-id="b6293-121">(You can browse or search for business objects and BAPIs under the **BAPI** node when you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].)</span></span>  
  
 <span data-ttu-id="b6293-122">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] Bapi 上支援下列：</span><span class="sxs-lookup"><span data-stu-id="b6293-122">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following on BAPIs:</span></span>  
  
- <span data-ttu-id="b6293-123">匯入參數</span><span class="sxs-lookup"><span data-stu-id="b6293-123">IMPORT parameters</span></span>  
  
- <span data-ttu-id="b6293-124">匯出參數</span><span class="sxs-lookup"><span data-stu-id="b6293-124">EXPORT parameters</span></span>  
  
- <span data-ttu-id="b6293-125">變更參數</span><span class="sxs-lookup"><span data-stu-id="b6293-125">CHANGING parameters</span></span>  
  
- <span data-ttu-id="b6293-126">資料表參數</span><span class="sxs-lookup"><span data-stu-id="b6293-126">Table parameters</span></span>  
  
  <span data-ttu-id="b6293-127">如需有關用來做為商務物件方法的 Bapi 的 SOAP 動作與訊息結構的詳細資訊，請參閱[BAPI 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-bapi-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="b6293-127">For more information about the message structures and SOAP actions used for BAPIs surfaced as business object methods, see [Message Schemas for BAPI Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-bapi-operations.md).</span></span>  
  
## <a name="bapi-transactions"></a><span data-ttu-id="b6293-128">BAPI 交易</span><span class="sxs-lookup"><span data-stu-id="b6293-128">BAPI Transactions</span></span>  
 <span data-ttu-id="b6293-129">當您叫用 BAPI 時，但它一定是 LUW 上 SAP 系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="b6293-129">When you invoke a BAPI, it is always part of an LUW on the SAP system.</span></span> <span data-ttu-id="b6293-130">是否為 RFC 或商務物件的方法叫用 BAPI，也是如此。</span><span class="sxs-lookup"><span data-stu-id="b6293-130">This is true whether you invoke the BAPI as an RFC or as a method of a business object.</span></span> <span data-ttu-id="b6293-131">RFC SDK 會將所有透過相同的 SAP 連線的相同 LUW 一部分傳送的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="b6293-131">The RFC SDK treats all BAPIs sent over the same SAP connection as part of the same LUW.</span></span> <span data-ttu-id="b6293-132">呼叫之後認可或復原交易上的連接，透過連線傳送的下一個 BAPI 會開始新 LUW。</span><span class="sxs-lookup"><span data-stu-id="b6293-132">After a call to commit or roll back the transaction on a connection, the next BAPI sent over the connection begins a new LUW.</span></span>  
  
 <span data-ttu-id="b6293-133">您可以呼叫 BAPI_TRANSACTION_COMMIT 或 BAPI_TRANSACTION_ROLLBACK 認可或回復交易。</span><span class="sxs-lookup"><span data-stu-id="b6293-133">You call BAPI_TRANSACTION_COMMIT or BAPI_TRANSACTION_ROLLBACK to commit or roll back the transaction.</span></span> <span data-ttu-id="b6293-134">配接器會呈現這些兩個 Bapi:</span><span class="sxs-lookup"><span data-stu-id="b6293-134">The adapter surfaces these two BAPIs:</span></span>  
  
- <span data-ttu-id="b6293-135">在以 RFC 作業的基礎節點。</span><span class="sxs-lookup"><span data-stu-id="b6293-135">Under the Basis node as RFC operations.</span></span>  
  
- <span data-ttu-id="b6293-136">在每個商務物件。</span><span class="sxs-lookup"><span data-stu-id="b6293-136">Under each business object.</span></span>  
  
  <span data-ttu-id="b6293-137">您可以確保，所有傳送相同的 SAP 連線 （包括認可或回復交易的呼叫），以控制在交易中的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="b6293-137">You control the BAPIs in a transaction by ensuring that they are all sent over the same SAP connection (including the call to commit or roll back the transaction).</span></span> <span data-ttu-id="b6293-138">您可以在中來這樣做：</span><span class="sxs-lookup"><span data-stu-id="b6293-138">You can do this in:</span></span>  
  
- <span data-ttu-id="b6293-139">使用 BizTalk 解決方案**ConnectionState**訊息內容屬性，以確保在交易中的 Bapi 會傳送使用相同的連線。</span><span class="sxs-lookup"><span data-stu-id="b6293-139">BizTalk Solutions by using the **ConnectionState** message context property to ensure that the BAPIs in a transaction are sent using the same connection.</span></span> <span data-ttu-id="b6293-140">這個屬性會顯示由配接器，並提供您明確控制用來傳送訊息，BizTalk 協調流程中的連接。</span><span class="sxs-lookup"><span data-stu-id="b6293-140">This property is surfaced by the adapter and provides you with explicit control over the connection used to send a message in a BizTalk orchestration.</span></span>  
  
   <span data-ttu-id="b6293-141">執行 BAPI 交易使用 BizTalk Server[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列的訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="b6293-141">For performing BAPI transactions using BizTalk Server, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following message context properties.</span></span>  
  
  |<span data-ttu-id="b6293-142">欄位</span><span class="sxs-lookup"><span data-stu-id="b6293-142">Field</span></span>|<span data-ttu-id="b6293-143">描述</span><span class="sxs-lookup"><span data-stu-id="b6293-143">Description</span></span>|  
  |-----------|-----------------|  
  |<span data-ttu-id="b6293-144">OPEN</span><span class="sxs-lookup"><span data-stu-id="b6293-144">OPEN</span></span>|<span data-ttu-id="b6293-145">開啟交易的新通道。</span><span class="sxs-lookup"><span data-stu-id="b6293-145">Opens a new channel for the transaction.</span></span>|  
  |<span data-ttu-id="b6293-146">重複使用</span><span class="sxs-lookup"><span data-stu-id="b6293-146">REUSE</span></span>|<span data-ttu-id="b6293-147">重複使用交易的現有通道。</span><span class="sxs-lookup"><span data-stu-id="b6293-147">Reuse existing channel for the transaction.</span></span>|  
  |<span data-ttu-id="b6293-148">CLOSE</span><span class="sxs-lookup"><span data-stu-id="b6293-148">CLOSE</span></span>|<span data-ttu-id="b6293-149">認可交易，並關閉現有的通道。</span><span class="sxs-lookup"><span data-stu-id="b6293-149">Commit the transaction and close the existing channel.</span></span>|  
  |<span data-ttu-id="b6293-150">ABORT</span><span class="sxs-lookup"><span data-stu-id="b6293-150">ABORT</span></span>|<span data-ttu-id="b6293-151">中止交易，並關閉現有的通道。</span><span class="sxs-lookup"><span data-stu-id="b6293-151">Abort the transaction and close the existing channel.</span></span>|  
  
   <span data-ttu-id="b6293-152">如需詳細資訊，請參閱 < [SAP 使用 BizTalk Server 中執行 BAPI 交易](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b6293-152">For more information, see [Run BAPI Transactions in SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md).</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="b6293-153">請確定您設定**EnableBizTalkCompatibilityMode**執行使用 BizTalk Server 的交易時，繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="b6293-153">Make sure you set the **EnableBizTalkCompatibilityMode**binding property when performing transactions using BizTalk Server.</span></span>  
  
- <span data-ttu-id="b6293-154">藉由確保在交易中的 Bapi 使用相同的 WCF 用戶端傳送的 WCF 服務模型方案。</span><span class="sxs-lookup"><span data-stu-id="b6293-154">WCF service model solutions by ensuring that the BAPIs in a transaction are sent using the same WCF client.</span></span> <span data-ttu-id="b6293-155">如需詳細資訊，請參閱 < [SAP 使用 WCF 服務模型中的 叫用 Bapi](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="b6293-155">For more information, see [Invoke BAPIs in SAP using WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md).</span></span>  
  
- <span data-ttu-id="b6293-156">WCF 通道模型的解決方案藉由確保在交易中的 Bapi 會透過相同的 WCF 通道傳送。</span><span class="sxs-lookup"><span data-stu-id="b6293-156">WCF channel model solutions by ensuring that the BAPIs in a transaction are sent over the same WCF channel.</span></span> <span data-ttu-id="b6293-157">如需詳細資訊，請參閱 <<c0> [ 使用 WCF 通道模型開發應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="b6293-157">For more information, see [Develop applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md).</span></span>  
  
### <a name="limitations-on-bapi-transactions"></a><span data-ttu-id="b6293-158">BAPI 交易的限制</span><span class="sxs-lookup"><span data-stu-id="b6293-158">Limitations on BAPI Transactions</span></span>  
 <span data-ttu-id="b6293-159">BAPI 交易，適用下列限制：</span><span class="sxs-lookup"><span data-stu-id="b6293-159">The following restrictions apply on BAPI transactions:</span></span>  
  
- <span data-ttu-id="b6293-160">您不可能進行一個 LUW 內相同的執行個體上的兩個的寫入存取。</span><span class="sxs-lookup"><span data-stu-id="b6293-160">It is not possible to make two write accesses on the same instance within one LUW.</span></span> <span data-ttu-id="b6293-161">例如，您無法建立訂單，並在相同交易中更新它。</span><span class="sxs-lookup"><span data-stu-id="b6293-161">For example, you cannot create an order and update it in the same transaction.</span></span>  
  
- <span data-ttu-id="b6293-162">執行 BAPI 交易使用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，必須透過傳送埠的單一主機執行個體傳送的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="b6293-162">When performing BAPI a transaction using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], all the messages must be sent over a single host instance of the send port.</span></span>  
  
- <span data-ttu-id="b6293-163">如果執行個體是建立、 更新或刪除使用 BAPI 的寫入，讀取 BAPI 無法檢視最新的資料，直到體會認可寫入 BAPI。</span><span class="sxs-lookup"><span data-stu-id="b6293-163">If an instance is created, updated, or deleted by using a write BAPI, a read BAPI cannot view the most recent data until the write BAPI is committed.</span></span>  
  
- <span data-ttu-id="b6293-164">外部用戶端叫用 LUW 應該在相同的 SAP 連接上呼叫 LUW 包含的所有 Bapi。</span><span class="sxs-lookup"><span data-stu-id="b6293-164">An external client that invokes an LUW should call all the BAPIs that the LUW contains on the same SAP connection.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b6293-165">屬於版本 3.1 的 Bapi 呼叫 COMMIT WORK，做為其實作的一部分。</span><span class="sxs-lookup"><span data-stu-id="b6293-165">BAPIs that belong to Release 3.1 call COMMIT WORK as part of their implementation.</span></span> <span data-ttu-id="b6293-166">這表示，（因為它們將會認可交易），這些 Bapi 不能包含其他 LUW 中的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="b6293-166">This means that these BAPIs cannot be included with other BAPIs in an LUW (because they will commit the transaction).</span></span> <span data-ttu-id="b6293-167">如需詳細資訊，請參閱 SAP 文件。</span><span class="sxs-lookup"><span data-stu-id="b6293-167">For more information, see the SAP documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6293-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6293-168">See Also</span></span>  
 <span data-ttu-id="b6293-169">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="b6293-169">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>