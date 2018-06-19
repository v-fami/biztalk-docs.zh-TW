---
title: 繫結和啟動協調流程 FRR |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FRR, binding orchestrations
- FRR, starting orchestrations
- bindings, orchestrations
- orchestrations, bindings
ms.assetid: b74a0116-e98b-4fec-b386-710ce421a1e2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81cf116fc03a8f2d898752a077e8347fd395a4a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209054"
---
# <a name="binding-and-starting-the-frr-orchestration"></a>繫結和啟動 FRR 協調流程
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]包含 FRR 協調流程做為已部署的組件 ([!INCLUDE[btsCoName](../../includes/btsconame-md.md)]。Solutions.FinancialServices.SWIFT.FrrOrchestration)。 您要啟動此協調流程。  
  
 **摘要**  
  
 若要啟動 FRR 協調流程，執行下列作業：  
  
-   藉由設定主應用程式 [biztalkserverapplication]，繫結 FrrOrchestration.FrrMain 協調流程。  
  
-   啟動 FrrOrchestration.FrrMain 協調流程。  
  
### <a name="to-bind-and-start-the-frr-orchestration"></a>若要繫結並啟動 FRR 協調流程  
  
1.  在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，然後**BizTalk應用程式 1**。 按一下**協調流程**。  
  
2.  在 [協調流程] 窗格中，以滑鼠右鍵按一下**FrrOrchestration.FrrMain**協調流程，然後再按一下**屬性**。  
  
3.  在 [協調流程屬性] 對話方塊中，按一下**繫結**的左窗格中。 如**主機**，選取**BizTalkServerApplication**。 按一下**套用**，然後按一下 **確定**。  
  
4.  在 [協調流程] 窗格中，以滑鼠右鍵按一下**FrrMain**協調流程，然後再按一下**啟動**。