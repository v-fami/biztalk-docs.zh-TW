---
title: 設定 SWIFT 解譯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, disassembler
- disassembler, configuring
ms.assetid: f3773781-7412-421c-943c-18cc665da8d9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ad88310f5bbf600edd576bc0bc17c64fe3ecbea
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001463"
---
# <a name="configuring-the-swift-disassembler"></a><span data-ttu-id="f7ad3-102">設定 SWIFT 解譯器</span><span class="sxs-lookup"><span data-stu-id="f7ad3-102">Configuring the SWIFT Disassembler</span></span>
<span data-ttu-id="f7ad3-103">SWIFT 解譯器 (DASM) 執行下列工作，當您在 Microsoft 中叫用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收管線：</span><span class="sxs-lookup"><span data-stu-id="f7ad3-103">The SWIFT disassembler (DASM) performs the following tasks when you invoke it in a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive pipeline:</span></span>  
  
- <span data-ttu-id="f7ad3-104">動態探索訊息類型，並解析文件結構描述</span><span class="sxs-lookup"><span data-stu-id="f7ad3-104">Dynamically discovers the message type and resolves the document schema</span></span>  
  
- <span data-ttu-id="f7ad3-105">將 SWIFT 的一般檔案剖析為 XML</span><span class="sxs-lookup"><span data-stu-id="f7ad3-105">Parses SWIFT flat files into XML</span></span>  
  
- <span data-ttu-id="f7ad3-106">叫用驗證讀取器執行 XML （結構描述） 驗證的 XML</span><span class="sxs-lookup"><span data-stu-id="f7ad3-106">Invokes the XML validating reader to perform XML (schema) validation</span></span>  
  
- <span data-ttu-id="f7ad3-107">叫用的 「 商務規則引擎 (BRE) 」，來執行 BRE 驗證</span><span class="sxs-lookup"><span data-stu-id="f7ad3-107">Invokes the Business Rule Engine (BRE) to perform BRE validation</span></span>  
  
- <span data-ttu-id="f7ad3-108">將已剖析的 XML 訊息發佈到 MessageBox 資料庫的升級的內容屬性與序列化的錯誤集合 XML</span><span class="sxs-lookup"><span data-stu-id="f7ad3-108">Publishes a parsed XML message to the MessageBox database with promoted context properties and serialized error collection XML</span></span>  
  
- <span data-ttu-id="f7ad3-109">處理程序的輸入批次</span><span class="sxs-lookup"><span data-stu-id="f7ad3-109">Processes inbound batches</span></span>  
  
  <span data-ttu-id="f7ad3-110">您可以設定以符合使用者案例的特定需求，上面所列的功能和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]解決方案。</span><span class="sxs-lookup"><span data-stu-id="f7ad3-110">You can configure the functionality listed above to meet the specific requirements for a user scenario and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] solution.</span></span>  
  
  <span data-ttu-id="f7ad3-111">BizTalk 管線設計師會在開發期間，自訂接收管線設定 SWIFT 解譯器。</span><span class="sxs-lookup"><span data-stu-id="f7ad3-111">BizTalk Pipeline Designer configures the SWIFT disassembler during development time of the custom receive pipeline.</span></span>  
  
  <span data-ttu-id="f7ad3-112">若要新增至自訂接收管線的 「 解譯 」 階段之後，請設定 SWIFT 解譯器，選取 BizTalk 管線設計工具畫布上的 SWIFT 解譯器元件。</span><span class="sxs-lookup"><span data-stu-id="f7ad3-112">To configure the SWIFT disassembler after it has been added to the disassemble stage of a custom receive pipeline, select the SWIFT disassembler component on the BizTalk Pipeline Designer canvas.</span></span> <span data-ttu-id="f7ad3-113">SWIFT 解譯器，然後接收焦點，而且您可以設定它使用在 Microsoft [屬性] 視窗的組態屬性[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f7ad3-113">The SWIFT disassembler then receives focus and you can set its configuration properties using the Properties window within Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)].</span></span>  
  
  <span data-ttu-id="f7ad3-114">可用的設定屬性及其描述和使用方式詳細資料的資料表，請參閱[SWIFT 解譯器設定屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ad3-114">For a table of available configuration properties and their descriptions and usage details, see [SWIFT Disassembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md).</span></span>  
  
  <span data-ttu-id="f7ad3-115">針對不同的案例使用 SWIFT 解譯器和設定組態屬性的相關資訊，請參閱[使用 SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ad3-115">For information about using the SWIFT disassembler for different scenarios and setting the configuration properties, see [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span></span>  
  
  <span data-ttu-id="f7ad3-116">當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]編譯二進位檔，它必須以靜態方式的組態設定寫入至自訂管線的自訂管線。</span><span class="sxs-lookup"><span data-stu-id="f7ad3-116">When [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] compiles the custom pipeline binary, it statically writes the configuration settings to the custom pipeline.</span></span> <span data-ttu-id="f7ad3-117">因此，您無法變更在部署期間的組態屬性，或執行階段。</span><span class="sxs-lookup"><span data-stu-id="f7ad3-117">Therefore, you cannot change configuration properties during deployment or run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7ad3-118">設定、 編譯及部署自訂的管線之後，在組態中的變更會需要重新編譯並重新部署自訂的管線。</span><span class="sxs-lookup"><span data-stu-id="f7ad3-118">After you configure, compile, and deploy a custom pipeline, changes in the configuration require recompiling and redeployment of the custom pipeline.</span></span>  
  
 <span data-ttu-id="f7ad3-119">如需建立、 建置和部署自訂的管線資訊，請參閱 BizTalk Server 說明。</span><span class="sxs-lookup"><span data-stu-id="f7ad3-119">For information about creating, building, and deploying custom pipelines, see BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="f7ad3-120">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="f7ad3-120">This section contains:</span></span>  
  
-   [<span data-ttu-id="f7ad3-121">SWIFT 解譯器設定屬性</span><span class="sxs-lookup"><span data-stu-id="f7ad3-121">SWIFT Disassembler Configuration Properties</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)