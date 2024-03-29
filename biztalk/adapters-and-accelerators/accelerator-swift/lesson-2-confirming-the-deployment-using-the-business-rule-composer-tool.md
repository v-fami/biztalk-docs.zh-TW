---
title: 第 2 課： 確認部署使用 「 商務規則編輯器 」 工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, verifying
- verifying, business rules
- verifying, Business Rule Composer tool
- business rules, Business Rule Composer tool
- Business Rule Composer tool
ms.assetid: 337dc469-cf9e-406b-90ae-0f580b17d7c9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e9de00e6996daf5ce7759d395f6dfcf97989aa4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997799"
---
# <a name="lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool"></a>第 2 課： 確認部署使用 「 商務規則編輯器 」 工具
在這一課，您可以確認 「 商務規則編輯器 」 工具可建立您的詞彙，並部署您的原則。 詞彙是您在規則組合中使用的詞彙項目集合。 原則是商務規則的版本集合。  
  
### <a name="to-confirm-the-deployment-using-the-business-rule-composer-tool"></a>若要確認部署使用 「 商務規則編輯器 」 工具  
  
1.  開始**商務規則編輯器 」** BizTalk Server 中。  
  
2.  在 [開啟規則存放區] 對話方塊中，按一下**確定**。  
  
3.  在 事實總管 的 商務規則編輯器工具，確認您想要的詞彙，會出現在 事實總管 中，如下圖所示。  
  
     ![](../../adapters-and-accelerators/accelerator-swift/media/tut2-scrn2.gif "Tut2_scrn2")  
  
4.  在 [原則總管] 中，確認 「 商務規則編輯器 」 工具會部署下列原則：  
  
     MT103_Master_Policy  
  
     MT103_Validation_Policy  
  
     SWIFT_NetworkRule149_Policy  
  
     SWIFT_NetworkRule150_Policy  
  
     SWIFT_NetworkRule151_Policy  
  
     SWIFT_NetworkRule175_Policy  
  
     SWIFT_NetworkRule2_Policy  
  
     SWIFT_NetworkRule201_Policy  
  
     SWIFT_NetworkRule202_Policy  
  
     SWIFT_NetworkRule203_Policy  
  
     SWIFT_NetworkRule204_Policy  
  
     SWIFT_NetworkRule205_Policy  
  
     SWIFT_NetworkRule206_Policy  
  
     SWIFT_NetworkRule207_Policy  
  
     SWIFT_NetworkRule209_Policy  
  
     SWIFT_NetworkRule210_Policy  
  
     SWIFT_NetworkRule212_Policy  
  
     SWIFT_NetworkRule213_Policy  
  
     SWIFT_NetworkRule215_Policy  
  
     SWIFT_NetworkRule216_Policy  
  
     SWIFT_NetworkRule217_Policy  
  
     SWIFT_NetworkRule218_Policy  
  
     SWIFT_NetworkRule244_Policy  
  
     SWIFT_NetworkRule245_Policy  
  
     SWIFT_NetworkRule81_Policy  
  
     SWIFT_PartyIdentifier_Policy  
  
     SWIFT_Reference_Policy  
  
### <a name="to-view-a-policy"></a>若要檢視原則  
  
1. 在 商務規則編輯器的 原則總管 窗格中，確定**SWIFT_NetworkRule149_Policy**會展開，然後展開**1.0 版 – 已部署**節點。  
  
2. 按兩下**Validate_MT103**節點以開啟它。  
  
    在畫面右側的 [編輯器] 窗格中，開啟原則。  
  
   請繼續進行[模組 7： 測試有效一般檔案執行個體](../../adapters-and-accelerators/accelerator-swift/module-7-testing-a-valid-flat-file-instance.md)。