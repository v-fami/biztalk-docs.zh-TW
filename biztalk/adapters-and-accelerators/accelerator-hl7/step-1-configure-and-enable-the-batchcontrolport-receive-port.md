---
title: 步驟 1： 設定和啟用 BatchControlPort 接收連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be248a05-e740-497a-b112-8ba3a57b020b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fb11e0638a66fa7d22332d1cbca103a14490528
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988247"
---
# <a name="step-1-configure-and-enable-the-batchcontrolport-receive-port"></a>步驟 1： 設定和啟用 BatchControlPort 接收埠
Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 安裝程式會建立接收埠，批次控制項即通訊埠，處理的訊息批次協調流程用來啟動、 停止，和時間的批次。 這些訊息包含批次啟動批次終止，批次計時器訊息。 在此步驟中，您可以設定批次的控制連接埠，接收管線，並啟用連接埠。  
  
### <a name="to-configure-and-enable-batchcontrolport"></a>若要設定及啟用 BatchControlPort  
  
1. 開始**BizTalk Server 管理**。  
  
2. 在 [BizTalk Server 管理主控台中，展開**BizTalk Server 管理]**， **BizTalk 群組**，**應用程式**，和**BizTalk 應用程式1**。 按一下 **接收位置**。  
  
3. 以滑鼠右鍵按一下**BatchControlLocation**，然後按一下**停用**。  
  
4. 以滑鼠右鍵按一下**BatchControlLocation**，然後按一下**屬性**。  
  
5. 在 接收位置屬性 對話方塊中，如**接收管線**，選取**BTAHL72XPipelines.BTAHL72XReceivePipeline**。按一下 **確定**。  
  
6. 在 BizTalk 管理主控台中，以滑鼠右鍵按一下**BatchControlLocation**，然後按一下**啟用**。  
  
   請繼續進行[步驟 2： 啟用批次協調流程](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md)。