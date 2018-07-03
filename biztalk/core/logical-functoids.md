---
title: 邏輯運算質 |Microsoft Docs
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
ms.openlocfilehash: 873e2b0ea1189586f9cabfbcb43c6ef276f34e0f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007591"
---
# <a name="logical-functoids"></a>邏輯運算質

## <a name="overview"></a>概觀
**邏輯**運算質用來執行下列類型的作業：  

- 在執行階段執行特定邏輯測試。 **邏輯 OR**，**邏輯 NOT**並**邏輯和**運算質可用來判斷是否要將記錄建立在目的地執行個體訊息中，如下所示：  

   若 ShipTo**或**orderedby 存在，請建立 BillTo 地址記錄。  

   您也可以搭配使用這些運算質**迴圈**設定多少次記錄迴圈運算質。  

- 控制是否在執行階段於目的執行個體訊息中建立特定記錄。 等運算質**IsNil**，**數字**，**小於**，以及**Greater Than**可用來控制是否建立記錄。  

   其中一個這些邏輯運算質的結果是否 **，則為 True**，就會產生目的地執行個體訊息中對應的記錄。 如果結果是**False**，目的地執行個體訊息中對應的記錄不會產生。  

  運算質**IsNil**，**邏輯日期**，**存在**，**邏輯 NOT**，**邏輯數字**，並**邏輯字串**只接受一個參數。 運算質**相等**， **Greater Than**， **Greater Than 或 Equal To**，**小於**，**小於或等於**，並**不等於**接受兩個輸入參數。 而，則**邏輯與**並**邏輯 OR**運算質接受 2 到 100 個輸入的參數。  

  輸出**邏輯**運算質也可接受做為對應中的其他運算質的輸入。 如果兩個**邏輯**運算質與迴圈運算質連結在一起，並接著連結至目的結構描述中的記錄，則會在使用 「 迴圈 」 運算質時，才**邏輯**運算質的輸出，則**True**。  

  您也可以使用**邏輯**運算質**值對應**或是**值對應 （簡維）** 運算質來控制是否在目的執行個體訊息中的記錄會建立。  

> [!IMPORTANT]
>  如果兩個記錄或欄位在來源結構描述中的連結至兩個不同**邏輯**運算質，然後將每個連結**邏輯**目的結構描述中相同的資料錄的運算質的第一個**邏輯**運算質會使用在產生可延伸樣式表語言轉換 (XSLT)。 第二個連結，第二個**邏輯**運算質，則會忽略。  

> [!NOTE]
>  在比較兩個字串時，邏輯運算質是區分大小寫的。 例如，"Abc" 與 "abc" 不相等。 此規則的例外狀況是當**邏輯**運算質比較代表布林值的字串 **，則為 True**並**False**。 例如，"True" 與 "true" 相等。  

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

更多詳細資料，這些函式[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

## <a name="see-also"></a>另請參閱  
- [如何新增基本運算質至對應](../core/how-to-add-basic-functoids-to-a-map.md)   
- **邏輯運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
