---
title: 使用管線介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4bb88d0d-23ab-4fdb-bcd2-56050456cf69
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c365a8d7bdf37564d3d9b2dceac1c8615e126ebc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289142"
---
# <a name="using-pipeline-interfaces"></a><span data-ttu-id="cabd3-102">使用管線介面</span><span class="sxs-lookup"><span data-stu-id="cabd3-102">Using Pipeline Interfaces</span></span>
<span data-ttu-id="cabd3-103">管線元件是一種 .NET 或 COM 元件，會實作一組預先定義的介面，以便與 BizTalk 傳訊引擎進行互動。</span><span class="sxs-lookup"><span data-stu-id="cabd3-103">A pipeline component is a .NET or COM component that implements a set of predefined interfaces for interaction with the BizTalk Messaging Engine.</span></span> <span data-ttu-id="cabd3-104">取決於元件的功能，必須實作不同的介面。</span><span class="sxs-lookup"><span data-stu-id="cabd3-104">Depending on the functionality of the component, different interfaces must be implemented.</span></span> <span data-ttu-id="cabd3-105">本主題討論這些介面，以及其所具有的一些方法。</span><span class="sxs-lookup"><span data-stu-id="cabd3-105">This topic discusses these interfaces and some of their methods.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="cabd3-106">如果您使用 COM 建置自訂管線元件，必須設定元件以使用多執行緒 Apartment (MTA) 模型。</span><span class="sxs-lookup"><span data-stu-id="cabd3-106">If you are building a custom pipeline component using COM, you must configure your component to use the Multi-Threaded Apartment (MTA) model.</span></span> <span data-ttu-id="cabd3-107">否則，叫用您的元件便會造成具有 E_NOINTERFACE 錯誤的失敗。</span><span class="sxs-lookup"><span data-stu-id="cabd3-107">If you do not, invocation of your component will fail with an E_NOINTERFACE error.</span></span>  
  
## <a name="ipipelinecontext"></a><span data-ttu-id="cabd3-108">IPipelineContext</span><span class="sxs-lookup"><span data-stu-id="cabd3-108">IPipelineContext</span></span>  
 <span data-ttu-id="cabd3-109">所有的管線元件可以使用**IPipelineContext**來存取所有文件處理特定介面的方法。</span><span class="sxs-lookup"><span data-stu-id="cabd3-109">All pipeline components can use **IPipelineContext** methods to access all document processing-specific interfaces.</span></span> <span data-ttu-id="cabd3-110">**IPipelineContext**介面提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="cabd3-110">The **IPipelineContext** interface provides the following functionalities:</span></span>  
  
-   <span data-ttu-id="cabd3-111">讓元件能夠擷取環境管線和階段設定。</span><span class="sxs-lookup"><span data-stu-id="cabd3-111">Allows components to retrieve the ambient pipeline and stage settings.</span></span>  
  
-   <span data-ttu-id="cabd3-112">讓元件能夠擷取訊息和訊息 Factory。</span><span class="sxs-lookup"><span data-stu-id="cabd3-112">Allows components to retrieve message and message factories.</span></span> <span data-ttu-id="cabd3-113">運用這些 Factory，元件可以建立執行元件時所需要的各種物件。</span><span class="sxs-lookup"><span data-stu-id="cabd3-113">With these factories, components can create various objects required for the execution of the component.</span></span>  
  
-   <span data-ttu-id="cabd3-114">讓元件能夠擷取文件規格。</span><span class="sxs-lookup"><span data-stu-id="cabd3-114">Allows components to retrieve the document specifications.</span></span> <span data-ttu-id="cabd3-115">文件規格是 XSD 結構描述加上其他註釋。</span><span class="sxs-lookup"><span data-stu-id="cabd3-115">A document specification is an XSD schema plus additional annotations.</span></span>  
  
## <a name="ibasecomponent"></a><span data-ttu-id="cabd3-116">IBaseComponent</span><span class="sxs-lookup"><span data-stu-id="cabd3-116">IBaseComponent</span></span>  
 <span data-ttu-id="cabd3-117">所有管線元件都需要實作此介面以提供元件的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="cabd3-117">All pipeline components need to implement this interface to provide basic information about the component.</span></span>  
  
