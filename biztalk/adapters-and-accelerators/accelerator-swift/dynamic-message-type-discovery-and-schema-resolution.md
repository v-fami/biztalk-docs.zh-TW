---
title: 動態訊息類型探索和解析結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic schema resolution
- disassembler, code sample
- schemas, dynamic resolution
- assembler, message types
- disassembler, message types
- code samples, disassembler
ms.assetid: 5f71d3df-a37e-4ef2-9055-b614656203e9
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5bbc5f8afaa8c08da04e9eab1b476e5884b2e6f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986407"
---
# <a name="dynamic-message-type-discovery-and-schema-resolution"></a><span data-ttu-id="1b664-102">動態訊息類型探索和結構描述解析</span><span class="sxs-lookup"><span data-stu-id="1b664-102">Dynamic Message Type Discovery and Schema Resolution</span></span>
<span data-ttu-id="1b664-103">Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]實現動態訊息類型探索和結構描述解析 SWIFT 解譯器和組合器中的。</span><span class="sxs-lookup"><span data-stu-id="1b664-103">Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] enables dynamic message type discovery and schema resolution in both the SWIFT disassembler and assembler.</span></span>  
  
## <a name="swift-disassembler"></a><span data-ttu-id="1b664-104">SWIFT 解譯器</span><span class="sxs-lookup"><span data-stu-id="1b664-104">SWIFT Disassembler</span></span>  
 <span data-ttu-id="1b664-105">SWIFT 解譯器 (DASM) 具有動態探索接收訊息的訊息類型，並載入適當的結構描述來剖析訊息所需的能力。</span><span class="sxs-lookup"><span data-stu-id="1b664-105">The SWIFT disassembler (DASM) has the ability to dynamically discover the message type of a received message and load the appropriate schema needed to parse the message.</span></span> <span data-ttu-id="1b664-106">這項功能的最大優點是，您可以設定單一管線來處理任何 SWIFT 的訊息類型的 SWIFT 訊息使用 SWIFT 解譯器。</span><span class="sxs-lookup"><span data-stu-id="1b664-106">The greatest benefit of this feature is that you can configure a single pipeline using the SWIFT disassembler to process SWIFT messages of any SWIFT message type.</span></span> <span data-ttu-id="1b664-107">不同於原生 BizTalk 一般檔案解譯器，SWIFT 解譯器不需要您建立個別的接收管線 A4SWIFT 可能會遇到每種訊息類型。</span><span class="sxs-lookup"><span data-stu-id="1b664-107">Unlike the native BizTalk flat-file disassembler, the SWIFT disassembler does not require that you build a separate receive pipeline for each message type that A4SWIFT might encounter.</span></span>  
  
 <span data-ttu-id="1b664-108">如果您假設，在大部分情況下，系統會接收的所有訊息的都開頭結構同質性的標頭資料，您可以使用動態訊息類型探索。</span><span class="sxs-lookup"><span data-stu-id="1b664-108">You can use dynamic message type discovery if you assume that, in most cases, all messages that a system receives will begin with structurally homogeneous header data.</span></span> <span data-ttu-id="1b664-109">標頭內的資料會顯示訊息的訊息類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="1b664-109">Within the header data are fields that reveal the message type of the message.</span></span> <span data-ttu-id="1b664-110">SWIFT 的訊息標頭資料包含 SWIFT 訊息區塊 1、 2 和 3，以包含在區塊 （稱為應用程式標頭） 的 2 的訊息型別資訊。</span><span class="sxs-lookup"><span data-stu-id="1b664-110">For SWIFT messages, header data consists of SWIFT message blocks 1, 2, and 3, with message type information contained in block 2 (known as the Application Header).</span></span>  
  
 <span data-ttu-id="1b664-111">SWIFT DASM 元件可以處理所有 「 單一 」 （非批次） SWIFT 訊息根據預設，而不需要任何設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="1b664-111">The SWIFT DASM component can process all "single" (non-batched) SWIFT Messages out of the box without requiring any of the properties to be set.</span></span> <span data-ttu-id="1b664-112">根據預設的 SWIFT 交換的結構描述和 SWIFT 標頭結構描述未設定;不過，SWIFT DASM 元件會使用存在於 Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll SWIFT 標頭結構描述，來動態偵測 SWIFT 訊息類型，並處理訊息。</span><span class="sxs-lookup"><span data-stu-id="1b664-112">By default, the SWIFT Interchange Schema and SWIFT Header schema are not set; however, the SWIFT DASM component will use the SWIFT Header schema present in Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll to detect the SWIFT Message Type dynamically and process the messages.</span></span> <span data-ttu-id="1b664-113">此外，BRE 」 和 「 XML 驗證會預設啟用以便處理任何訊息將會完整驗證。</span><span class="sxs-lookup"><span data-stu-id="1b664-113">Also, BRE and XML Validation are enabled by default so any message that is processed will be completely validated.</span></span> <span data-ttu-id="1b664-114">SWIFT 標頭結構描述屬性設定為指向 RuntimeSchemas.dll SWIFT 標頭也會與上述相同的行為。</span><span class="sxs-lookup"><span data-stu-id="1b664-114">Setting the SWIFT Header schema property to point to the SWIFT Header in RuntimeSchemas.dll will also result in the same behavior as above.</span></span>  
  
 <span data-ttu-id="1b664-115">當 SWIFT 解譯器的 SWIFT 標頭結構描述的組態屬性設定為"None"（預設值） 時，解譯器動態解析，並載入適當的結構描述，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1b664-115">When the SWIFT Header Schema configuration property for the SWIFT disassembler is set to "None" (the default), the disassembler dynamically resolves and loads the appropriate schema by performing the following steps:</span></span>  
  
