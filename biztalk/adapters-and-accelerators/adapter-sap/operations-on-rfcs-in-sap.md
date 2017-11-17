---
title: "作業中 SAP Rfc |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, operations on RFCs
- adapters, operations on IDOCs
- RFC, receiving inbound RFC calls from an SAP system
- RFCs, invoking RFCs on an SAP system
- adapters, operations on BAPIs
- RFC client
- adapters, operations on tRFCs
- RFC server
ms.assetid: ca1b7b00-a9cf-41bc-b87c-2e7ce8cff65c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd4ebbb33e9f9791589a3ef271412c8ae20090f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-rfcs-in-sap"></a><span data-ttu-id="d5aa3-102">作業中 SAP Rfc</span><span class="sxs-lookup"><span data-stu-id="d5aa3-102">Operations on RFCs in SAP</span></span>
<span data-ttu-id="d5aa3-103">您可以使用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]同時 RFC 用戶端和 RFC 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-103">You can use the[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] both as an RFC client and as an RFC server.</span></span> <span data-ttu-id="d5aa3-104">在 RFC 用戶端的情況下，您的應用程式的叫用 Rfc SAP 系統上叫用 RFC 作業上[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-104">In RFC client scenarios, your application invokes RFCs on the SAP system by invoking RFC operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="d5aa3-105">在 RFC 伺服器案例中的 SAP 系統會叫用 Rfc 上[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，，接著，會叫用 RFC 成為您的應用程式的作業。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-105">In RFC server scenarios the SAP system invokes RFCs on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], which, in turn, invokes the RFC as an operation on your application.</span></span>  
  
## <a name="rfc-operations"></a><span data-ttu-id="d5aa3-106">RFC 作業</span><span class="sxs-lookup"><span data-stu-id="d5aa3-106">RFC Operations</span></span>  
 <span data-ttu-id="d5aa3-107">Rfc 依名稱顯示為 RFC 的中繼資料類別目錄的節點下的讀取作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-107">RFCs are surfaced by name as operations under the RFC metadata category node by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="d5aa3-108">(您可以瀏覽或搜尋在 Rfc **RFC**節點，當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。)</span><span class="sxs-lookup"><span data-stu-id="d5aa3-108">(You can browse or search for RFCs under the **RFC** node when you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].)</span></span>  
  
 <span data-ttu-id="d5aa3-109">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可以介面只在它可以為其擷取中繼資料從 SAP 系統的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-109">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can surface only those RFCs for which it can retrieve metadata from the SAP system.</span></span> <span data-ttu-id="d5aa3-110">配接器使用 RFC SDK 擷取此中繼資料，因此它無法介面包含由 RFC SDK 不支援的資料型別參數的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-110">The adapter uses the RFC SDK to retrieve this metadata, so it cannot surface RFCs that contain parameters with data types that are not supported by the RFC SDK.</span></span> <span data-ttu-id="d5aa3-111">例如，配接器無法介面包含 ITAB II 類型結構或資料表的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-111">For example, the adapter cannot surface RFCs that contain ITAB II type structures or tables.</span></span>  
  
 <span data-ttu-id="d5aa3-112">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列 Rfc 上：</span><span class="sxs-lookup"><span data-stu-id="d5aa3-112">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following on RFCs:</span></span>  
  
-   <span data-ttu-id="d5aa3-113">匯入參數</span><span class="sxs-lookup"><span data-stu-id="d5aa3-113">IMPORT parameters</span></span>  
  
-   <span data-ttu-id="d5aa3-114">匯出參數</span><span class="sxs-lookup"><span data-stu-id="d5aa3-114">EXPORT parameters</span></span>  
  
-   <span data-ttu-id="d5aa3-115">變更參數</span><span class="sxs-lookup"><span data-stu-id="d5aa3-115">CHANGING parameters</span></span>  
  
 <span data-ttu-id="d5aa3-116">如需 rfc 配接器使用的 SOAP 動作與訊息結構的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-116">For more information about the message structures and SOAP actions used for RFCs by the adapter, see [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span></span>  
  
## <a name="invoking-rfcs-on-an-sap-system"></a><span data-ttu-id="d5aa3-117">SAP 系統上叫用的 Rfc</span><span class="sxs-lookup"><span data-stu-id="d5aa3-117">Invoking RFCs on an SAP System</span></span>  
 <span data-ttu-id="d5aa3-118">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] Rfc 呈現為個別的作業在 SAP 系統上進行 RFC 的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-118">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces RFCs as individual operations that take the name of the RFC on the SAP system.</span></span> <span data-ttu-id="d5aa3-119">要叫用的 RFC，SAP 系統上，您將叫用配接器的適當具名的 RFC 作業。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-119">To invoke an RFC on the SAP system, you invoke the appropriately named RFC operation on the adapter.</span></span>  
  
 <span data-ttu-id="d5aa3-120">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="d5aa3-120">For more information about:</span></span>  
  