## <a name="icomponent"></a><span data-ttu-id="cabd3-118">IComponent</span><span class="sxs-lookup"><span data-stu-id="cabd3-118">IComponent</span></span>  
 <span data-ttu-id="cabd3-119">所有的管線元件 (組合器與解譯器除外) 都會實作此介面，以便從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 引擎取得訊息並加以處理，並將處理過的訊息傳回到引擎。</span><span class="sxs-lookup"><span data-stu-id="cabd3-119">All pipeline components except assemblers and disassemblers implement this interface to get messages from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine for processing and to pass processed messages back to the engine.</span></span>  
  
 <span data-ttu-id="cabd3-120">**執行。**</span><span class="sxs-lookup"><span data-stu-id="cabd3-120">**Execute.**</span></span> <span data-ttu-id="cabd3-121">由引擎呼叫的方法，將輸入訊息傳遞到元件，並從元件擷取處理過的訊息。</span><span class="sxs-lookup"><span data-stu-id="cabd3-121">Method called by the engine to pass the input message to the component and retrieve the processed message from the component.</span></span>  
  
## <a name="ipropertybag-ipersistpropertybag"></a><span data-ttu-id="cabd3-122">IpropertyBag、IPersistPropertyBag</span><span class="sxs-lookup"><span data-stu-id="cabd3-122">IPropertyBag, IPersistPropertyBag</span></span>  
 <span data-ttu-id="cabd3-123">管線元件必須實作**IPersistPropertyBag**接收其組態資訊。</span><span class="sxs-lookup"><span data-stu-id="cabd3-123">Pipeline components need to implement **IPersistPropertyBag** to receive its configuration information.</span></span> <span data-ttu-id="cabd3-124">這個介面和**IPropertyBag**是標準的介面。</span><span class="sxs-lookup"><span data-stu-id="cabd3-124">This interface and **IPropertyBag** are the standard interfaces.</span></span> <span data-ttu-id="cabd3-125">如需這些介面的詳細資訊，請參閱 Microsoft .NET Framework 軟體開發套件 (SDK) 文件。</span><span class="sxs-lookup"><span data-stu-id="cabd3-125">For more information about these interfaces, refer to the Microsoft .NET Framework Software Development Kit (SDK) documentation.</span></span>  
  
## <a name="idisassemblercomponent"></a><span data-ttu-id="cabd3-126">IDisassemblerComponent</span><span class="sxs-lookup"><span data-stu-id="cabd3-126">IDisassemblerComponent</span></span>  
 <span data-ttu-id="cabd3-127">解譯元件是一種管線元件，會在輸入時接收一個訊息，並在輸出時產生零個或多個訊息。</span><span class="sxs-lookup"><span data-stu-id="cabd3-127">A disassembling component is a pipeline component that receives one message on input and produces zero or more messages on output.</span></span> <span data-ttu-id="cabd3-128">解譯元件的用途是將交換的訊息分割成個別的文件。</span><span class="sxs-lookup"><span data-stu-id="cabd3-128">Disassembling components are used to split interchanges of messages into individual documents.</span></span> <span data-ttu-id="cabd3-129">解譯元件必須實作的方法**IDisassemblerComponent**介面，以取得訊息從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件進行處理，以及傳遞反組譯傳回到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cabd3-129">A disassembler component must implement the methods of the **IDisassemblerComponent** interface to get messages from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for processing and to pass disassembled documents back to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
|<span data-ttu-id="cabd3-130">方法</span><span class="sxs-lookup"><span data-stu-id="cabd3-130">Method</span></span>|<span data-ttu-id="cabd3-131">Description</span><span class="sxs-lookup"><span data-stu-id="cabd3-131">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cabd3-132">**反組譯**</span><span class="sxs-lookup"><span data-stu-id="cabd3-132">**Disassemble**</span></span>|<span data-ttu-id="cabd3-133">執行內送文件的解譯**pInMsg**。</span><span class="sxs-lookup"><span data-stu-id="cabd3-133">Performs the disassembling of the incoming document **pInMsg**.</span></span>|  
|<span data-ttu-id="cabd3-134">**GetNext**</span><span class="sxs-lookup"><span data-stu-id="cabd3-134">**GetNext**</span></span>|<span data-ttu-id="cabd3-135">從解譯器執行所產生的訊息集取得下一個訊息。</span><span class="sxs-lookup"><span data-stu-id="cabd3-135">Gets the next message from the message set that resulted from disassembler execution.</span></span> <span data-ttu-id="cabd3-136">傳回**NULL**是否有任何訊息。</span><span class="sxs-lookup"><span data-stu-id="cabd3-136">Returns **NULL** if there are no more messages.</span></span>|  
  
 <span data-ttu-id="cabd3-137">如果您撰寫的是支援「可復原交換處理」的解譯器元件，便必須進行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cabd3-137">If you are writing a disassembler component that will support Recoverable Interchange Processing, you must do the following:</span></span>  
  
