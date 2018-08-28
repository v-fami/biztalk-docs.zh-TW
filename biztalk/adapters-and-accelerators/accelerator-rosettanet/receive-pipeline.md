---
title: 接收管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cd8f03aa-f5c3-49e7-946b-c8c91fe3abc7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a2c1de940fab14aa370dc1358efe36fe702a9d2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990303"
---
# <a name="receive-pipeline"></a><span data-ttu-id="887b6-102">接收管線</span><span class="sxs-lookup"><span data-stu-id="887b6-102">Receive Pipeline</span></span>
<span data-ttu-id="887b6-103">此範例提供了有效 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]接收管線，您可以自訂您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="887b6-103">This sample provides a working Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] receive pipeline that you can customize for your application.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="887b6-104">示範</span><span class="sxs-lookup"><span data-stu-id="887b6-104">Demonstrates</span></span>  
 <span data-ttu-id="887b6-105">本範例示範如何使用 BTARN 接收管線 (PipelineReceive.btp) 將內送 RNIF 訊息處理為相等的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="887b6-105">This sample demonstrates how to process an incoming RNIF message into the equivalent XML message using the BTARN receive pipeline (PipelineReceive.btp).</span></span> <span data-ttu-id="887b6-106">PipelineReceive.btp 位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\rnpipelines。</span><span class="sxs-lookup"><span data-stu-id="887b6-106">PipelineReceive.btp is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines.</span></span> <span data-ttu-id="887b6-107">它包含下列階段：</span><span class="sxs-lookup"><span data-stu-id="887b6-107">It includes the following stages:</span></span>  
  
- <span data-ttu-id="887b6-108">ReceiveMessageNonRepudiate</span><span class="sxs-lookup"><span data-stu-id="887b6-108">ReceiveMessageNonRepudiate</span></span>  
  
- <span data-ttu-id="887b6-109">RNMimeDecoder (MIME 前置處理器/解碼器)</span><span class="sxs-lookup"><span data-stu-id="887b6-109">RNMimeDecoder (MIME Preprocessor/Decoder)</span></span>  
  
- <span data-ttu-id="887b6-110">RNDAsm (XML 解譯器)</span><span class="sxs-lookup"><span data-stu-id="887b6-110">RNDAsm (XML Disassembler)</span></span>  
  
- <span data-ttu-id="887b6-111">RNPartyRes (「合作對象解析」元件)</span><span class="sxs-lookup"><span data-stu-id="887b6-111">RNPartyRes (Party Resolution component)</span></span>  
  
- <span data-ttu-id="887b6-112">MessageUpdater</span><span class="sxs-lookup"><span data-stu-id="887b6-112">MessageUpdater</span></span>  
  
  <span data-ttu-id="887b6-113">此管線中，以及此管線中的訊息流程元件的相關資訊，請參閱[BTARN 接收管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="887b6-113">For more information about the components of this pipeline, and the message flow in this pipeline, see [BTARN Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887b6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="887b6-114">See Also</span></span>  
 <span data-ttu-id="887b6-115">[管線範例](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md) </span><span class="sxs-lookup"><span data-stu-id="887b6-115">[Pipeline Samples](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md) </span></span>  
 [<span data-ttu-id="887b6-116">BTARN 接收管線</span><span class="sxs-lookup"><span data-stu-id="887b6-116">BTARN Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)