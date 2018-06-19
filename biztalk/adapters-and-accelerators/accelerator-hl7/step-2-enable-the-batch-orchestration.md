---
title: 步驟 2： 啟用批次協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4badf807-f461-4d0a-a3b6-9f671e580d91
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f8b18e41aacf61ac4e55e1c8047e9685179656a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206254"
---
# <a name="step-2-enable-the-batch-orchestration"></a>步驟 2： 啟用批次協調流程
批次協調流程會控制建立批次程序。 它維護要包含在批次中的所有訊息的參考、 控制輸出批次交易，會產生批次訊息、 路由傳送外寄批次，以及處理內送通知批次。 您需要建立批次程序工作批次協調流程登錄。  
  
### <a name="to-enable-the-batch-orchestration"></a>若要啟用批次協調流程  
  
1.  在 BizTalk 管理主控台中，按一下 **協調流程**，以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後按一下 **屬性**。  
  
2.  在 [協調流程屬性] 對話方塊的主控台樹狀目錄中，按一下**繫結**。  
  
3.  在**繫結** 窗格中，針對**主機**，選取**BizTalkServerApplication**。 按一下 **[確定]**。  
  
4.  在 BizTalk 管理主控台中，以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後按一下 **登錄**。  
  
 若要繼續[步驟 3： 建立和設定目的地合作對象](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-configure-a-destination-party.md)。