1.  <span data-ttu-id="cabd3-138">將輸入資料流包裝在 VirtualStream() 中，使其變成可搜尋的。</span><span class="sxs-lookup"><span data-stu-id="cabd3-138">Make the input streams seekable by wrapping them in a VirtualStream().</span></span>  
  
2.  <span data-ttu-id="cabd3-139">在 GetNext() 中，讓邏輯判斷訊息何時錯誤。</span><span class="sxs-lookup"><span data-stu-id="cabd3-139">In GetNext(), have logic to determine when a message is bad.</span></span> <span data-ttu-id="cabd3-140">如果訊息錯誤，請設定 BTS.MessageDestination = "SuspendQueue"，並在 GetNext() 中傳回訊息。</span><span class="sxs-lookup"><span data-stu-id="cabd3-140">If a message is bad, set BTS.MessageDestination = "SuspendQueue" and return the message in GetNext().</span></span>  
  
3.  <span data-ttu-id="cabd3-141">如果訊息良好，請設定 BTS.SuspendMessageOnRoutingFailure = True，並在 GetNext() 中傳回訊息。</span><span class="sxs-lookup"><span data-stu-id="cabd3-141">If the message is good, set BTS.SuspendMessageOnRoutingFailure = True and return the message in GetNext().</span></span>  
  
## <a name="iassemblercomponent"></a><span data-ttu-id="cabd3-142">IAssemblerComponent</span><span class="sxs-lookup"><span data-stu-id="cabd3-142">IAssemblerComponent</span></span>  
 <span data-ttu-id="cabd3-143">組合元件是一種管線元件，會在輸入時接收數個訊息，並在輸出時產生一個訊息。</span><span class="sxs-lookup"><span data-stu-id="cabd3-143">An assembling component is a pipeline component that receives several messages on input and produces one message on output.</span></span> <span data-ttu-id="cabd3-144">組合元件的用途是將個別文件收集到訊息交換批次中。</span><span class="sxs-lookup"><span data-stu-id="cabd3-144">Assembling components are used to collect individual documents into the message interchange batch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cabd3-145">在這個版本的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中並沒有使用組合功能，因此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 永遠都會將一份文件傳遞到元件輸入。</span><span class="sxs-lookup"><span data-stu-id="cabd3-145">In this release of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], assembling functionality is not used, so [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] always passes one document to the component input.</span></span>  
  
 <span data-ttu-id="cabd3-146">組合元件實作**IAssemblerComponent**所呼叫的方法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]引擎在執行階段。</span><span class="sxs-lookup"><span data-stu-id="cabd3-146">An assembler component implements the **IAssemblerComponent** methods that are called by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine at run time.</span></span>  
  
|<span data-ttu-id="cabd3-147">方法</span><span class="sxs-lookup"><span data-stu-id="cabd3-147">Method</span></span>|<span data-ttu-id="cabd3-148">Description</span><span class="sxs-lookup"><span data-stu-id="cabd3-148">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cabd3-149">**AddDocument**</span><span class="sxs-lookup"><span data-stu-id="cabd3-149">**AddDocument**</span></span>|<span data-ttu-id="cabd3-150">新增的文件**pInMsg**會包含在交換的訊息清單。</span><span class="sxs-lookup"><span data-stu-id="cabd3-150">Adds the document **pInMsg** to the list of messages that will be included in the interchange.</span></span>|  
|<span data-ttu-id="cabd3-151">**組合**</span><span class="sxs-lookup"><span data-stu-id="cabd3-151">**Assemble**</span></span>|<span data-ttu-id="cabd3-152">從藉由上一個方法新增的訊息中建立交換。</span><span class="sxs-lookup"><span data-stu-id="cabd3-152">Builds the interchange from the messages that were added by the previous method.</span></span> <span data-ttu-id="cabd3-153">將指標傳回到組合的訊息。</span><span class="sxs-lookup"><span data-stu-id="cabd3-153">Returns a pointer to the assembled message.</span></span>|  
  
