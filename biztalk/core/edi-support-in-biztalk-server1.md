---
title: EDI 支援中 BizTalk Server1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cddab7a-99ef-4dbb-bb74-9e3d03df3996
caps.latest.revision: 37
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e8351420ed8d7815944c3ae619420137a8a61df
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006967"
---
# <a name="edi-support-in-biztalk-server"></a><span data-ttu-id="22dd9-102">BizTalk Server 中的 EDI 支援</span><span class="sxs-lookup"><span data-stu-id="22dd9-102">EDI Support in BizTalk Server</span></span>
<span data-ttu-id="22dd9-103">本主題提供 EDI 和 BizTalk Server 如何支援 EDI 的簡短一般概觀。</span><span class="sxs-lookup"><span data-stu-id="22dd9-103">This topic provides a brief general overview of EDI and how BizTalk Server supports EDI.</span></span>  
  
## <a name="introduction-to-edi"></a><span data-ttu-id="22dd9-104">EDI 簡介</span><span class="sxs-lookup"><span data-stu-id="22dd9-104">Introduction to EDI</span></span>  
 <span data-ttu-id="22dd9-105">「電子資料交換」(EDI) 是商業交易夥伴交換 (Exchange) 電子資料時最常使用的方法。</span><span class="sxs-lookup"><span data-stu-id="22dd9-105">Electronic Data Interchange (EDI) is the single most commonly used means by which business trading partners exchange data electronically.</span></span> <span data-ttu-id="22dd9-106">EDI 主要為訊息導向。</span><span class="sxs-lookup"><span data-stu-id="22dd9-106">EDI is largely messaging-oriented.</span></span> <span data-ttu-id="22dd9-107">文件都會實作為一般檔案，其中可包含批次交易集。</span><span class="sxs-lookup"><span data-stu-id="22dd9-107">Documents are implemented as flat files that can include batched transaction sets.</span></span> <span data-ttu-id="22dd9-108">批次交換 (Interchange) 可以包含多個群組，每個群組又可以包含多個交易集或訊息。</span><span class="sxs-lookup"><span data-stu-id="22dd9-108">Batched interchanges can contain multiple groups, each of which can contain multiple transaction sets or messages.</span></span>  
  
 <span data-ttu-id="22dd9-109">EDI 包含標準組織所制定的特定資料交換 (Interchange) 方法。</span><span class="sxs-lookup"><span data-stu-id="22dd9-109">EDI consists of specific data interchange methods agreed upon by standards bodies.</span></span> <span data-ttu-id="22dd9-110">主要的 EDI 標準是 X12 (由 ANSI 制定標準，主要用於北美洲) 及 EDIFACT (由聯合國制定標準，主要用於美國境外)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-110">The primary EDI standards are X12 (standardized by ANSI and used primarily in North America) and EDIFACT (standardized by the United Nations and used primarily outside the U.S.).</span></span> <span data-ttu-id="22dd9-111">其他標準都衍伸自這些標準，例如，HIPAA 衍伸自 X12，韓國的 KEDIFACT 衍伸自 EDIFACT。</span><span class="sxs-lookup"><span data-stu-id="22dd9-111">Other standards are derived from these, for example, HIPAA from X12 and KEDIFACT in Korea from EDIFACT.</span></span> <span data-ttu-id="22dd9-112">這些標準在訊息結構和通知結構描述方面近乎相同，卻又有明顯的差異處。</span><span class="sxs-lookup"><span data-stu-id="22dd9-112">The standards are closely parallel in message structure and acknowledgment schemes, but have distinct differences.</span></span>  
  
 <span data-ttu-id="22dd9-113">EDI 標準規定下列項目：</span><span class="sxs-lookup"><span data-stu-id="22dd9-113">The EDI standards prescribe the following:</span></span>  
  
-   <span data-ttu-id="22dd9-114">文件交換 (Exchange) 中使用的格式、字元集和資料元素。</span><span class="sxs-lookup"><span data-stu-id="22dd9-114">The formats, character sets, and data elements used in the exchange of documents</span></span>  
  
-   <span data-ttu-id="22dd9-115">EDI 交易中使用的信封</span><span class="sxs-lookup"><span data-stu-id="22dd9-115">The envelopes used in EDI transaction</span></span>  
  
