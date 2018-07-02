---
title: BizTalk Server 中的 zombie |Microsoft Docs
description: BizTalk Server 中的 zombie 訊息的常見原因
ms.custom: ''
ms.date: 03/23/2016
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c684891-e984-442f-b5fd-de5f7cf32b44
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6a243e772fe5bc8408288167d3e8882a74e9a57
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976583"
---
# <a name="zombies-in-biztalk-server"></a>BizTalk Server 中的 Zombie

## <a name="what-is-a-zombie"></a>何謂 Zombie？  
  
-   Zombie (廢止) 訊息是從 MessageBox 經路由送往執行中協調流程、但是當該協調流程結束時仍「在途中」的訊息。 「在途中」訊息是已經路由送往服務執行個體，然後即處於該服務執行個體之 MessageBox 佇列中的訊息。 因為訂閱的協調流程執行個體可能不再取用該訊息，所以會擱置此訊息，並以「擱置 (不可繼續)」的 ServiceInstance/State 值標示它。  
  
-   Zombie 服務執行個體是當訊息從 MessageBox 經路由前往協調流程執行個體且仍「在途中」時，即已完成的協調流程執行個體。 由於協調流程執行個體已經結束，它便無法取用這個「在途中」訊息，因此訊息會遭到擱置，並且標示「擱置 (不可繼續)」的 ServiceInstance/State 值。  
  
## <a name="typical-causes"></a>常見的原因
發生 Zombie 的狀況通常分成以下類別：  
  
1. **終止控制訊息**-協調流程引擎允許控制訊息來取消所有目前正在執行的工作特定的協調流程執行個體中使用。 由於控制訊息會立即停止執行中的協調流程，所以產生 Zombie 執行個體一點也不意外。 有許多與「人力工作流程」相關的設計經常使用這種機制，而其他某些設計也會採用。  
  
2. **平行待命接收**– 在此案例中的服務執行個體等候 1 的 n 個訊息，並接收特定訊息時它會執行一些工作，並終止。 如果正好於服務執行個體終止時，在平行分支上收到訊息，便會產生 Zombie。  
  
3. **循序群組與非決定性端點**– 在此案例中，主要協調流程排程的設計可處理特定類型的所有訊息，以便滿足特定類型的系統設計需求。 這些設計需求可能包括有序傳遞、資源分配程式和批次處理。 就此實例而言，比較傾向於定義環繞「待命」的 While 迴圈，而此待命帶有一個含「接收」的分支以及另一個帶有延遲圖形 (其後連接某個用來設定某變數以指示 While 迴圈停止的建構) 的分支。 因為這可能觸發延遲，所以是非決定性的，但卻仍然會傳遞該訊息。 像這樣的非決定性端點就很容產生 Zombie。  
  
   Zombie 服務執行個體暫停時，會產生下列錯誤訊息：  
  
`0xC0C01B4C The instance completed without consuming all of its messages. The instance and its unconsumed messages have been suspended.`  
  
 您可以使用[BizTalk 結束字元](https://www.microsoft.com/download/details.aspx?id=2846)來協助移除 zombie。  
  
## <a name="see-also"></a>另請參閱  
 **移除已擱置的服務執行個體** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]