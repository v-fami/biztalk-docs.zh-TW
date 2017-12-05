---
title: "設定 SWIFT 解譯器和組合器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembler, configuring
- configuring, disassembler
- disassembler, configuring
- configuring, assembler
ms.assetid: 56e421f2-0292-40af-b878-0cba1b034e19
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8920a8b74da14eeb8186d153444ced7c54d57724
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-the-swift-disassembler-or-assembler"></a><span data-ttu-id="37050-102">設定 SWIFT 解譯器或組譯工具</span><span class="sxs-lookup"><span data-stu-id="37050-102">Configuring the SWIFT Disassembler or Assembler</span></span>
<span data-ttu-id="37050-103">SWIFT 解譯器或 SWIFT 組譯工具加入自訂管線後，您必須將它提供您想要用於特定案例 （例如啟用/停用動態訊息類型探索、 輸入解除批次處理即將、 XML 驗證的功能設定商務規則引擎 (BRE) 驗證，等等）。</span><span class="sxs-lookup"><span data-stu-id="37050-103">After you add the SWIFT disassembler or SWIFT assembler to a custom pipeline, you must configure it to provide the functionality you want for the particular scenario (such as enabling/disabling dynamic message type discovery, inbound debatching, XML validation, Business Rule Engine (BRE) validation, and so on).</span></span> <span data-ttu-id="37050-104">您必須設定 SWIFT 解譯器和組合器開發期間才能編譯和部署叫用的自訂管線。</span><span class="sxs-lookup"><span data-stu-id="37050-104">You must configure the SWIFT disassembler and assembler during development time before you compile and deploy the custom pipelines that invoke them.</span></span> <span data-ttu-id="37050-105">若要設定 SWIFT 的解譯器/組合器，在管線設計師中選取的元件，並編輯 [屬性] 視窗中的組態屬性。</span><span class="sxs-lookup"><span data-stu-id="37050-105">To configure the SWIFT disassembler/assembler, select the component in Pipeline Designer and edit the configuration properties in the Properties window.</span></span>  
  
 <span data-ttu-id="37050-106">請參閱[SWIFT 解譯器組態屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)完整詳細資料和每個組態屬性，以及其他使用方式和組態資訊的描述。</span><span class="sxs-lookup"><span data-stu-id="37050-106">Refer to [SWIFT Disassembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md) for complete details and descriptions for each configuration property, as well as other usage and configuration information.</span></span>  
  
 <span data-ttu-id="37050-107">請參閱[SWIFT 組合器組態屬性](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md)完整詳細資料和編碼字元集組態屬性，以及其他使用方式和組態資訊的描述。</span><span class="sxs-lookup"><span data-stu-id="37050-107">Refer to [SWIFT Assembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md) for complete details and descriptions for the Encoding Charset configuration property, as well as other usage and configuration information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37050-108">設定、 編譯及部署自訂的管線之後，組態中的變更將需要重新編譯和重新部署自訂的管線。</span><span class="sxs-lookup"><span data-stu-id="37050-108">After you configure, compile, and deploy the custom pipelines, changes in configuration will require re-compiling and re-deployment of the custom pipelines.</span></span>  
  
 <span data-ttu-id="37050-109">設定、 編譯及部署您的自訂管線來處理 SWIFT 訊息之後，您可以設定最多的使用您自訂的 SWIFT 接收管線和傳送連接埠會使用您自訂 SWIFT 傳送管線接收位置。</span><span class="sxs-lookup"><span data-stu-id="37050-109">After you configure, compile, and deploy your custom pipelines for processing SWIFT messages, you can set up receive locations that use your custom SWIFT receive pipeline, and send ports that use your custom SWIFT send pipeline.</span></span> <span data-ttu-id="37050-110">如需有關部署管線和設定接收埠、 接收位置和傳送埠，請參閱[單元 4： 建立 XML 接收和一般檔案傳送埠](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md)，[單元 5： 建立一般檔案接收和XML 傳送埠](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md)，和 BizTalk Server 說明。</span><span class="sxs-lookup"><span data-stu-id="37050-110">For more information about deploying pipelines and configuring receive ports, receive locations, and send ports, see [Module 4: Creating XML Receive and Flat File Send Ports](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md), [Module 5: Creating Flat File Receive and XML Send Ports](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md), and BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="37050-111">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="37050-111">This section contains:</span></span>  
  
-   [<span data-ttu-id="37050-112">設定 SWIFT 解譯器</span><span class="sxs-lookup"><span data-stu-id="37050-112">Configuring the SWIFT Disassembler</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-disassembler.md)  
  
-   [<span data-ttu-id="37050-113">設定 SWIFT 組合器</span><span class="sxs-lookup"><span data-stu-id="37050-113">Configuring the SWIFT Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-assembler.md)  
  
## <a name="see-also"></a><span data-ttu-id="37050-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="37050-114">See Also</span></span>  
 [<span data-ttu-id="37050-115">使用 SWIFT 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="37050-115">Working with the SWIFT Disassembler and Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)