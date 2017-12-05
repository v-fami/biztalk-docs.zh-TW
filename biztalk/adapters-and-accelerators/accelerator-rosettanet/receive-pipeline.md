---
title: "接收管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd8f03aa-f5c3-49e7-946b-c8c91fe3abc7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d5374c46411e0c4924585647736bfde7f1e4428
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="receive-pipeline"></a><span data-ttu-id="6a9c1-102">接收管線</span><span class="sxs-lookup"><span data-stu-id="6a9c1-102">Receive Pipeline</span></span>
<span data-ttu-id="6a9c1-103">這個範例提供了有效的 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 接收管線，您可以針對您的應用程式自訂此接收管線。</span><span class="sxs-lookup"><span data-stu-id="6a9c1-103">This sample provides a working [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] receive pipeline that you can customize for your application.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6a9c1-104">示範</span><span class="sxs-lookup"><span data-stu-id="6a9c1-104">Demonstrates</span></span>  
 <span data-ttu-id="6a9c1-105">本範例示範如何使用 BTARN 接收管線 (PipelineReceive.btp) 將內送 RNIF 訊息處理為相等的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="6a9c1-105">This sample demonstrates how to process an incoming RNIF message into the equivalent XML message using the BTARN receive pipeline (PipelineReceive.btp).</span></span> <span data-ttu-id="6a9c1-106">PipelineReceive.btp 位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\rnpipelines。</span><span class="sxs-lookup"><span data-stu-id="6a9c1-106">PipelineReceive.btp is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines.</span></span> <span data-ttu-id="6a9c1-107">它包含下列階段：</span><span class="sxs-lookup"><span data-stu-id="6a9c1-107">It includes the following stages:</span></span>  
  
-   <span data-ttu-id="6a9c1-108">ReceiveMessageNonRepudiate</span><span class="sxs-lookup"><span data-stu-id="6a9c1-108">ReceiveMessageNonRepudiate</span></span>  
  
-   <span data-ttu-id="6a9c1-109">RNMimeDecoder (MIME 前置處理器/解碼器)</span><span class="sxs-lookup"><span data-stu-id="6a9c1-109">RNMimeDecoder (MIME Preprocessor/Decoder)</span></span>  
  
-   <span data-ttu-id="6a9c1-110">RNDAsm (XML 解譯器)</span><span class="sxs-lookup"><span data-stu-id="6a9c1-110">RNDAsm (XML Disassembler)</span></span>  
  
-   <span data-ttu-id="6a9c1-111">RNPartyRes (「合作對象解析」元件)</span><span class="sxs-lookup"><span data-stu-id="6a9c1-111">RNPartyRes (Party Resolution component)</span></span>  
  
-   <span data-ttu-id="6a9c1-112">MessageUpdater</span><span class="sxs-lookup"><span data-stu-id="6a9c1-112">MessageUpdater</span></span>  
  
 <span data-ttu-id="6a9c1-113">這個管線，和此管線中的訊息流程元件的相關資訊，請參閱[BTARN 接收管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="6a9c1-113">For more information about the components of this pipeline, and the message flow in this pipeline, see [BTARN Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a9c1-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="6a9c1-114">See Also</span></span>  
 <span data-ttu-id="6a9c1-115">[管線範例](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md) </span><span class="sxs-lookup"><span data-stu-id="6a9c1-115">[Pipeline Samples](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md) </span></span>  
 [<span data-ttu-id="6a9c1-116">BTARN 接收管線</span><span class="sxs-lookup"><span data-stu-id="6a9c1-116">BTARN Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)