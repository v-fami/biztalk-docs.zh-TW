---
title: 第 6 課： 建立自訂傳送管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom pipelines
- send pipelines, custom pipelines
ms.assetid: 73a3a546-1e43-4b93-87d3-9bfb32685a57
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12afba9368554dc85cf57658f674a088db7580d2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973719"
---
# <a name="lesson-6-creating-a-custom-send-pipeline"></a>第 6 課： 建立自訂傳送管線
在這一課，您可以建立自訂傳送管線，使用 BizTalk 管線設計師。 傳送管線是您在之前的訊息執行的管線[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]傳送訊息至其目的地。  
  
 您設定自訂的管線，以使用 SWIFT 組合器 」 (ASM) 元件。 ASM 採用 XML 格式的訊息，並將轉換或將內容序列化至 SWIFT 的一般檔案。 這項轉換取決於您在中建立的 MT103 結構描述[第 3 課： 加入自訂接收管線](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md)。  
  
### <a name="to-create-a-custom-send-pipeline"></a>若要建立自訂傳送管線  
  
1. 在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTPipelines**專案，指向**新增**，然後按一下**新項目**。  
  
2. 在 [加入新項目-SWIFTPipelines] 對話方塊中，確認**管線檔案**已選取在 [分類] 窗格中，然後選取**傳送管線**從 [範本] 窗格。  
  
3. 在 **名稱**方塊中，輸入**MT103SendPipeline.btp**。  
  
4. 按一下 **新增**BizTalk 管線設計師中開啟空白的管線。  
  
   > [!NOTE]
   >  BizTalk 管線設計師 」 中，會出現空的管線。 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 將方案總管 中的新管線 SWIFTPipelines 專案底下。  
  
   請繼續進行[第 7 課： 將 SWIFT 組合器新增至自訂傳送管線](../../adapters-and-accelerators/accelerator-swift/lesson-7-adding-the-swift-assembler-to-a-custom-send-pipeline.md)。