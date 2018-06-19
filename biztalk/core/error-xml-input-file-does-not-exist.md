---
title: 錯誤-XML 輸入檔案不存在 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.xmlInputFileDoesNotExist
ms.assetid: d222e615-60c8-46f5-a8de-fc59650978c7
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4b70e749565bcf33f99c39faa0653c7fd952e9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245846"
---
# <a name="error---xml-input-file-does-not-exist"></a>錯誤-XML 輸入檔案不存在
**錯誤碼**  
  
 btm1039  
  
 **說明**  
  
 針對「測試對應」作業所指定的 XML 輸入執行個體訊息檔案不存在。 當值**TestMap 輸入**對應屬性設定為 XML 時，您必須指定現有的 XML 執行個體訊息檔案**TestMap 輸入執行個體**對應屬性。  
  
 **使用者動作**  
  
 以滑鼠右鍵按一下相關對應，在 [方案總管] 中，按一下**屬性**，然後在**測試對應**索引標籤中**屬性頁**對話方塊對應中，按一下省略符號 （**...**) 中的值欄位按鈕**TestMap 輸入執行個體**屬性。 使用**選取輸入檔案**對話方塊中，選取現有的 XML 執行個體符合對應的來源結構描述的訊息檔案。 或者，您可以直接在值欄位輸入此 XML 檔案的路徑**TestMap 輸入執行個體**屬性。