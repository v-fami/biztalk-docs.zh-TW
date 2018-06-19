---
title: 建立 FRR 接收管線 |Microsoft 文件
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
ms.openlocfilehash: ad31a69d579cf2bbe9f646fc87be1bea9f561a10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210374"
---
# <a name="creating-the-frr-receive-pipeline"></a>建立 FRR 接收管線
若要執行 FIN 回應重新調整，您必須建立包含 SWIFT FRR 解碼器和 SWIFT FRR CorrelationSet 解決器管線元件，除了 SWIFT 解譯器的接收管線。  
  
 **摘要**  
  
 建立接收管線包含下列階段/屬性：  
  
|階段/屬性|元件/設定|  
|---------------------|------------------------|  
|解譯階段|SWIFT 反組譯工具|  
|BRE 驗證屬性 （SWIFT 解譯器）|True|  
|XML 驗證屬性 （SWIFT 解譯器）|True|  
|SWIFT 標頭結構描述屬性 （SWIFT 解譯器）|(無)|  
|解碼器階段|SWIFT FRR MQSeries 解碼器|  
|合作對象解析階段|SWIFT FRR 相互關聯集解析程式|  
  
### <a name="to-create-a-custom-receive-pipeline-for-frr"></a>若要建立自訂接收管線 FRR  
  
1.  在 方案總管的 Visual Studio 中，以滑鼠右鍵按一下專案包含您[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管線，指向**新增**，然後按一下 **新項目**。  
  
2.  在 [加入新項目] 對話方塊中，按一下**管線檔案**在分類窗格中，然後選取**接收管線**在範本窗格中。  
  
3.  在**名稱**方塊中，輸入您的接收管線的名稱，例如**FRRReceivePipeline.btp**。 按一下 **[加入]**。  
  
    > [!NOTE]
    >  在執行步驟 4 之前，您必須新增[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]FRR 中所述，管線元件至工具箱，[加入 SWIFT 管線元件至工具箱](../../adapters-and-accelerators/accelerator-swift/adding-swift-pipeline-components-to-the-toolbox.md)。  
  
4.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下 **檢視**，然後按一下 **工具箱**。  
  
5.  從 BizTalk 管線元件 工具箱 窗格中，拖曳**SWIFT 解譯器**至**放置到此處**下列方塊**解譯**暫置在管線設計師中的圖形。  
  
6.  與**SWIFT 解譯器元件**在管線設計師中，選取**屬性**，確認**BRE 驗證**和**XML 驗證**屬性會設為**True**，而**SWIFT 標頭結構描述**屬性設定為 **（無）**。  
  
7.  在 BizTalk 管線元件工具箱拖曳**SWIFT FRR MQSeries 解碼器**至**放置到此處**下列方塊**解碼器**暫置在管線設計師中的圖形。  
  
8.  從 BizTalk 管線元件 工具箱 窗格中，拖曳**SWIFT FRR 相互關聯集解析程式**至**放置到此處**下列方塊**解析合作對象**暫置在管線中的圖形設計工具。  
  
9. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下 **檔案**，然後按一下 **全部儲存**。