-   <span data-ttu-id="22dd9-116">確認送達所需的通知</span><span class="sxs-lookup"><span data-stu-id="22dd9-116">The acknowledgments required to verify delivery</span></span>  
  
-   <span data-ttu-id="22dd9-117">提供保證只需一次的傳遞方式，以及自動偵測和報告損毀或不正確的資料。</span><span class="sxs-lookup"><span data-stu-id="22dd9-117">How to provide guaranteed, exactly-once delivery, and automatic detection and reporting of corrupted or incorrect data.</span></span>  
  
 <span data-ttu-id="22dd9-118">雖然 EDI 標準會建立文件結構的規則，但交易夥伴仍需同意要傳輸哪些特定資訊，以及這些資訊的使用方式。</span><span class="sxs-lookup"><span data-stu-id="22dd9-118">While the EDI standards establish the rules for the structure of the document, trading partners must agree on the specific information to be transmitted and how it should be used.</span></span> <span data-ttu-id="22dd9-119">連接兩個交易夥伴之 EDI 系統的設計走向，取決於標準所需的項目，以及交易夥伴達成協議的內容。</span><span class="sxs-lookup"><span data-stu-id="22dd9-119">The design of an EDI system connecting two trading partners is determined by what the standards require, and what the trading partners agree upon.</span></span> <span data-ttu-id="22dd9-120">如需有關 EDI 傳訊的詳細資訊，請參閱[EDI 傳訊](../core/edi-messaging.md)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-120">For more information about EDI messaging, see [EDI Messaging](../core/edi-messaging.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22dd9-121">EDI 訊息與其傳輸不同。</span><span class="sxs-lookup"><span data-stu-id="22dd9-121">EDI messages are distinguished from their transport.</span></span> <span data-ttu-id="22dd9-122">EDI 標準並未規定訊息傳輸，因此 EDI 訊息可透過多種不同方式傳送。</span><span class="sxs-lookup"><span data-stu-id="22dd9-122">The EDI standards do not prescribe message transport, and EDI messages can be sent by a variety of different means.</span></span>  
  
## <a name="how-edi-is-implemented-in-biztalk-server"></a><span data-ttu-id="22dd9-123">在 BizTalk Server 中實作 EDI 的方式</span><span class="sxs-lookup"><span data-stu-id="22dd9-123">How EDI Is Implemented in BizTalk Server</span></span>  
 <span data-ttu-id="22dd9-124">BizTalk Server 會包含可提供 EDI 支援的原生功能。</span><span class="sxs-lookup"><span data-stu-id="22dd9-124">BizTalk Server includes native functionality that provides support for EDI.</span></span> <span data-ttu-id="22dd9-125">EDI 是內建在產品中。它不是增益集，例如配接器或加速器。</span><span class="sxs-lookup"><span data-stu-id="22dd9-125">EDI is built into the product; it is not an add-in, such as an adapter or an accelerator .</span></span>  
  
 <span data-ttu-id="22dd9-126">**交換處理**</span><span class="sxs-lookup"><span data-stu-id="22dd9-126">**Interchange Processing**</span></span>  
  
 <span data-ttu-id="22dd9-127">EDI 功能會在管線中執行下列接收端和傳送端處理，以強制執行 EDI 標準規定的規則。</span><span class="sxs-lookup"><span data-stu-id="22dd9-127">The EDI feature performs the following receive-side and send-side processing in pipelines that enforces the rules dictated by the EDI standards.</span></span>  
  
-   <span data-ttu-id="22dd9-128">處理內送 EDI 訊息，包括驗證交換 (Interchange) 和產生通知。</span><span class="sxs-lookup"><span data-stu-id="22dd9-128">Processes incoming EDI messages, including validating interchanges and generating acknowledgments.</span></span>  
  
