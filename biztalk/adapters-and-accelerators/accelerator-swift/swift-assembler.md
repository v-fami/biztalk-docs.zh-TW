---
title: SWIFT 組合器 |Microsoft Docs
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
ms.openlocfilehash: 39f89720a36c026fa0e8f02902a8fefb08fcebf9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973311"
---
# <a name="swift-assembler"></a><span data-ttu-id="e3437-102">SWIFT 組合器</span><span class="sxs-lookup"><span data-stu-id="e3437-102">SWIFT Assembler</span></span>
<span data-ttu-id="e3437-103">輸出的傳送管線會處理傳輸的所有訊息[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]（透過傳送埠傳送） 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e3437-103">An outbound send pipeline processes all messages transmitted by an [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] application (sent through a send port).</span></span>  
  
 <span data-ttu-id="e3437-104">輸出處理相關的邏輯的執行階段是由 BizTalk 傳送管線所組成。</span><span class="sxs-lookup"><span data-stu-id="e3437-104">Logical execution stages related to outbound processing make up the BizTalk send pipelines.</span></span> <span data-ttu-id="e3437-105">管線元件或服務實作的每個階段。</span><span class="sxs-lookup"><span data-stu-id="e3437-105">A pipeline component services or implements each stage.</span></span> <span data-ttu-id="e3437-106">特別是，「 組合器 」 服務在接收管線中的 「 組合 」 階段。</span><span class="sxs-lookup"><span data-stu-id="e3437-106">In particular, the assembler services the assemble stage in the receive pipeline.</span></span> <span data-ttu-id="e3437-107">A4SWIFT 提供 SWIFT 特定輸出訊息處理的自訂組合器元件中的功能。</span><span class="sxs-lookup"><span data-stu-id="e3437-107">A4SWIFT provides SWIFT-specific outbound message processing functionality in a custom assembler component.</span></span>  
  
 <span data-ttu-id="e3437-108">SWIFT 組合器的自訂的一般檔案組合器中，提供功能來處理輸出 SWIFT 的訊息，並執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="e3437-108">The SWIFT assembler, a custom flat file assembler, provides functionality for processing outbound SWIFT messages, and performs the following functions:</span></span>  
  
- <span data-ttu-id="e3437-109">動態探索訊息類型，並解析文件結構描述</span><span class="sxs-lookup"><span data-stu-id="e3437-109">Dynamically discovers the message type and resolves the document schema</span></span>  
  
- <span data-ttu-id="e3437-110">將剖析的 XML 序列化至 SWIFT 的一般檔案</span><span class="sxs-lookup"><span data-stu-id="e3437-110">Serializes parsed XML into SWIFT flat files</span></span>  
  
  <span data-ttu-id="e3437-111">下圖顯示 SWIFT 組合器資料流。</span><span class="sxs-lookup"><span data-stu-id="e3437-111">The following figure shows the SWIFT assembler data flow.</span></span>  
  
  <span data-ttu-id="e3437-112">![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro3.gif "FSA_Intro3")</span><span class="sxs-lookup"><span data-stu-id="e3437-112">![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro3.gif "FSA_Intro3")</span></span>  
  
  <span data-ttu-id="e3437-113">如需有關 SWIFT 組合器的詳細資訊，請參閱[使用 SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)。</span><span class="sxs-lookup"><span data-stu-id="e3437-113">For more information about the SWIFT assembler, see [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3437-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3437-114">See Also</span></span>  
 [<span data-ttu-id="e3437-115">BizTalk Accelerator for SWIFT 執行階段</span><span class="sxs-lookup"><span data-stu-id="e3437-115">BizTalk Accelerator for SWIFT Runtime</span></span>](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)