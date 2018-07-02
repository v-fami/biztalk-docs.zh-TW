---
title: 第 5 課： 將 SWIFT 解譯器新增至自訂接收管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive pipelines, adding disassembler
- custom pipelines
- disassembler, custom pipelines
- disassembler, adding to pipelines
ms.assetid: 96e26d97-bfab-448f-b7b6-3bc2ec3ccebf
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0af7635b424a74b160991b1d6cfdeb53bfb7f23f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971295"
---
# <a name="lesson-5-adding-the-swift-disassembler-to-a-custom-receive-pipeline"></a>第 5 課： 將 SWIFT 解譯器新增至自訂接收管線
在這一課，您可以新增自訂的 SWIFT 解譯器 (DASM) 到您的管線。 DASM 管線元件會分成個別的文件中的訊息批次中的管線元件。  
  
 MicrosoftBizTalk Server 中提供的 DASM 管線元件如下：  
  
- 一般檔案解譯器  
  
- BizTalk Framework 解譯器  
  
- XML 解譯器  
  
  Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]新增額外的 SWIFT 解譯器。  
  
### <a name="to-add-the-swift-custom-disassembler-to-your-pipeline"></a>將 SWIFT 的自訂解譯器新增至您的管線  
  
1. 從 [檢視] 功能表中，按一下**工具箱**。  
  
2. 從**BizTalk 管線元件 [工具箱]**，按一下**SWIFT 解譯器**將它拖曳到**放在此處**下面的方塊**解譯**階段中的圖形**BizTalk 管線設計師**。 離開**SWIFT 解譯器**中所選取的形狀**BizTalk 管線設計師**。  
  
3. 在 **屬性**窗格中，選取**Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema** for **SWIFT 標頭結構描述**屬性。  
  
   > [!NOTE]
   >  請勿混淆**SWIFT 標頭結構描述**和訊息標頭結構描述。 您必須設定**SWIFT 標頭結構描述**在步驟 3。  
  
4. 在 [**屬性**] 窗格中，請確認**BRE 驗證**屬性設定為 **，則為 True**。  
  
   > [!NOTE]
   >  稍後在本教學課程會遵循說明商務規則引擎 (BRE)。  
  
5. 在 [**屬性**] 窗格中，請確認**XML 驗證**屬性設定為 **，則為 True**。  
  
6. 在 [**屬性**] 窗格中，確定**輸入解除批次處理**屬性設定為**False**。  
  
7. 在 **檔案**功能表上，選取**全部儲存**以儲存變更。  
  
   請繼續進行[第 6 課： 建立自訂傳送管線](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md)。