-   <span data-ttu-id="22dd9-129">產生並傳送外寄 EDI 訊息，包括驗證交換 (Interchange) 和根據組態來處理收到的通知。</span><span class="sxs-lookup"><span data-stu-id="22dd9-129">Generates and sends outgoing EDI messages, including validating interchanges and processing received ACKs depending upon the configuration.</span></span>  
  
 <span data-ttu-id="22dd9-130">**批次處理**</span><span class="sxs-lookup"><span data-stu-id="22dd9-130">**Batch Processing**</span></span>  
  
 <span data-ttu-id="22dd9-131">批次處理作業是由接收管線和協調流程處理：</span><span class="sxs-lookup"><span data-stu-id="22dd9-131">Batch processing is handled by the receive pipeline and orchestration:</span></span>  
  
-   <span data-ttu-id="22dd9-132">如果收到的批次交換 (Interchange) 需要分割，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將其分割為組成交易集，包括為每個交易集產生 XML 檔案，以及升級產生傳送端批次所需的屬性。</span><span class="sxs-lookup"><span data-stu-id="22dd9-132">If a received batched interchange is to be split, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] splits it into its constituent transaction sets, generating an XML file for each transaction set and promoting properties required for send-side batch generation.</span></span>  
  
-   <span data-ttu-id="22dd9-133">如果收到的批次交換 (Interchange) 需要保留，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 處理批次時，會保留收到批次時該批次所包含的交易集和群組。</span><span class="sxs-lookup"><span data-stu-id="22dd9-133">If a received batched interchange is to be preserved, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the batch such that it retains the transaction sets and groups that it contained when the batch was received.</span></span>  
  
-   <span data-ttu-id="22dd9-134">如果收到的批次交換 (Interchange) 需要設定，批次會將 EDI 交換集和群組批次收到外寄交換 (Interchange) 中。</span><span class="sxs-lookup"><span data-stu-id="22dd9-134">If a received batched interchange is to be configured, batches receive EDI transaction sets and groups into an outgoing interchange.</span></span>  
  
-   <span data-ttu-id="22dd9-135">如有多個合作對象訂閱批次交換 (Interchange)，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會傳送批次副本給每個合作對象。</span><span class="sxs-lookup"><span data-stu-id="22dd9-135">If multiple parties subscribe to a batched interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends a copy of the batch to each party.</span></span>  
  
 <span data-ttu-id="22dd9-136">**交易夥伴協議**</span><span class="sxs-lookup"><span data-stu-id="22dd9-136">**Trading Partner Agreements**</span></span>  
  
 <span data-ttu-id="22dd9-137">交易夥伴必須互相定義「交易夥伴協議」，此協議是一組在「BizTalk Server 管理主控台」中定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="22dd9-137">Trading partners mutually define the Trading Partner Agreement which is a set of properties defined in the BizTalk Server Administration Console.</span></span> <span data-ttu-id="22dd9-138">這些合作對象屬性以及傳送和接收埠/位置屬性，決定接收端與傳送端 EDI 處理方式。</span><span class="sxs-lookup"><span data-stu-id="22dd9-138">These party properties, send and receive port/location properties, determine receive-side and send-side EDI processing.</span></span> <span data-ttu-id="22dd9-139">如需有關交易夥伴協議的詳細資訊，請參閱[交易夥伴協議](../core/trading-partner-agreement.md)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-139">For more information about trading partner agreements, see [Trading Partner Agreement](../core/trading-partner-agreement.md).</span></span>  
  
 <span data-ttu-id="22dd9-140">**交換狀態**</span><span class="sxs-lookup"><span data-stu-id="22dd9-140">**Interchange Status**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="22dd9-141"> 會提供 EDI 特定狀態報告。</span><span class="sxs-lookup"><span data-stu-id="22dd9-141"> provides EDI-specific status reporting.</span></span> <span data-ttu-id="22dd9-142">這些狀態報告會提供 EDI 文件交換 (Interchange) 交易的完整狀態，包括與交換 (Interchange) 相互關聯的通知。</span><span class="sxs-lookup"><span data-stu-id="22dd9-142">These status reports provide a comprehensive status of an EDI document exchange transaction, including acknowledgments correlated to the interchange.</span></span>  
  
## <a name="edi-components-in-biztalk-server"></a><span data-ttu-id="22dd9-143">BizTalk Server 中的 EDI 元件</span><span class="sxs-lookup"><span data-stu-id="22dd9-143">EDI Components in BizTalk Server</span></span>  
 <span data-ttu-id="22dd9-144">Microsoft BizTalk Server 元件用於 EDI 處理包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="22dd9-144">Microsoft BizTalk Server components used for EDI processing include the following:</span></span>  
  
