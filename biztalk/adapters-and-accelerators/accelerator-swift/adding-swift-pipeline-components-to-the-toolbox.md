---
title: SWIFT 的管線元件新增至工具箱 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- toolbox, adding pipelines
- pipelines, adding to toolbox
ms.assetid: 3821c10e-ef9b-4657-b934-cff6d096f654
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aaef345994a1d849e09025d9ad1bb0f133c1b224
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22208926"
---
# <a name="adding-swift-pipeline-components-to-the-toolbox"></a>SWIFT 的管線元件新增至工具箱
您必須加入 SWIFT 的管線元件[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]工具箱中，好讓您可以建立使用這些元件的自訂管線。 如此才能建立 Message Repair 和 New Submission 或 FIN 回應對帳的管線。  
  
 **摘要**  
  
 新增下列 SWIFT 的管線元件才能[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]工具箱：  
  
-   SWIFT 的組譯工具 （適用於 Message Repair 和 New Submission 或 FIN 回應對帳 (FRR)）  
  
-   （針對 Message Repair 和 New Submission 或 FRR） SWIFT 反組譯工具  
  
-   SWIFT Frr 相互關聯集 （適用於 FRR) 解析程式  
  
-   （適用於 FRR) SWIFT Frr MQSeries 解碼器  
  
-   （適用於 FRR) SWIFT Frr MQSeries 傳送元件  
  
### <a name="to-add-a4swift-pipeline-components-to-the-toolbox"></a>將 A4SWIFT 管線元件新增至工具箱  
  
1.  在 Visual Studio 中，在**工具**功能表上，按一下 **選擇工具箱項目**。  
  
2.  在**選擇工具箱項目**對話方塊**BizTalk 管線元件**索引標籤上，選取**SWIFT 組譯工具**和**SWIFT 解譯器**. 如果您將使用 FIN 回應重新調整，選取**SWIFT Frr 相互關聯集解析程式**， **SWIFT Frr MQSeries 解碼器**，和**SWIFT Frr MQSeries 傳送元件**。  
  
3.  按一下 **[確定]**。