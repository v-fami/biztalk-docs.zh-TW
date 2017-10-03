---
title: "私用程序教學課程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private processes, tutorial
- private process tutorial
- tutorials, private process tutorial
ms.assetid: 58affc48-af73-406e-895f-696bc284d945
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c017d8b9b52c1f477aba62308ca2e65a1550564
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="private-process-tutorial"></a>私用程序教學課程
本教學課程包含了使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 的完整端點對端點解決方案。 其中詳細描述必須遵循的步驟，透過在兩家虛構公司之間建立交易實例，藉此實作 RosettaNet 相容解決方案：賣方組織 Contoso 與買方組織 Fabrikam。  
  
 此教學課程實作的實例會使用「3A2 - 價格與可用性」交易夥伴介面程序 (PIP)。 在開始採購之前，買方 Fabrikam 會先傳送「3A2 - 價格與可用性」要求給賣方 Contoso。 此 PIP 讓 Fabrikam 能夠取得特定產品的相關資訊，接著 Fabrikam 會透過商務規則處理那些資訊以決定是否採購產品。 下圖顯示啟動者組織與回應者組織在 3A2 PIP 交換期間的通訊模式。  
  
 ![&#60;沒有變更 &#62;] (../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-intro-eetut-3a2flow.gif "RN3_Intro_EETut_3A2Flow")  
  
 此教學課程會將重點放在 Contoso 解決方案。 其中摘列建立 RosettaNet 架構解決方案的各種不同層面，包括整合 ERP、強制執行商務原則、自訂私用程序及升級安全通訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [準備私用程序教學課程](../../adapters-and-accelerators/accelerator-rosettanet/preparing-for-the-private-process-tutorial.md)  
  
-   [建立 Contoso 解決方案](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-contoso-solution.md)  
  
-   [建立 Fabrikam 解決方案](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-fabrikam-solution.md)  
  
-   [測試方案](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-solution.md)