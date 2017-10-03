---
title: "步驟 1： 設定和啟用 BatchControlPort 接收連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be248a05-e740-497a-b112-8ba3a57b020b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d50289924062268db078844f2b3d2eaaccda23a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-and-enable-the-batchcontrolport-receive-port"></a>步驟 1： 設定和啟用 BatchControlPort 接收連接埠
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 安裝程式會建立接收埠、 批次控制連接埠，來處理訊息批次協調流程用來啟動、 停止，和時間的批次。 這些訊息包含批次啟動、 批次終止和批次計時器訊息。 在此步驟中，您會設定批次控制連接埠的接收管線，及啟用的通訊埠。  
  
### <a name="to-configure-and-enable-batchcontrolport"></a>若要設定並啟用 BatchControlPort  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，和**BizTalk 應用程式1**。 按一下**接收位置**。  
  
3.  以滑鼠右鍵按一下**BatchControlLocation**，然後按一下 **停用**。  
  
4.  以滑鼠右鍵按一下**BatchControlLocation**，然後按一下 **屬性**。  
  
5.  在 [接收位置屬性] 對話方塊的**接收管線**，選取**BTAHL72XPipelines.BTAHL72XReceivePipeline**。按一下**確定**。  
  
6.  在 BizTalk 管理主控台中，以滑鼠右鍵按一下**BatchControlLocation**，然後按一下 **啟用**。  
  
 若要繼續[步驟 2： 啟用批次協調流程](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md)。