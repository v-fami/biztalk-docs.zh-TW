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
ms.openlocfilehash: 7461ce357b3fa9cb6216dfce6381876100bb4287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-pipeline"></a>接收管線
這個範例提供了有效的 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 接收管線，您可以針對您的應用程式自訂此接收管線。  
  
## <a name="demonstrates"></a>示範  
 本範例示範如何使用 BTARN 接收管線 (PipelineReceive.btp) 將內送 RNIF 訊息處理為相等的 XML 訊息。 PipelineReceive.btp 位於*\<磁碟機 >*: \Program Files\Microsoft BizTalk\<版本 > Accelerator for rosettanet\sdk\rnpipelines。 它包含下列階段：  
  
-   ReceiveMessageNonRepudiate  
  
-   RNMimeDecoder (MIME 前置處理器/解碼器)  
  
-   RNDAsm (XML 解譯器)  
  
-   RNPartyRes (「合作對象解析」元件)  
  
-   MessageUpdater  
  
 這個管線，和此管線中的訊息流程元件的相關資訊，請參閱[BTARN 接收管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管線範例](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md)   
 [BTARN 接收管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)