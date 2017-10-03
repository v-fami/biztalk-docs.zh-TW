---
title: "如何編輯 XPath 選取器以處理多個記錄 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, editing multiple records
- Business Rules Framework, code samples
- Business Rules Framework, programming
ms.assetid: ef7e1f8d-2e29-4cef-b558-0090648bffc0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34c9b45e3fce9f4ad5730d7f03d2a568b3701742
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-edit-xpath-selector-to-process-multiple-records"></a>如何編輯 XPath 選取器以處理多個記錄
不同的子 TypedXmlDocuments 時，會建立 TypedXmlDocument 判斷提示至引擎。請參閱[Assert](../core/assert.md)。 此引擎根據規則中所定義的 XPath 選取器以決定建立哪個子 TypedXmlDocuments。 當您在編輯器中建置規則時，XPath 選取器的值預設為在 [事實總管] 的 [XML 結構描述] 索引標籤中選取的節點上方的節點。 XPath 欄位的值預設為選取的節點本身，相對於其父節點而言。  
  
 在某些情況下，您可能要自訂建置規則時編輯器所建立的預設 XPath。 假設下列範例 XML 文件。  
  
```  
<Order>  
   <Orderline>  
      <Hat style="Baseball">                        
         <Cost>10</Cost>  
      </Hat>  
      <Shirt color="Black">  
         <Cost>20</Cost>  
      </Shirt>  
      <Total></Total>  
   </Orderline>  
   <Orderline>  
      <Hat style="Bowler">                        
         <Cost>20</Cost>  
      </Hat>  
      <Shirt color="Red">  
         <Cost>20</Cost>  
      </Shirt>  
      <Total></Total>  
   </Orderline>  
</Order>  
```  
  
 假設您要建置計算每個 Orderline 的 Total 值的規則。 您的規則看起來將如下所示。  
  
 IF 1==1  
  
 然後**/順序/Orderline/**總計 = (**/順序/Orderline/Hat/**成本 + **/順序/Orderline/Shirt/**成本)  
  
 XPath 的粗體字部分表示 [選取器] 部分，其餘則代表 [欄位] XPath。 這些是由編輯器建置的預設。 執行此原則，不過，會導致建立 6 個物件 — 2 個 Orderline 物件、 2 個 Hat 物件以及 2 個 Shirt 物件。 會為 Hat 與 Shirt 物件的每個組合計算 Orderline 總計，而且總計永遠會設為相同值，該值為上次執行規則的結果。 此規則會引發 8 次。 這並非此實例的目的。  
  
 一個解決方式是依照下列內容編輯 XPath 值。  
  
 IF 1==1  
  
 然後**/順序/Orderline/**總計 = (**/順序/Orderline/**Hat/成本 + **/順序/Orderline/**Shirt/成本)  
  
 三個欄位的選取器 XPath 值已經全部設定為相同的 /Order/Orderline 值，而欄位 XPath 值也已經分別編輯。 這可藉由在 [XML 結構描述] 索引標籤中選取節點時，於 [屬性] 視窗內變更 [XPath 選取器] 與 [XPath 欄位] 值來完成。這應該在拖曳欄位至規則引數之前完成。  
  
 利用此變更來執行原則，將使得每個 Orderline 的 [總計] 值可依據該 Orderline 中 Shirt 與 Hat 節點的 [成本] 值正確計算。