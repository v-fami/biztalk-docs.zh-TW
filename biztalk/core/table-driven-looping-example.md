---
title: 表格驅動迴圈範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Table Extractor functoids, code sample
- Table Looping functoids
- Table Extractor functoids
- Table Looping functoids, about Table Looping functoids
- Table Extractor functoids, about Table Extractor functoids
- code samples, Table Looping functoids
- Table Looping functoids, code sample
- code samples, Table Extractor functoids
ms.assetid: d890bdb1-12a6-4001-9748-737b1f2bab79
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6989ac7e64cf28784d08f26aaf9e7af3a166a28
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="table-driven-looping-example"></a>表格驅動迴圈範例
這個部分扼要說明對應使用 **表格迴圈** 和 **表格抽選程式** 運算質。 如需選取的詳細資訊，放置、 連結及設定運算質，請參閱[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)。  
  
 假設您有一個位址清單，需要用在需要有個別運送和帳單寄送地址的文件。 這些位址的顯示方式可能會與下列程式碼類似。  
  
```  
<ns0:Root xmlns:ns0="http://TableLoopingSample.Addresses">  
    <Address>  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City>  
        <State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address>  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
</ns0:Root>  
```  
  
 輸出可能採取的一種格式會是下列程式碼，雖然地址會重複，但是透過屬性所產生。  
  
```  
<ns0:Root xmlns:ns0="http://TableLoopingSample.POAddresses">  
    <Address Type="ShipTo">  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City>  
        <State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address Type="BillTo">  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City><State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address Type="ShipTo">  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
    <Address Type="BillTo">  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
</ns0:Root>  
```  
  
 `The following figure shows a map using the`  **資料表** **迴圈**  `functoid and`  **資料表** **擷取程式**  `functoids to generate the desired output instance message.`  
  
 ![對應表格迴圈和表格擷取程式運算質](../core/media/tableloopingextractorfunctoid.gif "tableloopingextractorfunctoid")  
表格迴圈和擷取程式運算質  
  
 請注意， **表格迴圈** 運算質的輸入和輸出結構描述中的記錄層級項目連結。 該連結可確保封入結構的建立，並因而在記錄內建立項目。 也請注意，有一個 **表格抽選程式** 運算質的輸出結構描述中每個欄位。  
  
 輸入結構描述中的記錄連結是中的第一個參數**設定\<運算質\>運算質** 對話方塊。  
  
 第二個參數是運算質之格線資料表中的資料行數目︰ 各一個資料行地址類型、 名稱、 街道、 縣 （市）、 狀態和郵遞區號。 而在第二個參數後面的是可能出現在格線資料表中的所有值清單。 這些包含地址類型 ("ShipTo"、"BillTo") 的字串常數，以及地址欄位的連結。 請注意，地址欄位的連結會具有名稱。 命名對應中的連結可以簡化資料表的建構。 否則，完整的路徑會顯示在 **設定表格迴圈運算質** 對話方塊。  
  
 設定之後 **表格迴圈** 運算質，您可以建構資料表使用 **設定表格迴圈運算質** 對話方塊。 [] 對話方塊出現時按一下省略符號 (**...**) 相關聯的按鈕 **表格迴圈格線** 屬性 **屬性** 視窗。  
  
 請注意，有六個資料行中所指定 **設定表格迴圈運算質** 對話方塊︰ 輸出結構描述中每個欄位的一個資料行。 下拉式清單中顯示的欄位中的第三個以及下列參數所指定的可能值 **設定表格迴圈運算質**  對話方塊。 資料表具有兩個資料列，且在輸出結構描述中的每個記錄類型都會一個資料列。 因為有兩個資料列，所以此對應會為每個輸入記錄產生兩個記錄。 如果有四個資料列，則每個輸入記錄都會有四個輸出記錄。  
  
 做為 **表格迴圈** 運算質採用每一筆記錄，它會填入記錄值的資料表，並再一次傳送一個資料列 **表格抽選程式** 運算質。 **表格抽選程式** 運算質每個資料表資料列中擷取一個值，並將它傳遞到輸出執行個體訊息中的連結欄位。  
  
## <a name="see-also"></a>另請參閱  
 [表格迴圈運算質](../core/table-looping-functoid.md)   
 [表格抽選程式運算質](../core/table-extractor-functoid.md)   
 [表格驅動迴圈組態](../core/table-driven-looping-configuration.md)   
 [如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)   
 [進階運算質](../core/advanced-functoids.md)   
 [索引運算質](../core/index-functoid.md)   
 [反覆項目運算質](../core/iteration-functoid.md)   
 [迴圈運算質](../core/looping-functoid.md)   
 [記錄計數運算質](../core/record-count-functoid.md)