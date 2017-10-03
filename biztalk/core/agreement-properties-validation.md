---
title: "協議屬性驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d565c26-37ef-4aee-aebb-3152880242a1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20c01ec281005cbeaffda6dcd2349c1153a531b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-properties-validation"></a>協議屬性驗證
協議屬性包含檢查交換、群組或交易集的重複控制編號。 若已在協議屬性中啟用這些驗證，EDI 接收管線就會執行它們。 這些驗證包括：  
  
-   檢查重複的交換控制編號 (在 X12 中為 ISA13，在 EDIFACT 中為 UNB5)。 您輸入時間值 (天) 來建立這個檢查的有效時間範圍。  
  
-   檢查交換內重複的群組控制編號 (在 X12 中為 GS6，在 EDIFACT 中為 UNG5)  
  
-   檢查功能群組中重複的交易集控制編號 (在 X12 為 ST2，在 EDIFACT 為 UNH1)  
  
## <a name="see-also"></a>另請參閱  
 [EDI 訊息驗證](../core/edi-message-validation.md)