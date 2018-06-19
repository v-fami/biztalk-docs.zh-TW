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
# <a name="rnif-pipelines"></a>RNIF 管線
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]接收和傳送管線會執行接收所需的處理或傳送 RosettaNet 實作架構 (RNIF) 訊息。 這個處理作業包括預先處理、解碼/編碼、解密/加密、解譯/組譯以及一方驗證。  
  
## <a name="pipeline-files"></a>管線檔案  
 標準[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收和傳送管線不會處理 RNIF 訊息原生。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]已新增自訂接收管線和傳送管線針對此目的。 這些管線是以 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 管線為建構基礎，不過還附加了 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 特有的處理能力。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管線 （RNIFReceive.btp 和 RNIFSend.btp） 位於[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]SDK，網址\<*磁碟機*\>: \Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\rnpipelines。 如此，您就可以根據自己的目的自訂這些管線。  
  
## <a name="see-also"></a>請參閱  
 [BTARN 接收管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)   
 [BTARN 傳送管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)