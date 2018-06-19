---
title: 邏輯運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e37cdfc3-66de-4333-84eb-a8765afa8407
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7907d1045fde39d5ece963bd78e00d027e8a9da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262462"
---
# <a name="logical-functoids"></a>邏輯運算質

## <a name="overview"></a>概觀
**邏輯**運算質可用以執行下列類型的作業：  
  
-   在執行階段執行特定邏輯測試。 **邏輯 OR**，**邏輯 NOT**和**邏輯和**運算質可以用來判斷是否記錄建立在目的地執行個體訊息中，如下所示：  
  
     如果 ShipTo**或**orderedby 存在，請建立 billto 地址記錄。  
  
     您也可以使用這些運算質搭配**迴圈**設定多少次記錄迴圈運算質。  
  
-   控制是否在執行階段於目的執行個體訊息中建立特定記錄。 這類運算質**IsNil**，**邏輯數字**，**小於**，和**Greater Than**可用來控制是否建立的記錄。  
  
     如果其中一個這些邏輯運算質的結果會是**True**，就會產生目的地執行個體訊息中對應的記錄。 如果結果為**False**，不會產生目的執行個體訊息中的對應記錄。  
  
 運算質**IsNil**，**邏輯日期**，**存在**，**邏輯 NOT**，**邏輯數字**，和**邏輯字串**只接受一個參數。 運算質**等於**， **Greater Than**， **Greater Than 或 Equal To**，**小於**，**小於或等於**，和**不等於**接受兩個輸入參數。 而、**邏輯和**和**邏輯 OR**運算質接受 2 到 100 個輸入的參數。  
  
 輸出**邏輯**運算質也可以接受做為對應中的其他運算質的輸入。 如果兩個**邏輯**運算質與迴圈運算質會連結在一起，並接著連結到目的結構描述中的記錄，迴圈運算質時，才**邏輯**運算質的輸出，則為**True**。  
  
 您也可以使用**邏輯**運算質**值對應**或**值對應 （簡維）** 運算質來控制是否在目的執行個體訊息中的記錄會建立。  
  
> [!IMPORTANT]
>  如果兩個記錄或欄位在來源結構描述中的連結到兩個不同**邏輯**運算質，然後將每個連結**邏輯**相同記錄與目的結構描述中，運算質的第一個**邏輯**運算質使用中產生可延伸樣式表語言轉換 (XSLT)。 第二個連結，第二個**邏輯**運算質，則會忽略。  
  
> [!NOTE]
>  在比較兩個字串時，邏輯運算質是區分大小寫的。 例如，"Abc" 與 "abc" 不相等。 此規則的例外狀況是當**邏輯**運算質代表布林值的字串比較**True**和**False**。 例如，"True" 與 "true" 相等。  

## <a name="available-functoids"></a>可用的運算質  
 **邏輯**運算質為： 

* 等於
* 大於
* 大於或等於
* IsNil
* 小於
* 小於或等於
* 邏輯 AND
* 日期
* 存在
* 邏輯 NOT
* 數字
* 邏輯 OR
* 字串
* Not Equal

如需詳細資訊，這些函式[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="see-also"></a>另請參閱  
-  [如何新增基本運算質至對應](../core/how-to-add-basic-functoids-to-a-map.md)   
-  **邏輯運算質參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]