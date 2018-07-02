---
title: 步驟 6： 啟動協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, starting
- loopback tutorial, starting orchestratrations
ms.assetid: f16a4a77-04fe-4e73-8517-556668174eb9
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 973d0c5e8628d2363e8192c7faffeaebcc6d63b6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993183"
---
# <a name="step-6-start-orchestrations"></a>步驟 6： 啟動協調流程
在此步驟中，您可以使用 Microsoft[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以啟動 Microsoft 協調流程[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。  
  
### <a name="to-start-the-btarn-orchestrations-using-visual-studio"></a>啟動 BTARN 協調流程使用 Visual Studio  
  
1.  在 [ **BTARN**管理主控台中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，展開**應用程式**，和然後展開**BizTalk Application 1**。  
  
2.  按一下 **傳送埠**，然後啟動**PrivateInitiator_To_LOB**並**PrivateResponder_To_LOB**傳送埠。  
  
3.  按一下 **接收位置**，然後再啟用**LOB_To_PrivateInitiator**， **LOB_To_PrivateResponder**，**且**，並**Sync_Http_Receive**接收位置。  
  
4.  按一下 **協調流程**，並啟動所有**BTARN 協調流程**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 7： 建立範例 LOB 訊息](../../adapters-and-accelerators/accelerator-rosettanet/step-7-create-a-sample-lob-message.md)   
 [以程式控制方式停止及啟動協調流程、傳送埠和接收位置](../../adapters-and-accelerators/accelerator-rosettanet/code-to-stop-and-start-orchestrations-send-ports-and-receive-locations.md)