## <a name="iprobemessage"></a><span data-ttu-id="cabd3-154">IProbeMessage</span><span class="sxs-lookup"><span data-stu-id="cabd3-154">IProbeMessage</span></span>  
 <span data-ttu-id="cabd3-155">可實作任何管線元件 （一般、 組合或解譯） **IProbeMessage**是否需要訊息探查功能。</span><span class="sxs-lookup"><span data-stu-id="cabd3-155">Any pipeline component (general, assembling, or disassembling) can implement **IProbeMessage** if it requires message probing functionality.</span></span> <span data-ttu-id="cabd3-156">探查元件會用於具有管線階段**FirstMatch**執行模式。</span><span class="sxs-lookup"><span data-stu-id="cabd3-156">A probing component is used in the pipeline stages that have **FirstMatch** execution mode.</span></span> <span data-ttu-id="cabd3-157">在此種階段中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將訊息提供給元件，而**探查**方法會檢查以判斷該元件是否可識別訊息的格式訊息的開頭。</span><span class="sxs-lookup"><span data-stu-id="cabd3-157">In such stages, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] gives the message to the component, and the **Probe** method examines the beginning of the message to determine if the component recognizes the format of the message.</span></span>  
  
|<span data-ttu-id="cabd3-158">方法</span><span class="sxs-lookup"><span data-stu-id="cabd3-158">Method</span></span>|<span data-ttu-id="cabd3-159">Description</span><span class="sxs-lookup"><span data-stu-id="cabd3-159">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cabd3-160">**探查**</span><span class="sxs-lookup"><span data-stu-id="cabd3-160">**Probe**</span></span>|<span data-ttu-id="cabd3-161">這個方法會採用**pInMsg**訊息，並傳回**True**如果辨識的格式或**False**否則。</span><span class="sxs-lookup"><span data-stu-id="cabd3-161">This method takes **pInMsg** message, and returns **True** if the format is recognized or **False** otherwise.</span></span>|  
  
## <a name="inameditem"></a><span data-ttu-id="cabd3-162">INamedItem</span><span class="sxs-lookup"><span data-stu-id="cabd3-162">INamedItem</span></span>  
 <span data-ttu-id="cabd3-163">這是從 Managed 和 Unmanaged 程式碼存取文件結構描述的協助程式介面。</span><span class="sxs-lookup"><span data-stu-id="cabd3-163">This is a helper interface for accessing document schemas from managed and unmanaged code.</span></span>  
  
## <a name="inameditemlist"></a><span data-ttu-id="cabd3-164">INamedItemList</span><span class="sxs-lookup"><span data-stu-id="cabd3-164">INamedItemList</span></span>  
 <span data-ttu-id="cabd3-165">這是從 Managed 和 Unmanaged 程式碼存取文件結構描述的協助程式介面。</span><span class="sxs-lookup"><span data-stu-id="cabd3-165">This is a helper interface for accessing document schemas from managed and unmanaged code.</span></span>  
  
## <a name="idocumentspec"></a><span data-ttu-id="cabd3-166">IDocumentSpec</span><span class="sxs-lookup"><span data-stu-id="cabd3-166">IDocumentSpec</span></span>  
 <span data-ttu-id="cabd3-167">管線元件可以使用的方法**IDocumentSpec**介面來執行特定文件的動作，例如將內容屬性移至內容和回、 存取文件結構描述，並依此類推。</span><span class="sxs-lookup"><span data-stu-id="cabd3-167">Pipeline components can use methods of the **IDocumentSpec** interface to perform document-specific actions, such as moving content properties to context and back, accessing document schemas, and so on.</span></span>  
  