1. <span data-ttu-id="1b664-116">您可以使用 （SWIFT 標頭結構描述的組態屬性所指定） 的使用者指定的標頭結構描述，剖析接收訊息的開頭 （標頭）。</span><span class="sxs-lookup"><span data-stu-id="1b664-116">Uses the user-specified header schema (specified by the SWIFT Header Schema configuration property) to parse the beginning (header) of the receive message.</span></span>  
  
2. <span data-ttu-id="1b664-117">會產生 「 標頭 XML 」 檢查 A4SWIFT_MessageType 升級的屬性欄位。</span><span class="sxs-lookup"><span data-stu-id="1b664-117">Inspects the resulting "header XML" for the A4SWIFT_MessageType promoted property field.</span></span> <span data-ttu-id="1b664-118">如果此欄位存在，它會使用的欄位值為 「 訊息類型 」，並繼續進行步驟 4。</span><span class="sxs-lookup"><span data-stu-id="1b664-118">If this field exists, it uses the field value as the "message type" and proceeds to Step 4.</span></span> <span data-ttu-id="1b664-119">如果欄位不存在，便會繼續進行步驟 3。</span><span class="sxs-lookup"><span data-stu-id="1b664-119">If the field does not exist, it proceeds to Step 3.</span></span>  
  
3. <span data-ttu-id="1b664-120">會檢查 A4SWIFT_MessageType2 升級的屬性欄位的標頭 XML （預期如果解譯器找不到 A4SWIFT_MessageType 欄位）。</span><span class="sxs-lookup"><span data-stu-id="1b664-120">Inspects the header XML for the A4SWIFT_MessageType2 promoted property field (expected if the disassembler does not find the A4SWIFT_MessageType field).</span></span> <span data-ttu-id="1b664-121">使用 A4SWIFT_MessageType2 欄位值做為 「 訊息類型 」。</span><span class="sxs-lookup"><span data-stu-id="1b664-121">Uses the A4SWIFT_MessageType2 field value as the "message type".</span></span>  
  
4. <span data-ttu-id="1b664-122">如果 「 574"的 「 訊息類型 」 在步驟 2 或 3 中識別，SWIFT 解譯器會檢查訊息類型"574 」 是否雙重類型的訊息清單組態屬性 （這是屬性的反組譯工具） 中指定的訊息類型的清單中。</span><span class="sxs-lookup"><span data-stu-id="1b664-122">If the "message type" identified in Step 2 or 3 is "574", the SWIFT disassembler checks if the message type "574" is in the list of message types specified in the Dual Type Message List configuration property (which is a property of the disassembler).</span></span> <span data-ttu-id="1b664-123">如果是，它會繼續進行步驟 5。</span><span class="sxs-lookup"><span data-stu-id="1b664-123">If yes, it proceeds to Step 5.</span></span> <span data-ttu-id="1b664-124">若為否，則會繼續進行步驟 6。</span><span class="sxs-lookup"><span data-stu-id="1b664-124">If no, proceeds to Step 6.</span></span>  
  
