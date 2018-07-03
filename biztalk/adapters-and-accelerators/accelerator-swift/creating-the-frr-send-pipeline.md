---
title: 建立 FRR 傳送管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FRR, creating send pipelines
- creating, send pipelines
- send pipelines, creating
ms.assetid: c6cd2047-ea53-425f-80cc-b02a1deb5292
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d16003e489944016a7b840b870d33d8ebcf671d5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005743"
---
# <a name="creating-the-frr-send-pipeline"></a>建立 FRR 傳送管線
若要執行 FIN 回應對帳，您需要建立包含 SWIFTAsmFrrMQSeriesHelper 管線元件，除了 SWIFT 組合器的傳送管線。  

 **摘要**  

 建立傳送管線的下列階段：  

|階段|元件|  
|-----------|---------------|  
|組合階段|SWIFT 組合器|  
|編碼階段|SWIFT 的 Frr MQSeries 傳送元件|  

### <a name="to-create-a-custom-send-pipeline-for-frr"></a>建立 FRR 自訂傳送管線  

1. 在 Visual Studio 的方案總管中以滑鼠右鍵按一下管線專案，指向**新增**，然後按一下**新項目**。  

2. 在 [加入新項目] 對話方塊中，選取**傳送管線**從 [範本] 窗格。  

3. 在 **名稱**方塊中，輸入您的接收管線的名稱，例如**FRRSendPipeline.btp**。 按一下 **[加入]**。  

4. 在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下**檢視**，然後**工具箱**。  

5. BizTalk 管線元件 [工具箱] 拖曳**SWIFT 組合器**要**放置到此處**在下列方塊**組合**階段中的圖形**BizTalk 管線設計工具**。  

6. BizTalk 管線元件 [工具箱] 拖曳**SWIFT Frr MQSeries 傳送元件**要**放置到此處**在下列方塊**編碼**階段中的圖形**BizTalk 管線設計師**。  

7. 在 [BizTalk 總管] 中，以滑鼠右鍵按一下管線專案中，按一下**Undeploy**，然後按一下**是**。  

   > [!NOTE]
   >  解除部署，然後重新部署管線專案之後，您必須重設任何傳送埠或接收位置，其使用先前部署的專案中的管線。  

8. 在 [方案總管] 中，以滑鼠右鍵按一下您管線的專案，然後**建置**。  

9. 建置成功之後，以滑鼠右鍵按一下您管線的專案，然後**部署**。
