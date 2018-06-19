---
title: 設定 FRR 延遲逾時 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, configuring delay time-out
ms.assetid: 62209bf6-56c8-483a-96d5-328bffc8b680
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbf4c08984876627c0f11f935b0be3e32769b5f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22213998"
---
# <a name="setting-the-frr-delay-time-out"></a>設定 FRR 延遲逾時
您必須設定 FRR 協調流程的逾時時間後一些持續時間，因此它不會等待 FNN 回應無限期。 如果逾時期間到期，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]發行至自訂的逾時的處理常式逾時訊息。  
  
### <a name="to-set-the-frr-delay-time-out"></a>若要設定 FRR 延遲逾時  
  
1.  按一下**啟動**，按一下 **執行**，型別**regedit**，然後按一下 **確定**。  
  
2.  在左窗格的登錄編輯程式中，移至 我的電腦/HKEY_LOCAL_MACHINE/軟體/Microsoft/BizTalk Accelerator for SWIFT/FRR。  
  
    > [!IMPORTANT]
    >  在 [角色] 節點中所定義的工作流程中的位置，將會加入角色。 若要變更該位置，您需要執行步驟 8，變更順序的 [角色] 節點中的角色。  
  
3.  在右窗格的登錄編輯程式中，按兩下**DelayTimeout**。  
  
4.  在**編輯 DWORD 值**對話方塊中，於**數值資料**方塊中，以十六進位格式輸入逾時期間。  
  
    > [!NOTE]
    >  預設值為**FRR DelayTimeout**屬性為 600 秒 （258 十六進位）。  
  
5.  按一下 **[確定]**。