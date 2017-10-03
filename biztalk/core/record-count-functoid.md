---
title: "記錄計數運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Max Occurs property
- Record Count functoids
ms.assetid: e6aab13f-afbe-4401-abbe-020570e2ff16
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87653709bf5d52c21537064bad286078ad625cf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="record-count-functoid"></a>記錄計數運算質
**記錄計數**運算質會計算在輸入執行個體訊息中的記錄。  
  
 **記錄計數**運算質有一個輸入和一個輸出。 輸入為來源結構描述中迴圈記錄的連結。 輸出**記錄計數**運算質是實際輸入執行個體訊息中迴圈記錄的計數。  
  
 迴圈記錄對應到輸入執行個體訊息中重複次數無法預測的項目。 例如，在採購單，**項目**項目可能會發生多次。 此外，**項目**項目可能包含產品、 描述、 價格以及數量。 下列程式碼是此類訂單的簡化範例。  
  
```  
<ns0:PurchaseOrder xmlns:ns0="http://RecordFunctoid.PurchaseOrder">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <LineItems>  
        <Item>  
            <Product>Laptop Computer</Product>  
            <Description>Thin profile laptop</Description>  
            <Price>1999.95</Price>  
            <Quantity>1</Quantity>  
        </Item>  
        <Item>  
            <Product>Monitor Swipes</Product>  
            <Description>Disposable monitor swipes</Description>  
            <Price>3.95</Price>  
            <Quantity>10</Quantity>  
        </Item>  
    </LineItems>  
</ns0:PurchaseOrder>  
```  
  
 **Max Occurs**屬性**項目**記錄設定為 unbounded。 這表示**項目**記錄會重複，而 BizTalk 對應工具會編譯為迴圈這筆記錄。  
  
 假設您想要尋找的總數**項目**採購訂單輸入執行個體中的項目訊息，並將結果放在輸出執行個體訊息中的欄位。  
  
 下圖顯示**記錄計數**運算質，計算的內送訂單中的項目數目，並將該值放入**ItemCount**欄位**SummedPO**輸出執行個體訊息。  
  
 ![地圖顯示的記錄計數運算質使用。] (../core/media/recordcountfunctoid.gif "recordcountfunctoid")  
記錄計數運算質對應  
  
 請注意， **Max Occurs**屬性**項目**會記錄**unbounded**。 這表示**項目**記錄會重複，而 BizTalk 對應工具會編譯為迴圈這筆記錄。  
  
 如上述範例訂單執行個體訊息，其中包含兩個**項目**項目、 值**ItemCount**欄位將會設定為 2。  
  
```  
<ns0:SummedPO xmlns:ns0="http://RecordCountFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
    <ItemCount>2</ItemCount>  
</ns0:SummedPO>  
```  
  
> [!NOTE]
>  您也可以使用**記錄計數**運算質計算重複的欄位項目。 並不僅限計算記錄。  
  
## <a name="see-also"></a>另請參閱  
 [如何新增記錄計數運算質至對應](../core/how-to-add-record-count-functoids-to-a-map.md)   
 [進階運算質](../core/advanced-functoids.md)   
 [索引運算質](../core/index-functoid.md)   
 [反覆項目運算質](../core/iteration-functoid.md)   
 [迴圈運算質](../core/looping-functoid.md)