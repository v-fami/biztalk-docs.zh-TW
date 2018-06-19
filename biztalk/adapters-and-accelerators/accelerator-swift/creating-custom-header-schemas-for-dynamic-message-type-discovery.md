---
title: 建立動態的訊息類型探索自訂標頭結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, dynamic resolution
- schemas, message types
- schemas, custom headers
- header schemas
ms.assetid: 0c936c57-b533-47ca-9258-576b021fd016
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c87ba83961b9daac07028a994d7c01add0c11a73
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26004327"
---
# <a name="creating-custom-header-schemas-for-dynamic-message-type-discovery"></a><span data-ttu-id="9ecc0-102">建立自訂標頭結構描述的訊息動態類型探索</span><span class="sxs-lookup"><span data-stu-id="9ecc0-102">Creating Custom Header Schemas for Dynamic Message Type Discovery</span></span>
<span data-ttu-id="9ecc0-103">在大部分情況下，您應該指定預設 SWIFT 的標頭結構描述 (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema) SWIFT 解譯器的 SWIFT 標頭結構描述組態屬性。</span><span class="sxs-lookup"><span data-stu-id="9ecc0-103">In most scenarios, you should specify the default SWIFT header schema (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema) for the SWIFT Header Schema configuration property of the SWIFT disassembler.</span></span> <span data-ttu-id="9ecc0-104">SWIFT 解譯器會使用預設 SWIFT 的標頭結構描述剖析訊息標頭符合 SWIFT 標準規格，並具有所需之升級屬性，以便動態結構描述解析 （和 「 雙重類型 」 的子型別解析SWIFT 的訊息，例如 MT574_IRSLST 與 MT574_W8BENO）。</span><span class="sxs-lookup"><span data-stu-id="9ecc0-104">The SWIFT disassembler uses the default SWIFT header schema to parse message headers that conform to the SWIFT standard specification, and has the necessary promoted properties to facilitate dynamic schema resolution (and sub-type resolution for "dual type" SWIFT messages like MT574_IRSLST and MT574_W8BENO).</span></span> <span data-ttu-id="9ecc0-105">如需有關預設 SWIFT 的標頭結構描述，以及了解 SWIFT 解譯器的結構描述解析的執行方式的詳細資訊，請參閱[動態的訊息類型探索和結構描述解析](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="9ecc0-105">For more information about the default SWIFT header schema and to understand how the SWIFT disassembler performs schema resolution, see [Dynamic Message Type Discovery and Schema Resolution](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md).</span></span>  
  
 <span data-ttu-id="9ecc0-106">其他情況下，其中的訊息包含非 SWIFT 標準標頭資料，您可以使用自訂標頭結構描述剖析標頭和訊息動態類型探索。</span><span class="sxs-lookup"><span data-stu-id="9ecc0-106">For other scenarios where messages contain non-SWIFT standard header data, you can use a custom header schema for header parsing and dynamic message type discovery.</span></span> <span data-ttu-id="9ecc0-107">若要建立和自訂標頭結構描述用於動態結構描述解析，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="9ecc0-107">To create and use a custom header schema for dynamic schema resolution, do the following:</span></span>  
  
1.  <span data-ttu-id="9ecc0-108">建立自訂的結構描述 SWIFT 解譯器可讓結構上剖析預期的標頭資料格式。</span><span class="sxs-lookup"><span data-stu-id="9ecc0-108">Create a custom schema that the SWIFT disassembler can use to structurally parse the expected header data format.</span></span>  
  
2.  <span data-ttu-id="9ecc0-109">識別結構描述中的哪些欄位會保留的值，指出訊息類型。</span><span class="sxs-lookup"><span data-stu-id="9ecc0-109">Identify which fields in the schema will hold the value(s) indicating message type.</span></span>  
  
3.  <span data-ttu-id="9ecc0-110">將 A4SWIFT 屬性結構描述 (Microsoft.Solutions.A4SWIFT.Property.PropertySchema) 加入至屬性結構描述之 「 清單 」 的自訂標頭結構描述，並將升級的適當欄位，以指出訊息類型，使用下列[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]屬性：</span><span class="sxs-lookup"><span data-stu-id="9ecc0-110">Add the A4SWIFT Property Schema (Microsoft.Solutions.A4SWIFT.Property.PropertySchema) to the "Property schemas list" of the custom header schema and promote the appropriate fields that indicate message type using the following [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] properties:</span></span>  
  
    -   <span data-ttu-id="9ecc0-111">**A4SWIFT_MessageType**</span><span class="sxs-lookup"><span data-stu-id="9ecc0-111">**A4SWIFT_MessageType**</span></span>  
  
    -   <span data-ttu-id="9ecc0-112">**A4SWIFT_MessageType2** (選擇性若**A4SWIFT_MessageTypes**用)</span><span class="sxs-lookup"><span data-stu-id="9ecc0-112">**A4SWIFT_MessageType2** (optional if **A4SWIFT_MessageTypes** is used)</span></span>  
  
    -   <span data-ttu-id="9ecc0-113">**A4SWIFT_SecondaryMessageType** （選擇性）</span><span class="sxs-lookup"><span data-stu-id="9ecc0-113">**A4SWIFT_SecondaryMessageType** (optional)</span></span>  
  
4.  <span data-ttu-id="9ecc0-114">建置和部署自訂標頭結構描述。</span><span class="sxs-lookup"><span data-stu-id="9ecc0-114">Build and deploy the custom header schema.</span></span>  
  
5.  <span data-ttu-id="9ecc0-115">SWIFT 標頭結構描述組態屬性設 SWIFT 解譯器 （在接收管線專案） 中的自訂標頭結構描述。</span><span class="sxs-lookup"><span data-stu-id="9ecc0-115">Set the SWIFT Header Schema configuration property of the SWIFT disassembler (in your receive pipeline project) to the custom header schema.</span></span>  
  
 <span data-ttu-id="9ecc0-116">如需有關這些和其他升級的屬性的詳細資訊，請參閱[A4SWIFT_ \* 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9ecc0-116">For more information about these and other promoted properties, see [A4SWIFT_\* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).</span></span> <span data-ttu-id="9ecc0-117">如需有關如何使用 BizTalk 編輯器來建立和編輯結構描述、 使用屬性結構描述升級屬性，建置和部署結構描述專案的詳細資訊，請參閱 BizTalk Server 說明。</span><span class="sxs-lookup"><span data-stu-id="9ecc0-117">For more information about using BizTalk Editor to create and edit schemas, promote properties using a property schema, and build and deploy schema projects, see BizTalk Server Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ecc0-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="9ecc0-118">See Also</span></span>  
 [<span data-ttu-id="9ecc0-119">使用 SWIFT 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="9ecc0-119">Working with the SWIFT Disassembler and Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)