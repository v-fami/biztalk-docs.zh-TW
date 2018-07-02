---
title: 繫結和啟動 FRR 協調流程 |Microsoft Docs
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
ms.openlocfilehash: b01386cedbd25148e5ea0ce2ac44fb56e9fe3d03
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987439"
---
# <a name="binding-and-starting-the-frr-orchestration"></a>繫結和啟動 FRR 協調流程
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 包含 FRR 協調流程做為已部署的組件 (Microsoft。Solutions.FinancialServices.SWIFT.FrrOrchestration)。 您要啟動此協調流程。  
  
 **摘要**  
  
 若要啟動 FRR 協調流程，執行下列作業：  
  
-   藉由設定主應用程式 [biztalkserverapplication]，繫結 FrrOrchestration.FrrMain 協調流程。  
  
-   啟動 FrrOrchestration.FrrMain 協調流程。  
  
### <a name="to-bind-and-start-the-frr-orchestration"></a>若要繫結和啟動 FRR 協調流程  
  
1.  在 [BizTalk Server 管理主控台中，展開**BizTalk Server 管理]**， **BizTalk 群組**，**應用程式**，然後**BizTalk應用程式 1**。 按一下 **協調流程**。  
  
2.  在 [協調流程] 窗格中，以滑鼠右鍵按一下**FrrOrchestration.FrrMain**協調流程，然後再按一下**屬性**。  
  
3.  在 [協調流程屬性] 對話方塊中，按一下**繫結**的左窗格中。 針對**主機**，選取**BizTalkServerApplication**。 按一下 **套用**，然後按一下**確定**。  
  
4.  在 [協調流程] 窗格中，以滑鼠右鍵按一下**FrrMain**協調流程，然後再按一下**開始**。