-   <span data-ttu-id="22dd9-145">「BizTalk EDI 應用程式」包含處理 EDI 文件所需的成品 (包括管線、協調流程和結構描述)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-145">The BizTalk EDI Application contains artifacts (including pipelines, orchestrations, and schemas) that are needed to process EDI documents.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="22dd9-146">當您在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中設定 EDI 功能時，組態程式就會建立這個應用程式。</span><span class="sxs-lookup"><span data-stu-id="22dd9-146">When you configure the EDI feature in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the configuration program creates this application.</span></span> <span data-ttu-id="22dd9-147">每當您建立用於處理 EDI 交換 (Interchange) 的應用程式時，都必須在應用程式中加入「BizTalk EDI 應用程式」的參考。</span><span class="sxs-lookup"><span data-stu-id="22dd9-147">Whenever you create an application that will process EDI interchanges, you must add a reference to the BizTalk EDI Application from your application.</span></span> <span data-ttu-id="22dd9-148">如需詳細資訊，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-148">For more information, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
-   <span data-ttu-id="22dd9-149">「BizTalk EDI 接收管線」(EdiReceive 管線) 會剖析 EDI 編碼文件、分割 EDI 批次、將 EDI 編碼文件轉換為 XML 編碼、執行 EDI 和 XSD 驗證，以及執行 HIPAA X12 子文件分割作業。</span><span class="sxs-lookup"><span data-stu-id="22dd9-149">The BizTalk EDI Receive Pipeline (EdiReceive pipeline) parses EDI-encoded documents, splits EDI batches, converts the EDI-encoded documents into XML encoding, performs EDI and XSD validation, and performs HIPAA X12 sub-document splitting.</span></span> <span data-ttu-id="22dd9-150">如需詳細資訊，請參閱[EDI 接收元件](../core/edi-receive-components.md)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-150">For more information, see [EDI Receive Components](../core/edi-receive-components.md).</span></span>  
  
-   <span data-ttu-id="22dd9-151">「BizTalk EDI 傳送管線」(EdiSend 管線) 則會將 XML 文件轉換為 X12 或 EDIFACT 編碼、序列化 EDI 編碼文件，以及執行 EDI 和 XSD 驗證。</span><span class="sxs-lookup"><span data-stu-id="22dd9-151">The BizTalk EDI Send Pipeline (EdiSend pipeline) converts XML documents into X12 or EDIFACT encoding, serializes EDI-encoded documents, and performs EDI and XSD validation.</span></span> <span data-ttu-id="22dd9-152">如需詳細資訊，請參閱[EDI 傳送元件](../core/edi-send-components.md)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-152">For more information, see [EDI Send Components](../core/edi-send-components.md).</span></span>  
  
