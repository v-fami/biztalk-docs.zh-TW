---
title: "如何設定節點階層比對 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5302e194-cbc7-4d26-b25b-eb4e38abfe23
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d29a794db6f34d7e8251c32bbf428b3a336601fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-node-hierarchy-matching"></a>如何設定節點階層比對
在對應中建立連結時，BizTalk 對應工具會自動建立編譯器連結以實作已建立的連結。 **目標連結**連結的屬性會控制如何在 BizTalk 對應工具建立編譯器連結。 本主題提供如何設定目標連結的相關資訊。  
  
 **來源連結**屬性指定值，如何從來源節點擷取並套用至目的地節點。 如需如何設定來源連結的詳細資訊，請參閱[如何設定來源連結編譯器值](../core/how-to-set-the-source-links-compiler-value.md)。  
  
> [!NOTE]
>  此作業需要執行中的 BizTalk 對應工具。。  
  
### <a name="to-set-the-target-links-property"></a>設定目標連結屬性  
  
1.  在對應格線頁中，按一下要設定目標連結屬性的連結。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]**屬性**視窗中，將**目標連結**屬性設為其中包含下列選項：  
  
    -   **簡維連結。** 來源記錄節點中的階層簡維至目的結構描述中的連結到記錄節點。  
  
        > [!NOTE]
        >  根據預設，BizTalk 對應工具設定**目標連結**屬性**壓平合併**。  
  
    -   **連結由上往下比對。** 節點比對是由上往下以層級對層級的比對方式執行。  
  
    -   **比對下往上連結。** 節點比對是由下往上以層級對層級的比對方式執行。  
  
## <a name="see-also"></a>另請參閱  
 [節點階層層級比對](../core/node-hierarchy-level-matching.md)   
 [編譯器指示詞和連結](../core/compiler-directives-and-links.md)   
 [使用連結指定記錄和欄位對應](../core/using-links-to-specify-record-and-field-mappings.md)