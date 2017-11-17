---
title: "SWIFT 的標頭和結尾結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trailer schemas
- schemas, headers
- schemas, trailers
- header schemas
ms.assetid: 82cd33d4-6bbb-4124-9506-fd35b5dca8a4
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8f3cb45e14a7c7e900fc26a4cbc8fcfb5d7b66e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="swift-header-and-trailer-schemas"></a><span data-ttu-id="67ba0-102">SWIFT 的標頭和結尾結構描述</span><span class="sxs-lookup"><span data-stu-id="67ba0-102">SWIFT Header and Trailer Schemas</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="67ba0-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]提供 SWIFT 標頭和結尾結構描述。</span><span class="sxs-lookup"><span data-stu-id="67ba0-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides the SWIFT header and trailer schemas.</span></span> <span data-ttu-id="67ba0-104">A4SWIFT 已經已納入這些各種 FIN 訊息交換的結構描述。</span><span class="sxs-lookup"><span data-stu-id="67ba0-104">A4SWIFT has already incorporated these into the interchange schemas for the various FIN messages.</span></span> <span data-ttu-id="67ba0-105">如果您想要建立自訂 SWIFT FIN 格式樣式訊息類型 （例如，N98 訊息），您可以在標頭和結尾結構描述併入您自己的格式。</span><span class="sxs-lookup"><span data-stu-id="67ba0-105">If you want to create a custom SWIFT FIN format style message type (for example, an N98 message), you can incorporate the header and trailer schemas into your own format.</span></span>  
  
 <span data-ttu-id="67ba0-106">SWIFT 的標頭結構描述 (SWIFT Header.xsd) 包含下列格式：</span><span class="sxs-lookup"><span data-stu-id="67ba0-106">The SWIFT header schema (SWIFT Header.xsd) contains the formats for the following:</span></span>  
  
-   <span data-ttu-id="67ba0-107">基本的標頭</span><span class="sxs-lookup"><span data-stu-id="67ba0-107">Basic Header</span></span>  
  
-   <span data-ttu-id="67ba0-108">應用程式標頭 （選擇輸入或輸出）</span><span class="sxs-lookup"><span data-stu-id="67ba0-108">Application Header (choice of Input or Output)</span></span>  
  
-   <span data-ttu-id="67ba0-109">使用者標頭</span><span class="sxs-lookup"><span data-stu-id="67ba0-109">User Header</span></span>  
  
