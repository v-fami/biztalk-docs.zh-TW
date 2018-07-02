---
title: 建立 FRR 接收管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive pipelines, creating
- FRR, creating receive pipelines
- creating, receive pipelines
ms.assetid: 5884176b-8522-4dd3-8f93-8695858b59ac
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbf4e735019c5399e1b7f1648f3adbcffe18fed2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970799"
---
# <a name="creating-the-frr-receive-pipeline"></a>建立 FRR 接收管線
若要執行 FIN 回應對帳，您必須建立包含 SWIFT 的 FRR 解碼器和 SWIFT 的 FRR CorrelationSet 解析管線元件，以及 SWIFT 解譯器的接收管線。  

 **摘要**  

 建立接收管線包含下列階段/屬性：  

|階段/屬性|元件/設定|  
|---------------------|------------------------|  
|解譯階段|SWIFT 解譯器|  
|BRE 驗證屬性 （SWIFT 解譯器）|True|  
|XML 驗證屬性 （SWIFT 解譯器）|True|  
|SWIFT 標頭結構描述屬性 （SWIFT 解譯器）|(無)|  
|解碼器階段|SWIFT 的 FRR MQSeries 解碼器|  
|合作對象解析階段|SWIFT 的 FRR 相互關聯集解析程式|  

### <a name="to-create-a-custom-receive-pipeline-for-frr"></a>建立 FRR 自訂接收管線  

1. 在 Visual Studio 的方案總管中以滑鼠右鍵按一下專案包含您[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管線，指向**新增**，然後按一下**新項目**。  

2. 在 加入新項目 對話方塊中，按一下**管線檔案**類別 窗格，然後選取**接收管線**範本 窗格中。  

3. 在 **名稱**方塊中，輸入您的接收管線的名稱，例如**FRRReceivePipeline.btp**。 按一下 **[加入]**。  

   > [!NOTE]
   >  在執行步驟 4 之前，您必須新增[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]FRR 的管線元件 [工具箱] 中所述[新增 SWIFT 管線元件至工具箱](../../adapters-and-accelerators/accelerator-swift/adding-swift-pipeline-components-to-the-toolbox.md)。  

4. 在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下**檢視**，然後按一下**工具箱**。  

5. 從 BizTalk 管線元件 工具箱 窗格中，拖曳**SWIFT 解譯器**要**放置到此處**在下列方塊**解譯**階段管線設計師 」 中的圖形。  

6. 具有**SWIFT 解譯器元件**在管線設計師中，選取**屬性**，確認**BRE 驗證**並**XML 驗證**屬性會設為 **，則為 True**，而**SWIFT 標頭結構描述**屬性設為 **（無）**。  

7. 在 BizTalk 管線元件工具箱拖曳**SWIFT 的 FRR MQSeries 解碼器**要**放置到此處**下面的方塊**解碼器**階段管線設計師 」 中的圖形。  

8. 從 BizTalk 管線元件 工具箱 窗格中，拖曳**FRR 相互關聯集解析程式 SWIFT**來**放置到此處**下面的方塊**解析合作對象**暫置在管線中的圖形設計工具。  

9. 在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下**檔案**，然後按一下**全部儲存**。
