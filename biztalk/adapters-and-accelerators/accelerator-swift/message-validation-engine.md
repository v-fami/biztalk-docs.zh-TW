---
title: 訊息驗證引擎 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message validation engine
- errors, validating
- XML validation
- parsing validation
- BRE policies, validating
- errors, messages
- messages, errors
- validating, messages
- validating, BRE policies
- validating, XML
- messages, validating
- validating, errors
- validating, parsing
ms.assetid: 4ba0b75e-665b-4771-b04f-5bc3e90d83f0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbdcb375c04e4c9684b2a805c7a7a7315f46f83d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209030"
---
# <a name="message-validation-engine"></a><span data-ttu-id="ce5f8-102">訊息驗證引擎</span><span class="sxs-lookup"><span data-stu-id="ce5f8-102">Message Validation Engine</span></span>
<span data-ttu-id="ce5f8-103">所提供的最重要功能的其中一個[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]是完整驗證 SWIFT 接收從後端系統的 SWIFT 網路，或從 SWIFT （交易夥伴所傳送） 的網路接收的訊息的能力。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-103">One of the most important features provided by [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] is the ability to fully validate SWIFT messages received from back-end systems destined for the SWIFT network, or received from the SWIFT network (sent by trading partners).</span></span> <span data-ttu-id="ce5f8-104">驗證輸出 SWIFT 訊息保證的訊息符合 SWIFT 標準和 SWIFT 網路不會拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-104">Validating outbound SWIFT messages guarantees that the messages conform to SWIFT standards and that the SWIFT network will not reject the messages.</span></span>  
  
 <span data-ttu-id="ce5f8-105">驗證輸入 SWIFT 訊息可確保從其他金融機構接收的訊息會遵循特定協議 （商務規則） 特定的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-105">Validating inbound SWIFT messages ensures that messages received from other financial institutions obey particular agreements (business rules) specific to the relationship.</span></span> <span data-ttu-id="ce5f8-106">在這兩種情況下，有助於降低交易成本和總擁有成本 (TCO) 驗證，並且設陷錯誤，再認可訊息的能力。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-106">In both scenarios, the ability to validate and trap errors before committing a message helps to reduce transaction costs and total cost of ownership (TCO).</span></span>  
  
 <span data-ttu-id="ce5f8-107">下列清單說明組成 A4SWIFT 驗證引擎的四個部分：</span><span class="sxs-lookup"><span data-stu-id="ce5f8-107">The following list describes the four parts that make up the A4SWIFT validation engine:</span></span>  
  
-   <span data-ttu-id="ce5f8-108">一般檔案剖析器所執行的結構化驗證</span><span class="sxs-lookup"><span data-stu-id="ce5f8-108">Structural validation performed by the flat file parser</span></span>  
  
-   <span data-ttu-id="ce5f8-109">XML 驗證讀取器所執行的資料驗證</span><span class="sxs-lookup"><span data-stu-id="ce5f8-109">Data validation performed by the XML validating reader</span></span>  
  
-   <span data-ttu-id="ce5f8-110">執行商務規則引擎 (BRE) 的 SWIFT 網路和使用方式規則驗證</span><span class="sxs-lookup"><span data-stu-id="ce5f8-110">SWIFT network and usage rule validation performed by the Business Rule Engine (BRE)</span></span>  
  
-   <span data-ttu-id="ce5f8-111">訊息標記與收集的 「 盡力 」 時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="ce5f8-111">Message marking and "best effort" error collecting</span></span>  
  
