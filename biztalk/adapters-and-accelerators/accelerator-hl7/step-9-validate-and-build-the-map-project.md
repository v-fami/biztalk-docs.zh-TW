---
title: 步驟 9： 驗證和建置對應專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- validating, maps
- message enrichment tutorial, maps
- maps, building
- maps, validating
ms.assetid: 10716b0b-702c-48bb-85a9-d58d8f33b68b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1eb4580a9c89534204e492aebdd21988a6ce0e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206470"
---
# <a name="step-9-validate-and-build-the-map-project"></a>步驟 9： 驗證和建置對應專案
在此步驟中，您會使用**驗證對應**命令來判斷對應包含任何內部不一致，或是有其他問題，可避免對其有效地使用對應結構描述。 您也可以建置此專案以產生組件，其中包含您所建立的資源 （結構描述和對應）。 這也可確保您到目前為止完成的工作中沒有編譯錯誤。  
  
### <a name="to-validate-the-map-project"></a>若要驗證對應專案  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**DoorbellMap.btm**對應，，然後按一下 **驗證對應**。  
  
2.  請在 [輸出] 視窗中出現的成功訊息。 因為您不對應至目的結構描述中所有可用的項目，可能會出現一些警告。  
  
     如果沒有成功訊息隨即出現，疑難排解對應專案。  
  
### <a name="to-build-the-map-project"></a>若要建置對應專案  
  
-   在 方案總管 中，以滑鼠右鍵按一下**BTAHL7 專案**，然後按一下 **建置**。 請在 [輸出] 視窗中出現的成功訊息。  
  
     如果沒有成功訊息隨即出現，疑難排解對應專案。  
  
 若要繼續[步驟 10： 建立協調流程](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)