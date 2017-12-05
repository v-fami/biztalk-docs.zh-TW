---
title: "SWIFT 解譯器和組合器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developing, assembler
- developing, disassembler
- assembler, developing
- disassembler, developing
ms.assetid: cc88ed4c-baed-4efa-b54f-9fe079df9ba4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a63b27e3c89ac59c698098b09e2f6565980e363
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="working-with-the-swift-disassembler-and-assembler"></a><span data-ttu-id="2564d-102">SWIFT 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="2564d-102">Working with the SWIFT Disassembler and Assembler</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="2564d-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]提供自訂管線元件、 SWIFT 的解譯器和 SWIFT 組譯工具所沒有的功能，專為處理 SWIFT 的一般檔案訊息設計。</span><span class="sxs-lookup"><span data-stu-id="2564d-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides custom pipeline components, the SWIFT disassembler, and SWIFT assembler that have features designed specifically for processing SWIFT flat-file messages.</span></span> <span data-ttu-id="2564d-104">[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]傳送和接收管線使用 A4SWIFT 管線元件來執行特定工作階段定義輸入 （接收） 和輸出 （傳送） 處理。</span><span class="sxs-lookup"><span data-stu-id="2564d-104">The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] send and receive pipelines use the A4SWIFT pipeline components to perform specific tasks during defined stages of inbound (receive) and outbound (send) processing.</span></span> <span data-ttu-id="2564d-105">關於處理訊息、 管線和管線元件的詳細資訊，請參閱 BizTalk Server 說明。</span><span class="sxs-lookup"><span data-stu-id="2564d-105">For further details about message processing, pipelines, and pipeline components, see BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="2564d-106">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="2564d-106">This section contains:</span></span>  
  
-   [<span data-ttu-id="2564d-107">SWIFT 解譯器和組合器功能</span><span class="sxs-lookup"><span data-stu-id="2564d-107">SWIFT Disassembler and Assembler Functionality</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-and-assembler-functionality.md)  
  
-   [<span data-ttu-id="2564d-108">將 SWIFT 解譯器或組合器新增至管線</span><span class="sxs-lookup"><span data-stu-id="2564d-108">Adding the SWIFT Disassembler or Assembler to a Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-the-swift-disassembler-or-assembler-to-a-pipeline.md)  
  
-   [<span data-ttu-id="2564d-109">設定 SWIFT 解譯器或組合器</span><span class="sxs-lookup"><span data-stu-id="2564d-109">Configuring the SWIFT Disassembler or Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-disassembler-or-assembler.md)  
  
-   [<span data-ttu-id="2564d-110">動態訊息類型探索和結構描述解析</span><span class="sxs-lookup"><span data-stu-id="2564d-110">Dynamic Message Type Discovery and Schema Resolution</span></span>](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md)  
  
-   [<span data-ttu-id="2564d-111">建立動態訊息類型探索的自訂標頭結構描述</span><span class="sxs-lookup"><span data-stu-id="2564d-111">Creating Custom Header Schemas for Dynamic Message Type Discovery</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-custom-header-schemas-for-dynamic-message-type-discovery.md)  
  
-   [<span data-ttu-id="2564d-112">解譯輸入批次</span><span class="sxs-lookup"><span data-stu-id="2564d-112">Disassembling Inbound Batches</span></span>](../../adapters-and-accelerators/accelerator-swift/disassembling-inbound-batches.md)