5. <span data-ttu-id="1b664-125">會檢查 A4SWIFT_SecondaryMessageType 升級的屬性欄位的 XML 標頭。</span><span class="sxs-lookup"><span data-stu-id="1b664-125">Inspects header XML for the A4SWIFT_SecondaryMessageType promoted property field.</span></span> <span data-ttu-id="1b664-126">如果此欄位存在時，解譯器會使用 「 訊息子類型為"的欄位值 (例如，"IRSLST 」)，並將其附加至 「 訊息類型 」，比方說，「 574_IRSLST"。</span><span class="sxs-lookup"><span data-stu-id="1b664-126">If this field exists, the disassembler uses the field value (for example, "IRSLST") as the "message sub-type" and appends it to the "message type", for example, "574_IRSLST".</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="1b664-127">步驟 5 所提供的說明是簡化的 SWIFT 解譯器實際用途來評估訊息的子類型。</span><span class="sxs-lookup"><span data-stu-id="1b664-127">The explanation given for Step 5 is a simplification of what the SWIFT disassembler actually does to evaluate message sub-type.</span></span> <span data-ttu-id="1b664-128">實際上，SWIFT 解譯器會使用以下演算法以判斷訊息類型具有子類型，且如果是這樣，哪些的子類型，如下所示。</span><span class="sxs-lookup"><span data-stu-id="1b664-128">In actuality, the SWIFT disassembler uses the following algorithm to determine if a message type has sub-types, and if so, what that sub-type is as follows.</span></span>  
  
   ```  
   Given MT type number nxx ...  
   if nxx is in the Dual-Type list {  
     if field 119 exists AND field 119 is NOT null/empty {  
       if n == 1 {  
         if field 119 == "STP" {  
           Use MTnxxPLUS schema  
         } else if field 119 == "REMIT" {  
           Use MTnxx schema  
         } else {  
           Use MTnxx_<field 119> schema  
         }   
       } else {  
         // n != 1  
         Use MTnxx_<field 119> schema  
       }  
     } else {  
       // field 119 does not exist or 119 does exist but is null/empty  
       Use MTnxx schema  
     }  
   } else {  
     // nxx is not a dual-type message  
     Use MTnxx schema  
   }  
   ```  
  
6. <span data-ttu-id="1b664-129">反組譯工具現在知道訊息類型，並以形成交換結構描述名稱串連一些固定的結構描述命名前置詞和尾碼 （例如"MT"前置詞中讓 「 MT574_IRSLST")。</span><span class="sxs-lookup"><span data-stu-id="1b664-129">The disassembler now knows the message type, and it can form the interchange schema name by concatenating some fixed schema naming prefixes and suffixes (such as "MT" in the prefix to make "MT574_IRSLST").</span></span>  
  
