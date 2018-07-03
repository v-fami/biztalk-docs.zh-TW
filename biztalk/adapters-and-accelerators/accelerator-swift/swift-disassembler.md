---
title: SWIFT 解譯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disassembler
- messages, receive pipelines
- receive pipelines, messages
ms.assetid: 42641550-0c88-4535-b5d5-b90acb30a6d3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25c389e10a48287ef87495b32fe2d69644a8259e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010919"
---
# <a name="swift-disassembler"></a><span data-ttu-id="91549-102">SWIFT 解譯器</span><span class="sxs-lookup"><span data-stu-id="91549-102">SWIFT Disassembler</span></span>
<span data-ttu-id="91549-103">輸入的接收管線會處理所有的訊息提交至[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]（在接收位置接收） 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="91549-103">An inbound receive pipeline processes all messages submitted to an [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] application (received at a receive location).</span></span>  
  
 <span data-ttu-id="91549-104">與 BizTalk 的輸入的處理構成邏輯的執行階段接收管線。</span><span class="sxs-lookup"><span data-stu-id="91549-104">Logical execution stages related to inbound processing make up the BizTalk receive pipelines.</span></span> <span data-ttu-id="91549-105">管線元件或服務實作的每個階段。</span><span class="sxs-lookup"><span data-stu-id="91549-105">A pipeline component services or implements each stage.</span></span> <span data-ttu-id="91549-106">特別是，解譯器服務在接收管線的解譯階段。</span><span class="sxs-lookup"><span data-stu-id="91549-106">In particular, the disassembler services the disassemble stage in the receive pipeline.</span></span> <span data-ttu-id="91549-107">A4SWIFT 提供特定 SWIFT 的訊息處理中的自訂解譯器元件的功能。</span><span class="sxs-lookup"><span data-stu-id="91549-107">A4SWIFT provides SWIFT-specific message processing functionality in a custom disassembler component.</span></span>  
  
 <span data-ttu-id="91549-108">SWIFT 解譯器中，自訂的一般檔案解譯器，可用來處理輸入的 SWIFT 訊息與批次，提供功能，並執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="91549-108">The SWIFT disassembler, a custom flat file disassembler, provides functionality for processing inbound SWIFT messages and batches, and performs the following functions:</span></span>  
  
- <span data-ttu-id="91549-109">動態探索訊息類型，並解析文件結構描述</span><span class="sxs-lookup"><span data-stu-id="91549-109">Dynamically discovers the message type and resolves the document schema</span></span>  
  
- <span data-ttu-id="91549-110">將 SWIFT 的一般檔案剖析為 XML</span><span class="sxs-lookup"><span data-stu-id="91549-110">Parses SWIFT flat files into XML</span></span>  
  
- <span data-ttu-id="91549-111">叫用驗證讀取器執行 XML （結構描述） 驗證的 XML</span><span class="sxs-lookup"><span data-stu-id="91549-111">Invokes the XML validating reader to perform XML (schema) validation</span></span>  
  
- <span data-ttu-id="91549-112">叫用的 「 商務規則引擎 (BRE) 」，來執行 BRE 驗證</span><span class="sxs-lookup"><span data-stu-id="91549-112">Invokes the Business Rule Engine (BRE) to perform BRE validation</span></span>  
  
- <span data-ttu-id="91549-113">將已剖析的 XML 訊息發佈到 MessageBox 資料庫的升級的內容屬性與序列化的錯誤集合 XML</span><span class="sxs-lookup"><span data-stu-id="91549-113">Publishes a parsed XML message to the MessageBox database with promoted context properties and serialized error collection XML</span></span>  
  
- <span data-ttu-id="91549-114">處理並解譯輸入批次</span><span class="sxs-lookup"><span data-stu-id="91549-114">Processes and disassembles inbound batches</span></span>  
  
  <span data-ttu-id="91549-115">下圖顯示 SWIFT 解譯器資料流。</span><span class="sxs-lookup"><span data-stu-id="91549-115">The following figure shows the SWIFT disassembler data flow.</span></span>  
  
  <span data-ttu-id="91549-116">![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro2.gif "FSA_Intro2")</span><span class="sxs-lookup"><span data-stu-id="91549-116">![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro2.gif "FSA_Intro2")</span></span>  
  
  <span data-ttu-id="91549-117">如需有關 SWIFT 解譯器的詳細資訊，請參閱[使用 SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)。</span><span class="sxs-lookup"><span data-stu-id="91549-117">For more information about the SWIFT disassembler, see [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91549-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91549-118">See Also</span></span>  
 [<span data-ttu-id="91549-119">BizTalk Accelerator for SWIFT 執行階段</span><span class="sxs-lookup"><span data-stu-id="91549-119">BizTalk Accelerator for SWIFT Runtime</span></span>](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)