---
title: "第 5 課： 加入自訂接收管線 SWIFT 解譯器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines, adding disassembler
- custom pipelines
- disassembler, custom pipelines
- disassembler, adding to pipelines
ms.assetid: 96e26d97-bfab-448f-b7b6-3bc2ec3ccebf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04feeaf88cef2f4ab876b22eda1b1e060a1e0173
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-5-adding-the-swift-disassembler-to-a-custom-receive-pipeline"></a>第 5 課： 加入自訂接收管線 SWIFT 反組譯工具
在這一課，您可以加入自訂 SWIFT 的解譯器 (DASM) 到您的管線。 DASM 管線元件是將一批訊息分割成個別文件的管線元件。  
  
 DASM 管線元件中提供[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]是：  
  
-   一般檔案解譯器  
  
-   BizTalk Framework 解譯器  
  
-   XML 解譯器  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]新增額外的 SWIFT 解譯器。  
  
### <a name="to-add-the-swift-custom-disassembler-to-your-pipeline"></a>將 SWIFT 的自訂解譯器新增至您的管線  
  
1.  從 檢視 功能表中，按一下 **工具箱**。  
  
2.  從**BizTalk 管線元件工具箱**，按一下  **SWIFT 解譯器**將它拖曳到**放置到此處**下列方塊**解譯**階段中的圖形**BizTalk 管線設計師**。 保留**SWIFT 解譯器**圖形中選取**BizTalk 管線設計師**。  
  
3.  在**屬性**窗格中，選取**Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema**如**SWIFT 標頭結構描述**屬性。  
  
    > [!NOTE]
    >  請勿混淆**SWIFT 標頭結構描述**和訊息標頭結構描述。 您必須設定**SWIFT 標頭結構描述**步驟 3 中。  
  
4.  在**屬性** 窗格中，確定**BRE 驗證**屬性設定為**True**。  
  
    > [!NOTE]
    >  稍後在本教學課程會遵循說明商務規則引擎 (BRE)。  
  
5.  在**屬性** 窗格中，確定**XML 驗證**屬性設定為**True**。  
  
6.  在**屬性** 窗格中，確定**輸入解除批次處理即將**屬性設定為**False**。  
  
7.  在**檔案**功能表上，選取**全部儲存**以儲存變更。  
  
 若要繼續[第 6 課： 建立自訂傳送管線](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md)。