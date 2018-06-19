---
title: SWIFT 組合器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assembler
- send pipelines, messages
- messages, send pipelines
ms.assetid: 2a95c7d4-da10-4058-bc2c-3efc35958e14
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91d9411cce90079e8a84fc6919bd6ebf8b2b4371
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214430"
---
# <a name="swift-assembler"></a><span data-ttu-id="9cfed-102">SWIFT 組譯工具</span><span class="sxs-lookup"><span data-stu-id="9cfed-102">SWIFT Assembler</span></span>
<span data-ttu-id="9cfed-103">輸出的傳送管線處理傳輸的所有訊息[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]應用程式 （透過傳送埠傳送）。</span><span class="sxs-lookup"><span data-stu-id="9cfed-103">An outbound send pipeline processes all messages transmitted by an [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] application (sent through a send port).</span></span>  
  
 <span data-ttu-id="9cfed-104">與輸出處理邏輯的執行階段便會產生 BizTalk 傳送管線。</span><span class="sxs-lookup"><span data-stu-id="9cfed-104">Logical execution stages related to outbound processing make up the BizTalk send pipelines.</span></span> <span data-ttu-id="9cfed-105">管線元件服務，或實作每個階段。</span><span class="sxs-lookup"><span data-stu-id="9cfed-105">A pipeline component services or implements each stage.</span></span> <span data-ttu-id="9cfed-106">特別是，組合器服務在接收管線的 「 組合 」 階段。</span><span class="sxs-lookup"><span data-stu-id="9cfed-106">In particular, the assembler services the assemble stage in the receive pipeline.</span></span> <span data-ttu-id="9cfed-107">A4SWIFT 提供 SWIFT 特定輸出訊息處理中的自訂組合器元件的功能。</span><span class="sxs-lookup"><span data-stu-id="9cfed-107">A4SWIFT provides SWIFT-specific outbound message processing functionality in a custom assembler component.</span></span>  
  
 <span data-ttu-id="9cfed-108">SWIFT 組譯工具，自訂的一般檔案組合器處理輸出 SWIFT 的訊息，提供功能，並執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="9cfed-108">The SWIFT assembler, a custom flat file assembler, provides functionality for processing outbound SWIFT messages, and performs the following functions:</span></span>  
  
-   <span data-ttu-id="9cfed-109">動態探索訊息類型，並解析文件結構描述</span><span class="sxs-lookup"><span data-stu-id="9cfed-109">Dynamically discovers the message type and resolves the document schema</span></span>  
  
-   <span data-ttu-id="9cfed-110">剖析的 XML 序列化 SWIFT 的一般檔案</span><span class="sxs-lookup"><span data-stu-id="9cfed-110">Serializes parsed XML into SWIFT flat files</span></span>  
  
 <span data-ttu-id="9cfed-111">下圖顯示 SWIFT 組合器資料流。</span><span class="sxs-lookup"><span data-stu-id="9cfed-111">The following figure shows the SWIFT assembler data flow.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro3.gif "FSA_Intro3")  
  
 <span data-ttu-id="9cfed-112">如需 SWIFT 組譯工具的詳細資訊，請參閱[SWIFT 解譯器和組合器使用](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)。</span><span class="sxs-lookup"><span data-stu-id="9cfed-112">For more information about the SWIFT assembler, see [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cfed-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cfed-113">See Also</span></span>  
 [<span data-ttu-id="9cfed-114">BizTalk Accelerator for SWIFT 的執行階段</span><span class="sxs-lookup"><span data-stu-id="9cfed-114">BizTalk Accelerator for SWIFT Runtime</span></span>](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)