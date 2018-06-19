---
title: RNIF 管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RNIF, pipelines
- pipelines, RNIF
ms.assetid: 6cf480fe-6b54-4b13-8318-617f3bba71d0
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cfdc50906f356a7eceeea50dd716c903720f785
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963436"
---
# <a name="rnif-pipelines"></a><span data-ttu-id="aefb3-102">RNIF 管線</span><span class="sxs-lookup"><span data-stu-id="aefb3-102">RNIF Pipelines</span></span>
<span data-ttu-id="aefb3-103">[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]接收和傳送管線會執行接收所需的處理或傳送 RosettaNet 實作架構 (RNIF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="aefb3-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] receive and send pipelines perform the processing required for receive or send RosettaNet Implementation Framework (RNIF) messages.</span></span> <span data-ttu-id="aefb3-104">這個處理作業包括預先處理、解碼/編碼、解密/加密、解譯/組譯以及一方驗證。</span><span class="sxs-lookup"><span data-stu-id="aefb3-104">This processing includes preprocessing, decoding/encoding, decrypting/encrypting, disassembly/assembly, and party authentication.</span></span>  
  
## <a name="pipeline-files"></a><span data-ttu-id="aefb3-105">管線檔案</span><span class="sxs-lookup"><span data-stu-id="aefb3-105">Pipeline Files</span></span>  
 <span data-ttu-id="aefb3-106">標準[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收和傳送管線不會處理 RNIF 訊息原生。</span><span class="sxs-lookup"><span data-stu-id="aefb3-106">Standard [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive and send pipelines do not process RNIF messages natively.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="aefb3-107">已新增自訂接收管線和傳送管線針對此目的。</span><span class="sxs-lookup"><span data-stu-id="aefb3-107"> has added custom receive and send pipelines for this purpose.</span></span> <span data-ttu-id="aefb3-108">這些管線是以 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 管線為建構基礎，不過還附加了 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 特有的處理能力。</span><span class="sxs-lookup"><span data-stu-id="aefb3-108">These pipelines are built on the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipelines, but add [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]-specific processing capability.</span></span> <span data-ttu-id="aefb3-109">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管線 （RNIFReceive.btp 和 RNIFSend.btp） 位於[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]SDK，網址\<*磁碟機*\>: \Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\rnpipelines。</span><span class="sxs-lookup"><span data-stu-id="aefb3-109">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipelines (RNIFReceive.btp and RNIFSend.btp) are available in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK at \<*drive*\>:\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines.</span></span> <span data-ttu-id="aefb3-110">如此，您就可以根據自己的目的自訂這些管線。</span><span class="sxs-lookup"><span data-stu-id="aefb3-110">This lets you customize them for your own purposes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefb3-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="aefb3-111">See Also</span></span>  
 <span data-ttu-id="aefb3-112">[BTARN 接收管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="aefb3-112">[BTARN Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md) </span></span>  
 [<span data-ttu-id="aefb3-113">BTARN 傳送管線</span><span class="sxs-lookup"><span data-stu-id="aefb3-113">BTARN Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)