-   <span data-ttu-id="22dd9-153">交易夥伴管理 (TPM) 使用者介面可讓您設定參與 EDI 文件交換與 AS2 文件傳輸之交易夥伴的處理屬性。</span><span class="sxs-lookup"><span data-stu-id="22dd9-153">The Trading Partner Management (TPM) user interface enables you to set processing properties for trading partners engaging in EDI document exchange and AS2 document transport.</span></span> <span data-ttu-id="22dd9-154">如需詳細資訊，請參閱[中協議的角色中處理 EDI](../core/the-role-of-agreements-in-edi-processing.md)和**EDI 和 AS2 UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="22dd9-154">For more information, see [The Role of Agreements in EDI Processing](../core/the-role-of-agreements-in-edi-processing.md) and **EDI and AS2 UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
-   <span data-ttu-id="22dd9-155">批次處理協調流程會將 EDI 交換 (Interchange) 進行批次處理，並設定批次交換 (Interchange) 傳送的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="22dd9-155">The batching orchestration batches EDI interchanges and sets context properties for sending of the batched interchange.</span></span> <span data-ttu-id="22dd9-156">路由協調流程則會處理訊息符合多個批次的情況，並建立該訊息的必要副本數目。</span><span class="sxs-lookup"><span data-stu-id="22dd9-156">The routing orchestration handles the instances in which messages match multiple batches, creating as many copies of the message as required.</span></span> <span data-ttu-id="22dd9-157">如需詳細資訊，請參閱[處理內送批次](../core/processing-incoming-batches.md)和[批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-157">For more information, see [Processing Incoming Batches](../core/processing-incoming-batches.md) and [Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md).</span></span>  
  
-   <span data-ttu-id="22dd9-158">狀態報告使用者介面可提供 EDI 交換 (Interchange) 的完整狀態及相互關聯的通知。</span><span class="sxs-lookup"><span data-stu-id="22dd9-158">The status reporting user interface provides comprehensive status of EDI interchanges and correlated acknowledgments.</span></span> <span data-ttu-id="22dd9-159">如需詳細資訊，請參閱[EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-159">For more information, see [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md).</span></span>  
  
-   <span data-ttu-id="22dd9-160">Visual Studio 中的設計階段工具可讓您產生執行個體、驗證執行個體、驗證結構描述、測試對應以及驗證對應。</span><span class="sxs-lookup"><span data-stu-id="22dd9-160">Design time tools in Visual Studio enable you to generate an instance, validate an instance, validate a schema, test a map, and validating a map.</span></span> <span data-ttu-id="22dd9-161">如需詳細資訊，請參閱[使用設計階段 XML 工具](../core/using-design-time-xml-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-161">For more information, see [Using Design-Time XML Tools](../core/using-design-time-xml-tools.md).</span></span>  
  
-   <span data-ttu-id="22dd9-162">結構描述儲存機制包括 X12、EDIFACT、HIPAA X12N 4010A XSD、EANCOM 和控制結構描述。</span><span class="sxs-lookup"><span data-stu-id="22dd9-162">A schema repository includes X12, EDIFACT, HIPAA X12N 4010A XSD, EANCOM, and control schemas.</span></span> <span data-ttu-id="22dd9-163">如需詳細資訊，請參閱[EDI 文件結構描述支援](../core/edi-document-schema-support.md)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-163">For more information, see [EDI Document Schema Support](../core/edi-document-schema-support.md).</span></span>  
  
-   <span data-ttu-id="22dd9-164">移轉工具 （合作對象移轉工具） 可讓您將 EDI 合作對象資料從 BizTalk Server 2006 R2 或 BizTalk Server 2009 移轉至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="22dd9-164">A migration tool (Party Migration Tool) enables you to migrate EDI party data from BizTalk Server 2006 R2 or BizTalk Server 2009 to BizTalk Server.</span></span> <span data-ttu-id="22dd9-165">如需詳細資訊，請參閱[移轉 EDI 成品從 BizTalk Server 先前版本](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c)。</span><span class="sxs-lookup"><span data-stu-id="22dd9-165">For more information, see [Migrating EDI Artifacts from a Previous Version of BizTalk Server](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22dd9-166">請參閱</span><span class="sxs-lookup"><span data-stu-id="22dd9-166">See Also</span></span>  
 <span data-ttu-id="22dd9-167">[BizTalk Server 中的 EDI 處理](../core/edi-processing-in-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="22dd9-167">[EDI Processing in BizTalk Server](../core/edi-processing-in-biztalk-server.md) </span></span>  
 <span data-ttu-id="22dd9-168">[BizTalk Server 中的 HIPAA 支援](../core/hipaa-support-in-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="22dd9-168">[HIPAA Support in BizTalk Server](../core/hipaa-support-in-biztalk-server.md) </span></span>  
 <span data-ttu-id="22dd9-169">[EDI 支援問題](../core/edi-support-issues.md) </span><span class="sxs-lookup"><span data-stu-id="22dd9-169">[EDI Support Issues](../core/edi-support-issues.md) </span></span>  
 <span data-ttu-id="22dd9-170">[EDI 解決方案架構](../core/edi-solution-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="22dd9-170">[EDI Solution Architecture](../core/edi-solution-architecture.md) </span></span>  
 <span data-ttu-id="22dd9-171">[EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md) </span><span class="sxs-lookup"><span data-stu-id="22dd9-171">[EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md) </span></span>  
 [<span data-ttu-id="22dd9-172">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="22dd9-172">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)