## <a name="structural-validation-parsing"></a><span data-ttu-id="ce5f8-112">（剖析） 的結構化驗證</span><span class="sxs-lookup"><span data-stu-id="ce5f8-112">Structural Validation (Parsing)</span></span>  
 <span data-ttu-id="ce5f8-113">A4SWIFT 剖析 SWIFT 標準根據每個 SWIFT 訊息類型所定義的 XSD 結構描述的 SWIFT 的一般檔案訊息。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-113">A4SWIFT parses SWIFT flat file messages against XSD schemas defined for each SWIFT message type in accordance with the SWIFT standard.</span></span> <span data-ttu-id="ce5f8-114">將一般檔案剖析為 XML 可保證，一般檔案結構正確。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-114">Parsing a flat file into XML guarantees that the flat file is structurally correct.</span></span> <span data-ttu-id="ce5f8-115">剖析時，也會產生更輕鬆地讀取、 操作或轉換成其他格式或訊息類型的 XML。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-115">Parsing also produces XML that is easier to read, manipulate, or transform into other formats or message types.</span></span> <span data-ttu-id="ce5f8-116">您也可以針對資料有效性的結構描述驗證 XML，並使用更複雜的評估商務規則引擎 (BRE)。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-116">You can also validate the XML against schema for data validity and use the Business Rule Engine (BRE) for more complex evaluations.</span></span>  
  
 <span data-ttu-id="ce5f8-117">SWIFT 解譯器會叫用 BizTalk 一般檔案剖析器剖析 SWIFT 解譯器所叫用的 SWIFT 的一般檔案訊息。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-117">The SWIFT disassembler invokes the BizTalk flat file parser to parse SWIFT flat file messages invoked by the SWIFT disassembler.</span></span> <span data-ttu-id="ce5f8-118">SWIFT 的解譯器中的錯誤集合會記錄在剖析期間發生的任何錯誤的詳細資料，並一律會嘗試繼續剖析為了儘可能收集多結構的錯誤，在第一階段中的資料。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-118">The SWIFT disassembler records in an error collection the details of any errors encountered during parsing, and always attempts to continue parsing the data in an effort to collect as many structural errors as possible on the first pass.</span></span> <span data-ttu-id="ce5f8-119">不過，大部分的剖析錯誤嚴重並停止在第一個錯誤的訊息處理。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-119">However, most parse errors are fatal and halt message processing at the first error.</span></span>  
  
 <span data-ttu-id="ce5f8-120">如需結構化驗證的詳細資訊，請參閱[使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-120">For more information about structural validation, see [Working with Schemas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md).</span></span>  
  
## <a name="data-validation-xml-validation"></a><span data-ttu-id="ce5f8-121">資料驗證 （XML 驗證）</span><span class="sxs-lookup"><span data-stu-id="ce5f8-121">Data Validation (XML Validation)</span></span>  
 <span data-ttu-id="ce5f8-122">您可以定義符合定義 XSD 結構描述做為格式正確的 XML 傳遞結構化驗證的 SWIFT 訊息。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-122">You can define SWIFT messages that pass structural validation as well-formed XML conforming to defined XSD schemas.</span></span> <span data-ttu-id="ce5f8-123">A4SWIFT 會在剖析階段期間產生的結構上有效的 SWIFT 訊息的 XML。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-123">A4SWIFT produces XML for structurally valid SWIFT messages during the parsing stage.</span></span> <span data-ttu-id="ce5f8-124">A4SWIFT 可以接著會驗證此 XML 資料的正確性，針對對應 XSD 結構描述中定義的條件約束。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-124">A4SWIFT can then validate this XML for data correctness against constraints defined in the corresponding XSD schema.</span></span>  
  
 <span data-ttu-id="ce5f8-125">這些條件約束包括資料輸入、 長度和標準 SWIFT 依據定義的值範圍。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-125">These constraints include data typing, length, and value ranges defined in accordance with the SWIFT standard.</span></span> <span data-ttu-id="ce5f8-126">SWIFT 解譯器會叫用驗證讀取器來執行資料驗證的 XML。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-126">The SWIFT disassembler invokes the XML validating reader to perform data validation.</span></span>  
  
 <span data-ttu-id="ce5f8-127">SWIFT 解譯器會記錄錯誤集合中的 XML 驗證期間發生的錯誤詳細資料，並繼續驗證要儘可能收集最多的 XML 驗證錯誤，在第一階段的剩餘資料。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-127">The SWIFT disassembler records in an error collection the details of any errors encountered during XML validation, and continues validating the remaining data to collect as many XML validation errors as possible on the first pass.</span></span> <span data-ttu-id="ce5f8-128">（不同於剖析時，接續的 XML 驗證不會保證。）</span><span class="sxs-lookup"><span data-stu-id="ce5f8-128">(Unlike parsing, continuation of XML validation is guaranteed.)</span></span>  
  
 <span data-ttu-id="ce5f8-129">如需詳細資料驗證的詳細資訊，請參閱[使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-129">For more information about data validation, see [Working with Schemas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md).</span></span>  
  
## <a name="swift-network-and-usage-rule-validation-bre-validation"></a><span data-ttu-id="ce5f8-130">SWIFT 網路和使用方式規則驗證 （BRE 驗證）</span><span class="sxs-lookup"><span data-stu-id="ce5f8-130">SWIFT Network and Usage Rule Validation (BRE Validation)</span></span>  
 <span data-ttu-id="ce5f8-131">A4SWIFT 驗證 XML 結構上有效的 SWIFT 訊息的商務層級，根據商務規則引擎 (BRE) 原則的正確性。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-131">A4SWIFT validates XML for structurally valid SWIFT messages for business-level correctness against Business Rule Engine (BRE) policies.</span></span> <span data-ttu-id="ce5f8-132">這些原則包括強制執行 SWIFT 網路和使用方式的規則和其他複雜的跨欄位規則，依據 SWIFT 的標準定義。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-132">These policies include enforcement of SWIFT network and usage rules and other complex cross-field rules defined in accordance with the SWIFT standard.</span></span> <span data-ttu-id="ce5f8-133">SWIFT 解譯器會叫用 BRE 執行商業層級驗證。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-133">The SWIFT disassembler invokes the BRE to perform business-level validation.</span></span>  
  
 <span data-ttu-id="ce5f8-134">SWIFT 解譯器會記錄錯誤集合中的 BRE 驗證期間發生的錯誤詳細資料，並繼續驗證要儘可能收集最多的 BRE 驗證錯誤，在第一階段的剩餘資料。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-134">The SWIFT disassembler records in an error collection the details of any errors encountered during BRE validation, and continues validating the remaining data to collect as many BRE validation errors as possible on the first pass.</span></span> <span data-ttu-id="ce5f8-135">（如同 XML 驗證，接續的 BRE 驗證保證。）</span><span class="sxs-lookup"><span data-stu-id="ce5f8-135">(Like XML validation, continuation of BRE validation is guaranteed.)</span></span>  
  
 <span data-ttu-id="ce5f8-136">如需 SWIFT 網路和使用方式的規則驗證的詳細資訊，請參閱[使用 BRE 原則](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md)。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-136">For more information about SWIFT network and usage rule validation, see [Working with BRE Policies](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md).</span></span>  
  
## <a name="validation-failures-and-message-marking"></a><span data-ttu-id="ce5f8-137">驗證失敗，訊息標記</span><span class="sxs-lookup"><span data-stu-id="ce5f8-137">Validation Failures and Message Marking</span></span>  
 <span data-ttu-id="ce5f8-138">A4SWIFT 收集驗證錯誤，以及透過訊息驗證的每個階段的詳細資料： 剖析結構化 XML 驗證，BRE 驗證。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-138">A4SWIFT collects validation errors and details through each stage of message validation: structural parsing, XML validation, and BRE validation.</span></span> <span data-ttu-id="ce5f8-139">A4SWIFT 收集來收集錯誤相關資訊訊息盡可能使用 「 盡力 」 啟發學習法這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-139">A4SWIFT collects these errors using a "best effort" heuristic to gather as much error information about a message as possible.</span></span> <span data-ttu-id="ce5f8-140">這項功能可讓失敗的訊息，找出的所有錯誤，然後再回報一次，而不是需要的送出，多個反覆項目驗證、 失敗、 修正，再重新送出。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-140">This functionality allows a failing message to have all errors caught and reported in one pass rather than having multiple iterations of submit, validate, fail, fix, resubmit.</span></span>  
  
 <span data-ttu-id="ce5f8-141">至少一個錯誤集合中的任何驗證階段期間發生的錯誤訊息會被視為無效，而且會失敗。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-141">Messages that have at least one error encountered during any validation stage in the error collection are considered invalid and are failed.</span></span> <span data-ttu-id="ce5f8-142">A4SWIFT 將這些訊息發佈到 MessageBox 資料庫，但它們就會標示，表示訊息已驗證失敗的升級屬性，報表的每個驗證階段的錯誤計數。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-142">A4SWIFT publishes these messages to the MessageBox database, but they are marked with promoted properties to indicate that the message has failed validation and to report error counts for each validation stage.</span></span>  
  
 <span data-ttu-id="ce5f8-143">提升的屬性，除了 A4SWIFT 序列化成 XML 的錯誤集合，並將 「 錯誤 」 的一部分多部分訊息的集合附加。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-143">In addition to the promoted properties, A4SWIFT serializes the error collection into XML and attaches the collection as an "error part" of the multipart message.</span></span> <span data-ttu-id="ce5f8-144">最後的訊息包含失敗的訊息內文部分中和錯誤組件中的錯誤集合 XML 及增強 A4SWIFT 升級屬性，以指出失敗狀態。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-144">The final message consists of the failed message in the body part and error-collection XML in the error part, and is enhanced with A4SWIFT promoted properties that indicate a failure state.</span></span> <span data-ttu-id="ce5f8-145">SWIFT 解譯器會將此多部分訊息發佈到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-145">The SWIFT disassembler publishes this multipart message to the MessageBox database.</span></span>  
  
 <span data-ttu-id="ce5f8-146">BizTalk 傳送埠或協調流程可以擷取失敗的訊息從 MessageBox 資料庫訂閱特殊 A4SWIFT 升級屬性。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-146">BizTalk send ports or orchestrations can retrieve failed messages from the MessageBox database by subscribing to the special A4SWIFT promoted properties.</span></span> <span data-ttu-id="ce5f8-147">您可以將訂用帳戶來擷取特定的驗證階段的所有失敗的訊息或只使用特定數目的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-147">You can make subscriptions to retrieve all failed messages or only messages with a particular number of errors from specific validation stages.</span></span>  
  
 <span data-ttu-id="ce5f8-148">擷取失敗的訊息之後，您可以將它傳送給報表的應用程式、 修復應用程式或處理序或失敗的儲存機制，或您可以將它捨棄。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-148">After a failed message is retrieved, you can send it to a reporting application, a repair application or process, or a failure repository, or you can discard it.</span></span>  
  
 <span data-ttu-id="ce5f8-149">這項功能訂閱失敗的訊息 （和區分其他部分類型的訂用帳戶中的失敗），搭配豐富資訊的錯誤集合附加至每個失敗的訊息的 XML 表單強大的架構來開發簡單的錯誤報告應用程式，例如提供訊息修復和新送出功能 A4SWIFT 安裝程式安裝。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-149">This ability to subscribe to failed messages (and to differentiate between types of failures in the subscription), coupled with information-rich error collection XML attached to each failed message, forms a powerful framework for developing simple error reporting applications, such as provided by the message repair and new submission feature installed by A4SWIFT setup.</span></span>  
  
 <span data-ttu-id="ce5f8-150">如需驗證失敗並標示為訊息的詳細資訊，請參閱[處理失敗的訊息訂閱](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="ce5f8-150">For more information about validation failures and message marking, see [Working with Failed Message Subscriptions](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce5f8-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce5f8-151">See Also</span></span>  
 [<span data-ttu-id="ce5f8-152">BizTalk Accelerator for SWIFT 的執行階段</span><span class="sxs-lookup"><span data-stu-id="ce5f8-152">BizTalk Accelerator for SWIFT Runtime</span></span>](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)