7. <span data-ttu-id="1b664-130">載入交換結構描述 （依名稱），並剖析整個訊息，**從頭開始**，使用載入的結構描述 (這表示解譯器剖析的標頭資料兩次： 一次使用標頭的結構描述，並再次使用交換結構描述的開頭）。</span><span class="sxs-lookup"><span data-stu-id="1b664-130">Loads the interchange schema (by name) and parses the entire message, **starting from the beginning**, using the loaded schema (this means that the disassembler parses the header data twice: once using the header schema, and again using the beginning of the interchange schema).</span></span> <span data-ttu-id="1b664-131">交換結構描述必須是能夠剖析整個訊息，包括標頭。</span><span class="sxs-lookup"><span data-stu-id="1b664-131">The interchange schema must be able to parse the entire message, including the header.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="1b664-132">反組譯工具可以使用所有 A4SWIFT SWIFT 訊息結構描述來剖析整個 SWIFT 交換 （1、 2、 3、 4 和 5 SWIFT 區塊）。</span><span class="sxs-lookup"><span data-stu-id="1b664-132">The disassembler can use all A4SWIFT SWIFT message schemas to parse the entire SWIFT interchange (SWIFT blocks 1, 2, 3, 4, and 5).</span></span> <span data-ttu-id="1b664-133">解譯器會剖析區塊 1、 2 和 3 只使用預設 SWIFT 標頭結構描述。</span><span class="sxs-lookup"><span data-stu-id="1b664-133">The disassembler uses the default SWIFT header schema to parse blocks 1, 2, and 3 only.</span></span> <span data-ttu-id="1b664-134">如需詳細資訊，請參閱後文。</span><span class="sxs-lookup"><span data-stu-id="1b664-134">See below for details.</span></span>  
  
   <span data-ttu-id="1b664-135">上面所述的結構描述解析演算法表示，為了讓動態訊息類型探索才能運作，SWIFT 標頭結構描述必須包含解譯器已升級使用下列的升級的屬性 （在 A4SWIFT 中定義的欄位屬性結構描述，Microsoft.Solutions.A4SWIFT.Property.PropertySchema）：</span><span class="sxs-lookup"><span data-stu-id="1b664-135">The schema resolution algorithm described above implies that in order for dynamic message type discovery to work, the SWIFT Header Schema must contain fields that the disassembler has promoted using the following promoted properties (defined in the A4SWIFT Property Schema, Microsoft.Solutions.A4SWIFT.Property.PropertySchema):</span></span>  
  
- <span data-ttu-id="1b664-136">**A4SWIFT_MessageType**</span><span class="sxs-lookup"><span data-stu-id="1b664-136">**A4SWIFT_MessageType**</span></span>  
  
- <span data-ttu-id="1b664-137">**A4SWIFT_MessageType2** (若**A4SWIFT_MessageTypes**用)</span><span class="sxs-lookup"><span data-stu-id="1b664-137">**A4SWIFT_MessageType2** (optional if **A4SWIFT_MessageTypes** is used)</span></span>  
  
- <span data-ttu-id="1b664-138">**A4SWIFT_SecondaryMessageType** （選擇性）</span><span class="sxs-lookup"><span data-stu-id="1b664-138">**A4SWIFT_SecondaryMessageType** (optional)</span></span>  
  
  <span data-ttu-id="1b664-139">如需有關這些和其他升級的屬性的詳細資訊，請參閱 < [A4SWIFT_ \* 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1b664-139">For more information about these and other promoted properties, see [A4SWIFT_\* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b664-140">如果您將設定 SWIFT 標頭結構描述**無**，您應該指定完整的交換結構描述**SWIFT 交換結構描述**屬性。</span><span class="sxs-lookup"><span data-stu-id="1b664-140">If you set the SWIFT Header Schema to **None**, you should specify a complete interchange schema for the **SWIFT Interchange Schema** property.</span></span> <span data-ttu-id="1b664-141">在此情況下，解譯器會使用指定的交換結構描述來剖析 A4SWIFT 接收的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="1b664-141">In this case, the disassembler uses the specified interchange schema to parse all messages that A4SWIFT receives.</span></span> <span data-ttu-id="1b664-142">也就是您要停用動態結構描述解析，並設定管線來接收其類型符合指定的交換結構描述的訊息。</span><span class="sxs-lookup"><span data-stu-id="1b664-142">That is, you disable dynamic schema resolution and configure the pipeline to receive only messages whose type matches the specified interchange schema.</span></span>  
  
 <span data-ttu-id="1b664-143">A4SWIFT 安裝的預設 SWIFT 標頭結構描述 (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema)，可以剖析 SWIFT 的標準標頭資料，並具備必要的升級的屬性，以便動態結構描述解析。</span><span class="sxs-lookup"><span data-stu-id="1b664-143">A4SWIFT installs a default SWIFT header schema (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema) that can parse SWIFT standard header data and has the necessary promoted properties to facilitate dynamic schema resolution.</span></span>  
  
 <span data-ttu-id="1b664-144">預設的 SWIFT 標頭結構描述有下列的升級的欄位：</span><span class="sxs-lookup"><span data-stu-id="1b664-144">The default SWIFT header schema has the following promoted fields:</span></span>  
  
- <span data-ttu-id="1b664-145">**SWIFTHeader/ApplicationHeaderBlock_Input/MessageType**。</span><span class="sxs-lookup"><span data-stu-id="1b664-145">**SWIFTHeader/ApplicationHeaderBlock_Input/MessageType**.</span></span> <span data-ttu-id="1b664-146">解譯器將其升級使用**A4SWIFT_MessageType**屬性。</span><span class="sxs-lookup"><span data-stu-id="1b664-146">The disassembler promotes this using the **A4SWIFT_MessageType** property.</span></span>  
  
- <span data-ttu-id="1b664-147">**SWIFTHeader/ApplicationHeaderBlock_Output/MessageType**。</span><span class="sxs-lookup"><span data-stu-id="1b664-147">**SWIFTHeader/ApplicationHeaderBlock_Output/MessageType**.</span></span> <span data-ttu-id="1b664-148">解譯器將其升級使用**A4SWIFT_MessageType2**屬性。</span><span class="sxs-lookup"><span data-stu-id="1b664-148">The disassembler promotes this using the **A4SWIFT_MessageType2** property.</span></span>  
  
- <span data-ttu-id="1b664-149">**SWIFTHeader/UserHeaderBlock/ValidationFlag_119**。</span><span class="sxs-lookup"><span data-stu-id="1b664-149">**SWIFTHeader/UserHeaderBlock/ValidationFlag_119**.</span></span> <span data-ttu-id="1b664-150">解譯器將其升級使用**A4SWIFT_MessageType**屬性。</span><span class="sxs-lookup"><span data-stu-id="1b664-150">The disassembler promotes this using the **A4SWIFT_MessageType** property.</span></span>  
  
  <span data-ttu-id="1b664-151">解譯器會使用**Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema**標頭結構描述，如果您將 SWIFT 標頭結構描述和 SWIFT 交換的結構描述組態屬性設為預設 「None"。</span><span class="sxs-lookup"><span data-stu-id="1b664-151">The disassembler uses **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema** by default as the header schema if you set both SWIFT Header Schema and SWIFT Interchange Schema configuration properties to "None".</span></span>  
  
## <a name="swift-assembler"></a><span data-ttu-id="1b664-152">SWIFT 組合器</span><span class="sxs-lookup"><span data-stu-id="1b664-152">SWIFT Assembler</span></span>  
 <span data-ttu-id="1b664-153">SWIFT 解譯器，例如 SWIFT 組合器能夠動態探索輸出訊息的訊息類型，並載入序列化訊息所需的適當結構描述。</span><span class="sxs-lookup"><span data-stu-id="1b664-153">Like the SWIFT disassembler, the SWIFT assembler has the ability to dynamically discover the message type of an outbound message and load the appropriate schema needed to serialize the message.</span></span> <span data-ttu-id="1b664-154">這項功能可讓您設定單一管線來處理任何 SWIFT 的訊息類型的 SWIFT 訊息使用 SWIFT 組合器。</span><span class="sxs-lookup"><span data-stu-id="1b664-154">This feature enables you to configure a single pipeline using the SWIFT assembler to process SWIFT messages of any SWIFT message type.</span></span> <span data-ttu-id="1b664-155">不同於原生的 BizTalk 一般檔案組合器 SWIFT 組合器不需要您建立個別的傳送管線 A4SWIFT 可能會遇到每種訊息類型。</span><span class="sxs-lookup"><span data-stu-id="1b664-155">Unlike the native BizTalk flat-file assembler, the SWIFT assembler does not require you to build a separate send pipeline for each message type that A4SWIFT might encounter.</span></span>  
  
 <span data-ttu-id="1b664-156">SWIFT 組合器中的動態結構描述解析會比 SWIFT 解譯器中更簡單，因為 「 組合器 」 會將 XML 序列化回至 SWIFT 的一般檔案格式的工作。</span><span class="sxs-lookup"><span data-stu-id="1b664-156">Dynamic schema resolution in the SWIFT assembler is much simpler than in the SWIFT disassembler because the assembler does the job of serializing XML back into SWIFT flat-file format.</span></span> <span data-ttu-id="1b664-157">XML 的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]讓 SWIFT 組合器序列化包含訊息類型和結構描述資訊，其中 SWIFT 組合器可以直接使用來載入適當的結構描述進行序列化。</span><span class="sxs-lookup"><span data-stu-id="1b664-157">The XML that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] gives to the SWIFT assembler for serialization contains the message type and schema information, which the SWIFT assembler can use directly to load the appropriate schema for serialization.</span></span> <span data-ttu-id="1b664-158">因此，SWIFT 組合器並沒有任何可設定性的標頭和交換的結構描述： 一律會使用指定的結構描述的 XML 中，它會序列化。</span><span class="sxs-lookup"><span data-stu-id="1b664-158">As such, the SWIFT assembler does not have any configurability for header and interchange schemas: it always uses the schema specified in the XML that it will serialize.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b664-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b664-159">See Also</span></span>  
 [<span data-ttu-id="1b664-160">使用 SWIFT 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="1b664-160">Working with the SWIFT Disassembler and Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)