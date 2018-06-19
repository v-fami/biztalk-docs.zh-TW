---
title: 進階運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82bf2547-5e44-45f8-b577-97e5760a0339
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5002b639df79ece1019c2d013c128f615517ae5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230390"
---
# <a name="advanced-functoids"></a>進階運算質

## <a name="overview"></a>概觀
根據進階運算質的用途，它們可分屬五個群組：  
  
-   **管理迴圈記錄。** **索引**，**反覆項目**，**迴圈**， **「 Nil 值**，**記錄計數**，**資料表擷取程式**，和**表格迴圈**各種組合使用運算質時輸入執行個體訊息包含區段具有無法預測數目所表示的迴圈，重複項目，來源結構描述中的記錄。  
  
-   **條件式對應。** **值對應**和**值對應 （簡維）** 運算質可用以提供從輸入執行個體訊息到輸出執行個體訊息的條件式對應。 當第一個輸入參數為 True 時，第二個輸入參數會被放入輸出執行個體訊息中的特定項目或屬性；否則，該項目或屬性不會在輸出執行個體訊息中建立。  
  
-   **任意指令碼。** **指令碼處理**運算質可用來執行任意指令碼，或輸入執行個體訊息對應到輸出執行個體訊息時，已編譯程式碼。 此種指令碼或已編譯的程式碼可以建立，以便接受來自來源執行個體訊息、來自設定的常數值、來自其他運算質的輸出或這些組合的輸入參數。  
  
-   **簡單對應。** **大量複製**運算質可以用來複製到任意深度，包括它的子元素，從輸入執行個體訊息到輸出執行個體訊息的整個項目。  
  
-   **疑難排解**。 **Assert**運算質可以用來測試項目值的相關假設。  
  
## <a name="available-functoids"></a>可用的運算質
  
 **進階**運算質為： 

* 判斷提示運算質
* 索引運算質 
* 重複項目運算質 
* 迴圈運算質 
* 大量複製運算質 
* Nil 值運算質
* 記錄計數運算質 
* 指令碼處理運算質 
* 表格迴圈和表格擷取程式運算質
* 值對應運算質
* 值對應 (簡維) 運算質

這些運算質上的更多詳細資料位於**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="next-steps"></a>後續的步驟
  
-   [判斷提示運算質](../core/assert-functoid.md)  
  
-   [索引運算質](../core/index-functoid.md)  
  
-   [反覆項目運算質](../core/iteration-functoid.md)  
  
-   [迴圈運算質](../core/looping-functoid.md)  
  
-   [大量複製運算質](../core/mass-copy-functoid.md)  
  
-   [Nil 值運算質](../core/nil-value-functoid.md)  
  
-   [記錄計數運算質](../core/record-count-functoid.md)  
  
-   [表格迴圈和表格擷取程式運算質](../core/table-looping-and-table-extractor-functoids.md)  
  
-   [值對應運算質](../core/value-mapping-functoid.md)  
  
-   [值對應 （簡維） 運算質](../core/value-mapping-flattening-functoid.md)  
  
-   [指令碼處理運算質](../core/scripting-functoid.md)