-   <span data-ttu-id="d5aa3-121">叫用 RFC 使用 BizTalk Server，請參閱[使用 BizTalk server 叫用的 Rfc](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-121">Invoking an RFC using BizTalk Server, see [Invoke RFCs by Using BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="d5aa3-122">叫用 RFC 使用 WCF 服務模型，請參閱[SAP 使用 WCF 服務模型中的 叫用 Rfc](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-122">Invoking an RFC using the WCF service model, see [Invoke RFCs in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="d5aa3-123">叫用 RFC 使用 WCF 通道模型，請參閱[SAP 系統所使用 WCF 通道模型上的叫用作業](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-123">Invoking an RFC using the WCF channel model, see [Invoke Operations on the SAP System by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="receiving-inbound-rfc-calls-from-an-sap-system"></a><span data-ttu-id="d5aa3-124">從 SAP 系統接收輸入的 RFC 呼叫</span><span class="sxs-lookup"><span data-stu-id="d5aa3-124">Receiving Inbound RFC Calls from an SAP System</span></span>  
 <span data-ttu-id="d5aa3-125">很可能適用於 SAP 做為用戶端，並叫用外部 RFC 伺服器上的函式模組。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-125">It is possible for SAP to act as a client and invoke function modules on an external RFC server.</span></span> <span data-ttu-id="d5aa3-126">這項功能可讓：</span><span class="sxs-lookup"><span data-stu-id="d5aa3-126">This functionality enables:</span></span>  
  
-   <span data-ttu-id="d5aa3-127">SAP 到外部系統推播通知，而不需要藉由呼叫 Rfc 持續輪詢通知的 SAP 外部系統。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-127">SAP to push notifications to external systems without the external systems having to continuously poll SAP for notifications by calling RFCs.</span></span>  
  
-   <span data-ttu-id="d5aa3-128">SAP 系統之外的商務邏輯的實作。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-128">The implementation of business logic outside the SAP system.</span></span> <span data-ttu-id="d5aa3-129">SAP 系統就可以在 RFC 伺服器呼叫外部程式。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-129">The SAP system can then call the external program on the RFC server.</span></span>  
  
 <span data-ttu-id="d5aa3-130">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可以做為 RFC 伺服器從 SAP 系統接收這類輸入的 RFC 呼叫。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-130">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can act as an RFC server to receive such inbound RFC calls from the SAP system.</span></span> <span data-ttu-id="d5aa3-131">當配接器會從 SAP 接收 RFC 呼叫時，它會叫用該 RFC 作業，在您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-131">When the adapter receives an RFC call from SAP, it invokes that RFC operation on your application.</span></span>  
  
 <span data-ttu-id="d5aa3-132">若要執行 RFC 伺服器配接器：</span><span class="sxs-lookup"><span data-stu-id="d5aa3-132">For the adapter to perform as an RFC server:</span></span>  
  
-   <span data-ttu-id="d5aa3-133">必須宣告 RFC，SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-133">The RFC must be declared on the SAP system.</span></span> <span data-ttu-id="d5aa3-134">這是讓配接器可以擷取描述從 SAP 系統的 RFC 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-134">This is so the adapter can retrieve metadata that describes the RFC from the SAP system.</span></span> <span data-ttu-id="d5aa3-135">RFC 實際上是在您的應用程式中實作的。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-135">The RFC is actually implemented in your application.</span></span>  
  
-   <span data-ttu-id="d5aa3-136">配接器必須向 SAP 閘道上的 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-136">The adapter must register with an RFC destination on an SAP gateway.</span></span> <span data-ttu-id="d5aa3-137">註冊為基礎的邏輯名稱呼叫的程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-137">The registration is based on a logical name called a program ID.</span></span> <span data-ttu-id="d5aa3-138">您提供的連線 URI 指定的程式識別碼，SAP 閘道和 SAP 此註冊的伺服器中的參數。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-138">You supply parameters in the connection URI to specify the PROGRAM ID, SAP gateway, and SAP server for this registration.</span></span>  
  
 <span data-ttu-id="d5aa3-139">下列範例顯示叫用程式 ID，MYDEST 透過 RFC 所需的 ABAP 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-139">The following example shows the ABAP code required to invoke an RFC through the PROGRAM ID, MYDEST.</span></span>  
  
```  
CALL FUNCTION ‘ABC’ DESTINATION ‘MYDEST’  
```  
  
 <span data-ttu-id="d5aa3-140">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="d5aa3-140">For more information about:</span></span>  
  
-   <span data-ttu-id="d5aa3-141">接收 RFC 伺服器呼叫使用 BizTalk Server，請參閱[接收輸入 RFC 呼叫使用 BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-141">Receiving an RFC server call using BizTalk Server, see [Receive Inbound RFC Calls by Using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="d5aa3-142">接收 RFC 伺服器呼叫使用 WCF 服務模型，請參閱[接收輸入 RFC 呼叫中使用 WCF 服務模型的 SAP](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-142">Receiving an RFC server call using the WCF service model, see [Receive  Inbound RFC Calls in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="d5aa3-143">接收 RFC 伺服器呼叫使用 WCF 通道模型，請參閱[接收輸入作業使用的 WCF 通道模型的 SAP 系統從](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-143">Receiving an RFC server call using the WCF channel model, see [Receive Inbound Operations from the SAP System by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="special-rfc-operations"></a><span data-ttu-id="d5aa3-144">特殊 RFC 作業</span><span class="sxs-lookup"><span data-stu-id="d5aa3-144">Special RFC Operations</span></span>  
 <span data-ttu-id="d5aa3-145">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也可以執行 SAP 系統上的某些特殊 RFC 作業。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-145">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can also perform certain special RFC operations on the SAP system.</span></span> <span data-ttu-id="d5aa3-146">一個這類作業是 RfcGetAttributes。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-146">One such operation is RfcGetAttributes.</span></span>  
  
-   <span data-ttu-id="d5aa3-147">**RfcGetAttributes**。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-147">**RfcGetAttributes**.</span></span> <span data-ttu-id="d5aa3-148">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會使用這項作業取得 RFC 連線參數，例如系統識別碼、 夥伴的字碼頁和語言的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-148">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses this operation to get information about the RFC connection parameters such as system ID, partner code page, and language.</span></span> <span data-ttu-id="d5aa3-149">這項作業時才可使用**RFC**節點時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-149">This operation is available under the **RFC** node when using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
 <span data-ttu-id="d5aa3-150">如需訊息結構和叫用 RfcGetAttributes 作業 SAP 系統上的 SOAP 動作的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="d5aa3-150">For more information about message structure and SOAP action for invoking an RfcGetAttributes operation on the SAP system, see [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5aa3-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5aa3-151">See Also</span></span>  
 <span data-ttu-id="d5aa3-152">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="d5aa3-152">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>