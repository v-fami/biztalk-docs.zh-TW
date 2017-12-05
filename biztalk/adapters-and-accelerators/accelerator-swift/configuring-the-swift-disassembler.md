---
title: "設定 SWIFT 解譯器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, disassembler
- disassembler, configuring
ms.assetid: f3773781-7412-421c-943c-18cc665da8d9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26147924950a73b0f654531e9e0eff8e5ac82541
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-the-swift-disassembler"></a><span data-ttu-id="221cf-102">設定 SWIFT 反組譯工具</span><span class="sxs-lookup"><span data-stu-id="221cf-102">Configuring the SWIFT Disassembler</span></span>
<span data-ttu-id="221cf-103">SWIFT 的解譯器 (DASM) 執行下列工作，當您叫用在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收管線：</span><span class="sxs-lookup"><span data-stu-id="221cf-103">The SWIFT disassembler (DASM) performs the following tasks when you invoke it in a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive pipeline:</span></span>  
  
-   <span data-ttu-id="221cf-104">動態探索訊息類型，並解析文件結構描述</span><span class="sxs-lookup"><span data-stu-id="221cf-104">Dynamically discovers the message type and resolves the document schema</span></span>  
  
-   <span data-ttu-id="221cf-105">將 SWIFT 的一般檔案剖析為 XML</span><span class="sxs-lookup"><span data-stu-id="221cf-105">Parses SWIFT flat files into XML</span></span>  
  
-   <span data-ttu-id="221cf-106">叫用驗證讀取器執行 XML （結構描述） 驗證的 XML</span><span class="sxs-lookup"><span data-stu-id="221cf-106">Invokes the XML validating reader to perform XML (schema) validation</span></span>  
  
-   <span data-ttu-id="221cf-107">叫用來執行 BRE 驗證商務規則引擎 (BRE)</span><span class="sxs-lookup"><span data-stu-id="221cf-107">Invokes the Business Rule Engine (BRE) to perform BRE validation</span></span>  
  
-   <span data-ttu-id="221cf-108">將剖析的 XML 訊息發佈到 MessageBox 資料庫的升級的內容屬性與序列化的錯誤集合 XML</span><span class="sxs-lookup"><span data-stu-id="221cf-108">Publishes a parsed XML message to the MessageBox database with promoted context properties and serialized error collection XML</span></span>  
  
-   <span data-ttu-id="221cf-109">處理程序輸入批次</span><span class="sxs-lookup"><span data-stu-id="221cf-109">Processes inbound batches</span></span>  
  
 <span data-ttu-id="221cf-110">您可以設定以符合使用者案例的特定需求，上面所列的功能和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]方案。</span><span class="sxs-lookup"><span data-stu-id="221cf-110">You can configure the functionality listed above to meet the specific requirements for a user scenario and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] solution.</span></span>  
  
 <span data-ttu-id="221cf-111">BizTalk 管線設計師 」 的自訂接收管線開發期間設定 SWIFT 解譯器。</span><span class="sxs-lookup"><span data-stu-id="221cf-111">BizTalk Pipeline Designer configures the SWIFT disassembler during development time of the custom receive pipeline.</span></span>  
  
 <span data-ttu-id="221cf-112">若要加入自訂接收管線的解譯階段之後，請設定 SWIFT 解譯器，選取 BizTalk 管線設計工具畫布上的 SWIFT 的解譯器元件。</span><span class="sxs-lookup"><span data-stu-id="221cf-112">To configure the SWIFT disassembler after it has been added to the disassemble stage of a custom receive pipeline, select the SWIFT disassembler component on the BizTalk Pipeline Designer canvas.</span></span> <span data-ttu-id="221cf-113">SWIFT 解譯器就會接收焦點，因此您可以設定其組態屬性，使用 [屬性] 視窗內[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="221cf-113">The SWIFT disassembler then receives focus and you can set its configuration properties using the Properties window within [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)].</span></span>  
  
 <span data-ttu-id="221cf-114">可用的設定屬性及其描述和使用方式詳細資料的資料表，請參閱[SWIFT 解譯器組態屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="221cf-114">For a table of available configuration properties and their descriptions and usage details, see [SWIFT Disassembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md).</span></span>  
  
 <span data-ttu-id="221cf-115">針對不同的案例使用 SWIFT 解譯器和設定組態屬性的相關資訊，請參閱[SWIFT 解譯器和組合器使用](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)。</span><span class="sxs-lookup"><span data-stu-id="221cf-115">For information about using the SWIFT disassembler for different scenarios and setting the configuration properties, see [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span></span>  
  
 <span data-ttu-id="221cf-116">當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]編譯二進位，它以靜態方式寫入自訂管線的組態設定的自訂管線。</span><span class="sxs-lookup"><span data-stu-id="221cf-116">When [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] compiles the custom pipeline binary, it statically writes the configuration settings to the custom pipeline.</span></span> <span data-ttu-id="221cf-117">因此，您無法在部署期間變更的組態屬性，或執行階段。</span><span class="sxs-lookup"><span data-stu-id="221cf-117">Therefore, you cannot change configuration properties during deployment or run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="221cf-118">設定、 編譯及部署自訂的管線之後，組態中的變更需要重新編譯和重新部署自訂管線。</span><span class="sxs-lookup"><span data-stu-id="221cf-118">After you configure, compile, and deploy a custom pipeline, changes in the configuration require recompiling and redeployment of the custom pipeline.</span></span>  
  
 <span data-ttu-id="221cf-119">建立、 建置和部署自訂管線的相關資訊，請參閱 BizTalk Server 說明。</span><span class="sxs-lookup"><span data-stu-id="221cf-119">For information about creating, building, and deploying custom pipelines, see BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="221cf-120">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="221cf-120">This section contains:</span></span>  
  
-   [<span data-ttu-id="221cf-121">SWIFT 解譯器設定屬性</span><span class="sxs-lookup"><span data-stu-id="221cf-121">SWIFT Disassembler Configuration Properties</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)