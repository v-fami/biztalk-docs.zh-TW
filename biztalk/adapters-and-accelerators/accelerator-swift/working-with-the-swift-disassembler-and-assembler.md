---
title: 使用 SWIFT 解譯器和組合器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- developing, assembler
- developing, disassembler
- assembler, developing
- disassembler, developing
ms.assetid: cc88ed4c-baed-4efa-b54f-9fe079df9ba4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1942e6648311c65acc2bb1cd91406904906cc8f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005735"
---
# <a name="working-with-the-swift-disassembler-and-assembler"></a><span data-ttu-id="a4dad-102">使用 SWIFT 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="a4dad-102">Working with the SWIFT Disassembler and Assembler</span></span>
<span data-ttu-id="a4dad-103">Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]提供自訂管線元件、 SWIFT 解譯器，以及 SWIFT 組合器具有專為處理 SWIFT 的一般檔案訊息的功能。</span><span class="sxs-lookup"><span data-stu-id="a4dad-103">Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides custom pipeline components, the SWIFT disassembler, and SWIFT assembler that have features designed specifically for processing SWIFT flat-file messages.</span></span> <span data-ttu-id="a4dad-104">[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]傳送和接收管線使用 A4SWIFT 管線元件的輸入定義的各個階段中執行特定工作 （接收） 和輸出 （傳送） 處理。</span><span class="sxs-lookup"><span data-stu-id="a4dad-104">The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] send and receive pipelines use the A4SWIFT pipeline components to perform specific tasks during defined stages of inbound (receive) and outbound (send) processing.</span></span> <span data-ttu-id="a4dad-105">如需訊息處理、 管線和管線元件的進一步詳細資訊，請參閱 BizTalk Server 說明。</span><span class="sxs-lookup"><span data-stu-id="a4dad-105">For further details about message processing, pipelines, and pipeline components, see BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="a4dad-106">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="a4dad-106">This section contains:</span></span>  
  
-   [<span data-ttu-id="a4dad-107">SWIFT 解譯器和組合器功能</span><span class="sxs-lookup"><span data-stu-id="a4dad-107">SWIFT Disassembler and Assembler Functionality</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-and-assembler-functionality.md)  
  
-   [<span data-ttu-id="a4dad-108">將 SWIFT 解譯器或組合器新增至管線</span><span class="sxs-lookup"><span data-stu-id="a4dad-108">Adding the SWIFT Disassembler or Assembler to a Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-the-swift-disassembler-or-assembler-to-a-pipeline.md)  
  
-   [<span data-ttu-id="a4dad-109">設定 SWIFT 解譯器或組合器</span><span class="sxs-lookup"><span data-stu-id="a4dad-109">Configuring the SWIFT Disassembler or Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-disassembler-or-assembler.md)  
  
-   [<span data-ttu-id="a4dad-110">動態訊息類型探索和結構描述解析</span><span class="sxs-lookup"><span data-stu-id="a4dad-110">Dynamic Message Type Discovery and Schema Resolution</span></span>](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md)  
  
-   [<span data-ttu-id="a4dad-111">建立動態訊息類型探索的自訂標頭結構描述</span><span class="sxs-lookup"><span data-stu-id="a4dad-111">Creating Custom Header Schemas for Dynamic Message Type Discovery</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-custom-header-schemas-for-dynamic-message-type-discovery.md)  
  
-   [<span data-ttu-id="a4dad-112">解譯輸入批次</span><span class="sxs-lookup"><span data-stu-id="a4dad-112">Disassembling Inbound Batches</span></span>](../../adapters-and-accelerators/accelerator-swift/disassembling-inbound-batches.md)