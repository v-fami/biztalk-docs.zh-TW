---
title: 累計運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0549867-e0e4-4cdb-aae0-cadc99088e03
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dffa6448511eca4d101423dbe356b82ff38aebb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004391"
---
# <a name="cumulative-functoids"></a>累計運算質

## <a name="overview"></a>概觀
**累計**運算質會減少一系列的值設為單一的值，例如總和、 串連的字串或平均。  

 所有**累計**運算質都接受兩個輸入參數：  

1. 要累計的值。 此值是所有數字**累計**以外的運算質**累計串連**運算質預期字串值。 值的連結，通常是從**Field 屬性**，**欄位項目**，或**記錄**節點 (使用其**混合**屬性設定為  **，則為 true**)。  

   > [!NOTE]
   >  如果沒有上階**記錄**迴圈中的結構描述樹狀結構節點、 使用**累計**運算質不需要。  

2. 累計此值的範圍。 此引數是選擇性的。 此引數指示要累計的值所必須緊密相關的程度。  

   下表顯示範圍參數值及其效果：  

|範圍參數值|效果|  
|-----------------------------|------------|  
|0 (零)|累計整個執行個體訊息的值。 預設值。|  
|1 (一)|以相同父項目累計項目值或屬性值。|  
|2|以相同父父代項目累計項目值或屬性值。|  
|3 或以上|累計依據先前模式逐步擴大範圍的項目值或屬性值 (父父父代、父父父父代等)。|  

## <a name="example"></a>範例  
 使用的範例**累計**運算質可能成本加總訂單。 下列程式碼為訂單範例。  

```  
<ns0:PurchaseOrder xmlns:ns0="http://CumulativeFunctoid.PurchaseOrder">  
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

 **Max Occurs**屬性**項目**記錄，當然會**unbounded**。 這表示 [Item] 記錄會重複，而 BizTalk 對應工具將此記錄編譯成迴圈。  

 下圖顯示對應，使用**乘法**運算質並**累計總和**彙總的項目記錄的運算質，從內送訂單，並將結果輸出**POTotal**欄位：  

 ![顯示使用 「 累計總和 」 運算質的對應。](../core/media/cumulativefunctoids.gif "cumulativefunctoids")  


 此對應使用先前的資料與預設範圍參數值 0 (零) 產生下列輸出：  

```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
</ns0:SummedPO>  
```  

 在此範例中，所有**項目**記錄之下**LineItems**記錄都參與累計，範圍參數的預設值表示累計整個訊息的值。 **價格**並**Quantity**欄位傳送到**乘法**運算質。 輸出**乘法**運算質會變成輸入**累計總和**運算質。 輸出**累計總和**運算質是累計的值為**項目**記錄會周遊輸入的訂單中。  

> [!NOTE]
>  輸入的累計彙總發生在父記錄，由此產生輸入連結。 即使**累計**運算質從另一個運算質取得其輸入，累計彙總都會經由輸入連結的父記錄輸入到運算質**累計**運算質。  

 將範圍參數變更為 1 (一) 並稍微修改輸出結構描述，得到類似下面的輸出：  

```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <ItemTotal>1999.95</ItemTotal>  
    <ItemTotal>39.5</ItemTotal>  
</ns0:SummedPO>  
```  

 將範圍參數設為 1 (一) 表示以相同父項累計項目或屬性的值。 以下**價格**並**數量**欄位具有**項目**當做父代，以便針對每個運算質加總的值**項目**。  

 若將範圍參數設為 2，則此運算質會以相同父父代累計項目或屬性的值。 祖系**價格**並**Quantity**欄位是**LineItems**記錄。 因為只有一個**LineItems**記錄執行個體訊息中，結果就是使用預設值：  

```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
</ns0:SummedPO>  
```  

> [!NOTE]
>  累計運算質 (除了**累計字串**運算質) 忽略非數值輸入。 例如，輸入值 "three" 會被忽略。  

 **累計平均**，**累計最小值**，並**累計最大值**運算質的行為類似於**累計總和**運算質。 **累計字串**串連字串，而不是彙總數值。  

## <a name="available-functoids"></a>可用的運算質

 **累計**運算質為： 

* 累計平均
* 累計串連
* 累計最大值
* 累計最小值
* 累計總和

更多詳細資料，這些運算質上[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

## <a name="see-also"></a>另請參閱  
- [如何新增基本運算質至對應](../core/how-to-add-basic-functoids-to-a-map.md)   
- **累計運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