|<span data-ttu-id="cabd3-168">方法</span><span class="sxs-lookup"><span data-stu-id="cabd3-168">Method</span></span>|<span data-ttu-id="cabd3-169">Description</span><span class="sxs-lookup"><span data-stu-id="cabd3-169">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cabd3-170">**文件類型**</span><span class="sxs-lookup"><span data-stu-id="cabd3-170">**DocType**</span></span>|<span data-ttu-id="cabd3-171">傳回目前文件的類型。</span><span class="sxs-lookup"><span data-stu-id="cabd3-171">Returns the type of the current document.</span></span>|  
|<span data-ttu-id="cabd3-172">**DocSpecName**</span><span class="sxs-lookup"><span data-stu-id="cabd3-172">**DocSpecName**</span></span>|<span data-ttu-id="cabd3-173">傳回目前文件的規格名稱。</span><span class="sxs-lookup"><span data-stu-id="cabd3-173">Returns the specification name of the current document.</span></span>|  
|<span data-ttu-id="cabd3-174">**GetSchemaCollection**</span><span class="sxs-lookup"><span data-stu-id="cabd3-174">**GetSchemaCollection**</span></span>|<span data-ttu-id="cabd3-175">傳回目前文件之文件結構描述的清單。</span><span class="sxs-lookup"><span data-stu-id="cabd3-175">Returns the list of document schemas for the current document.</span></span>|  
|<span data-ttu-id="cabd3-176">**GetBodyPath**</span><span class="sxs-lookup"><span data-stu-id="cabd3-176">**GetBodyPath**</span></span>|<span data-ttu-id="cabd3-177">傳回文件中開始內文部分所在之節點的 XPath。</span><span class="sxs-lookup"><span data-stu-id="cabd3-177">Returns the XPath to the node in the document where the body part begins.</span></span>|  
|<span data-ttu-id="cabd3-178">**GetDistinguishedPropertyAnnotationEnumerator**</span><span class="sxs-lookup"><span data-stu-id="cabd3-178">**GetDistinguishedPropertyAnnotationEnumerator**</span></span>|<span data-ttu-id="cabd3-179">傳回所有辨別欄位屬性註釋的字典列舉程式。</span><span class="sxs-lookup"><span data-stu-id="cabd3-179">Returns a dictionary enumerator of all distinguished field property annotations.</span></span>|  
|<span data-ttu-id="cabd3-180">**GetPropertyAnnotationEnumerator**</span><span class="sxs-lookup"><span data-stu-id="cabd3-180">**GetPropertyAnnotationEnumerator**</span></span>|<span data-ttu-id="cabd3-181">傳回所有屬性註釋的列舉程式。</span><span class="sxs-lookup"><span data-stu-id="cabd3-181">Returns an enumerator of all property annotations.</span></span>|  
  
## <a name="icomponentui"></a><span data-ttu-id="cabd3-182">IComponentUI</span><span class="sxs-lookup"><span data-stu-id="cabd3-182">IComponentUI</span></span>  
 <span data-ttu-id="cabd3-183">管線元件必須實作此介面，以便在「管線設計師」環境內使用。</span><span class="sxs-lookup"><span data-stu-id="cabd3-183">Pipeline components must implement this interface to be used within the Pipeline Designer environment.</span></span>  
  
|<span data-ttu-id="cabd3-184">方法</span><span class="sxs-lookup"><span data-stu-id="cabd3-184">Method</span></span>|<span data-ttu-id="cabd3-185">Description</span><span class="sxs-lookup"><span data-stu-id="cabd3-185">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cabd3-186">**圖示**</span><span class="sxs-lookup"><span data-stu-id="cabd3-186">**Icon**</span></span>|<span data-ttu-id="cabd3-187">提供與此元件相關聯的圖示。</span><span class="sxs-lookup"><span data-stu-id="cabd3-187">Provides the icon that is associated with this component.</span></span>|  
|<span data-ttu-id="cabd3-188">**Validate**</span><span class="sxs-lookup"><span data-stu-id="cabd3-188">**Validate**</span></span>|<span data-ttu-id="cabd3-189">[管線設計師] 會在管線編譯前呼叫此方法，以確認有正確設定所有的組態屬性。</span><span class="sxs-lookup"><span data-stu-id="cabd3-189">Pipeline Designer calls this method before pipeline compilation to verify that all the configuration properties are set correctly.</span></span>|  
  
 <span data-ttu-id="cabd3-190">**圖示**屬性會傳回**IntPtr**。</span><span class="sxs-lookup"><span data-stu-id="cabd3-190">The **Icon** property returns an **IntPtr**.</span></span> <span data-ttu-id="cabd3-191">下列 C# 範例示範如何傳回**IntPtr**。</span><span class="sxs-lookup"><span data-stu-id="cabd3-191">The following C# example shows how to return an **IntPtr**.</span></span>  
  
```csharp  
static   ResourceManager resManager = new ResourceManager("ResourceManager", Assembly.GetExecutingAssembly());  
...  
[Browsable(false)]  
public IntPtr Icon  
{  
   get  
   {  
      return ((Bitmap)resManager.GetObject("MyIcon")).GetHicon();  
   }  
}  
```  
  
 <span data-ttu-id="cabd3-192">如需詳細資訊，請參閱**IComponentUI 介面 (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="cabd3-192">For more information, see **IComponentUI Interface (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="cabd3-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cabd3-193">See Also</span></span>  
 <span data-ttu-id="cabd3-194">[開發自訂管線元件](../core/developing-custom-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="cabd3-194">[Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md) </span></span>  
 [<span data-ttu-id="cabd3-195">CustomComponent （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="cabd3-195">CustomComponent (BizTalk Server Sample)</span></span>](../core/customcomponent-biztalk-server-sample.md)