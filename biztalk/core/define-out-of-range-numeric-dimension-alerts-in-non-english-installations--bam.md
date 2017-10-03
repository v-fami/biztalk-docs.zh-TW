---
title: "如何在非英文的安裝中定義超出範圍的數字維度警示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f1e0373-eadf-4c6d-9a38-a34d847f310f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea63008680c026eded843e32a7b2c6ff26dc0bf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-define-out-of-range-numeric-dimension-alerts-in-non-english-installations"></a>如何在非英文的安裝中定義超過範圍的數字維度警示
當設定包含超出定義的數字範圍維度，在非英文的安裝上的值條件的警示，您必須手動修改 BAM 定義的當地語系化版本字串的**超出範圍**.  
  
 下表列出值超過範圍的範例。  
  
|語言代碼|當地語系化字串|  
|-------------------|----------------------|  
|CN|超出范围|  
|DE|Außerhalb des gültigen Bereichs|  
|ES|Fuera de rango|  
|FR|hors limites|  
|IT|Fuori intervallo|  
|JA|範囲外|  
|KO|범위를 벗어남|  
|TW|超過範圍|  
  
### <a name="to-define-out-of-range-alerts-in-non-english-installations"></a>若要在非英文的安裝中定義超過範圍的警示  
  
1.  瀏覽至包含 BAM 定義 xml 檔案的資料夾。  
  
2.  利用文字編輯器或 XML 編輯器開啟 BAM 定義檔。  
  
3.  找出數字維度的 Slicer 維度。 例如，如果 slicer 維度名稱為**Alerts_NumDim**，您必須尋找下列節點：  
  
    ```  
    <SlicerDimension Name="Alerts_NumDim">  
    <Level Name="(Out of Range)" />  
    </SlicerDimension>  
    ```  
  
4.  變更**超出範圍**至適當的字串值的當地語系化字串。  
  
5.  儲存檔案並部署定義。  
  
## <a name="see-also"></a>另請參閱  
 [何謂 BAM 定義結構描述](../core/what-is-a-bam-definition-schema.md)   
 [如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md)