-   <span data-ttu-id="67ba0-110">文字區塊的起始分隔符號</span><span class="sxs-lookup"><span data-stu-id="67ba0-110">Beginning delimiter of the text block</span></span>  
  
 <span data-ttu-id="67ba0-111">基本的標頭包含屬於訊息來源之相關資訊。</span><span class="sxs-lookup"><span data-stu-id="67ba0-111">The Basic Header contains information about the source of the message.</span></span> <span data-ttu-id="67ba0-112">應用程式標頭包含訊息類型和訊息的目的地的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="67ba0-112">The Application Header contains information about the message type and the destination of the message.</span></span> <span data-ttu-id="67ba0-113">SWIFT 的解譯器，接收管線中的訊息類型解析根據適當的應用程式標頭中欄位的內容。</span><span class="sxs-lookup"><span data-stu-id="67ba0-113">The resolution of the message type by the SWIFT disassembler in a receive pipeline is based upon the contents of the field in the appropriate Application Header.</span></span> <span data-ttu-id="67ba0-114">使用者標頭是選擇性的並包含特殊的處理指示。</span><span class="sxs-lookup"><span data-stu-id="67ba0-114">The User Header is optional, and contains special processing instructions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67ba0-115">少數的訊息類型會顯示變數的格式欄位 119 使用者標頭中的內容為基礎。</span><span class="sxs-lookup"><span data-stu-id="67ba0-115">A few message types have variable formats based upon the contents of field 119 in the User Header.</span></span> <span data-ttu-id="67ba0-116">這些是在 A4SWIFT 的 「 雙重訊息類型 」。</span><span class="sxs-lookup"><span data-stu-id="67ba0-116">These are "dual message types" in A4SWIFT.</span></span> <span data-ttu-id="67ba0-117">A4SWIFT 解譯器使用應用程式中的標頭搭配 119 欄位的內容中的訊息類型，選取適當的結構描述的訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="67ba0-117">The A4SWIFT disassembler uses the message type in the Application Header in conjunction with the contents of field 119 to select the appropriate schema for a message instance.</span></span>  
  
 <span data-ttu-id="67ba0-118">*SWIFT 使用者手冊*，這是 SWIFT FIN 服務文件的部分描述所有這些標頭。</span><span class="sxs-lookup"><span data-stu-id="67ba0-118">The *SWIFT User Handbook*, which is part of the SWIFT documentation for the FIN service, describes all of these headers.</span></span>  
  
 <span data-ttu-id="67ba0-119">文字區塊的開頭是"{4: 」 後面接著歸位字元和換行字元。</span><span class="sxs-lookup"><span data-stu-id="67ba0-119">The beginning of the text block is "{4:" followed by a carriage return and line feed.</span></span> <span data-ttu-id="67ba0-120">需要文字區塊的開頭。</span><span class="sxs-lookup"><span data-stu-id="67ba0-120">The beginning of the text block is required.</span></span>  
  
 <span data-ttu-id="67ba0-121">為了要考慮處理 （剖析及驗證） 的交換包含只 SWIFT 區塊 4，交換結構描述中的所有標頭和結尾區塊會標示為選擇性。</span><span class="sxs-lookup"><span data-stu-id="67ba0-121">In order to accommodate processing (parsing and validation) of interchanges containing only SWIFT block 4, all header and trailer blocks in the interchange schemas are marked as optional.</span></span> <span data-ttu-id="67ba0-122">這偏離 SWIFT FIN 規格，其中基本的標頭區塊 1 和 2 應用程式標頭區塊是強制性。</span><span class="sxs-lookup"><span data-stu-id="67ba0-122">This deviates from the SWIFT FIN specification, where the Basic Header block 1 and the Application Header block 2 are mandatory.</span></span> <span data-ttu-id="67ba0-123">這可讓您使用交換的結構描述來處理不要求標頭的訊息。</span><span class="sxs-lookup"><span data-stu-id="67ba0-123">This enables you to use the interchange schema to handle messages that do not require headers.</span></span> <span data-ttu-id="67ba0-124">例如，如果您接受透過 FileAct 收到的訊息，批次標頭可能包含訊息，以及一般的訊息類型的來源。</span><span class="sxs-lookup"><span data-stu-id="67ba0-124">For example, if you are accepting messages received through FileAct, the batch header may contain the source of the messages as well as a common message type.</span></span>  
  
 <span data-ttu-id="67ba0-125">執行階段結構描述 DLL 也包含標頭結構描述。</span><span class="sxs-lookup"><span data-stu-id="67ba0-125">The RunTime schema DLL also includes the header schema.</span></span> <span data-ttu-id="67ba0-126">A4SWIFT 安裝部署執行階段結構描述 DLL 和 A4SWIFT 屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="67ba0-126">A4SWIFT installation deploys the RunTime schema DLL and the A4SWIFT property schema.</span></span> <span data-ttu-id="67ba0-127">如果您需要使用您自己的標頭，以便進行處理，您可以定義和部署自訂標頭結構描述，並將升級訊息解析為適當的屬性。</span><span class="sxs-lookup"><span data-stu-id="67ba0-127">If you need to use your own header for processing, you can define and deploy a custom header schema, and promote the appropriate properties for message resolution.</span></span> <span data-ttu-id="67ba0-128">如果您這樣做，您也必須指定新的標頭 SWIFT 解譯器 (DASM)。</span><span class="sxs-lookup"><span data-stu-id="67ba0-128">If you do so, you will also need to specify the new header to the SWIFT disassembler (DASM).</span></span> <span data-ttu-id="67ba0-129">自訂標頭結構描述不應該有相同的文件類型為 SWIFT 標頭結構描述該 A4SWIFT 安裝已部署在執行階段結構描述 DLL 中。</span><span class="sxs-lookup"><span data-stu-id="67ba0-129">The custom header schema should not have the same Document Type as the SWIFT header schema that A4SWIFT installation has deployed in the RunTime schemas DLL.</span></span> <span data-ttu-id="67ba0-130">請務必變更結構描述命名空間或根節點名稱，或兩者。</span><span class="sxs-lookup"><span data-stu-id="67ba0-130">Be sure to change the schema namespace, or root node name, or both.</span></span>  
  
 <span data-ttu-id="67ba0-131">SWIFT 結尾結構描述 (**SWIFT Trailer.xsd**) 包含下列格式：</span><span class="sxs-lookup"><span data-stu-id="67ba0-131">The SWIFT Trailer schema (**SWIFT Trailer.xsd**) contains the format for the following:</span></span>  
  
-   <span data-ttu-id="67ba0-132">文字區塊的結尾分隔字元</span><span class="sxs-lookup"><span data-stu-id="67ba0-132">Ending delimiter of the text block</span></span>  
  
-   <span data-ttu-id="67ba0-133">使用者結尾 （使用者和系統資訊）</span><span class="sxs-lookup"><span data-stu-id="67ba0-133">User trailers (user and system information)</span></span>  
  
-   <span data-ttu-id="67ba0-134">系統結尾</span><span class="sxs-lookup"><span data-stu-id="67ba0-134">System trailers</span></span>  
  
 <span data-ttu-id="67ba0-135">文字區塊的結束分隔符號是"-"}。</span><span class="sxs-lookup"><span data-stu-id="67ba0-135">The ending delimiter of the text block is "-}".</span></span> <span data-ttu-id="67ba0-136">結尾區塊的開頭"{5:"。</span><span class="sxs-lookup"><span data-stu-id="67ba0-136">The trailer block begins with "{5:".</span></span> <span data-ttu-id="67ba0-137">結尾區塊的內容會包含使用者資訊 （總和檢查碼、 訊息驗證，專屬的驗證，等等） 和系統資訊 （延遲的訊息，訊息參考，可能重複的訊息，以及等等）。</span><span class="sxs-lookup"><span data-stu-id="67ba0-137">The contents of the trailer block include both user information (checksum, message authentication, proprietary authentication, and so on) and system information (delayed message, message reference, possible duplicate message, and so on).</span></span> <span data-ttu-id="67ba0-138">SWIFT 所加入的結尾也提供第三個區塊，以分隔"{S"。</span><span class="sxs-lookup"><span data-stu-id="67ba0-138">Trailers added by SWIFT also provide a third block, delimited by "{S:".</span></span> <span data-ttu-id="67ba0-139">*SWIFT 使用者手冊*，在 [尋找服務描述]，詳細說明區塊 5 的內容。</span><span class="sxs-lookup"><span data-stu-id="67ba0-139">The *SWIFT User Handbook*, under "FIN Service Description", describes in detail the contents of block 5.</span></span> <span data-ttu-id="67ba0-140">A4SWIFT 不會驗證 s 區塊的內容</span><span class="sxs-lookup"><span data-stu-id="67ba0-140">A4SWIFT does not validate the contents of block S.</span></span>  
  
 <span data-ttu-id="67ba0-141">實際的 FIN 介面或 SWIFT 網路將附加至結尾。</span><span class="sxs-lookup"><span data-stu-id="67ba0-141">The actual FIN interface or the SWIFT network appends the trailers.</span></span> <span data-ttu-id="67ba0-142">如果訊息包含結尾 A4SWIFT 接收訊息時，A4SWIFT 會有訊息結尾。</span><span class="sxs-lookup"><span data-stu-id="67ba0-142">If a message contains a trailer when A4SWIFT receives the message, A4SWIFT carries the trailer with the message.</span></span> <span data-ttu-id="67ba0-143">如果訊息沒有結尾 A4SWIFT 接收訊息時，A4SWIFT 就不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="67ba0-143">A4SWIFT does not raise an error if a message does not contain a trailer when A4SWIFT receives the message.</span></span> <span data-ttu-id="67ba0-144">做為標頭與結尾的項目，包括區塊本身，均 A4SWIFT 的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="67ba0-144">As with headers, all of the trailer entries, including the blocks themselves, are optional in A4SWIFT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ba0-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67ba0-145">See Also</span></span>  
 [<span data-ttu-id="67ba0-146">使用結構描述</span><span class="sxs-lookup"><span data-stu-id="67ba0-146">Working with Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)