---
title: "執行 「 轉換服務 」 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42064d32-5ec5-4219-a338-c5769969b958
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ac733f3164a319ed0b86e0f609de8ccd03bdbca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-transformation-service-sample"></a>執行 「 轉換服務 」 範例
您可以執行轉換服務 」 範例使用任何工具或公用程式可執行 Web 服務方法。 例如，您可以使用出現，可從[CodePlex](http://go.microsoft.com/fwlink/?LinkId=187762) ([http://go.microsoft.com/fwlink/?LinkId=187762](http://go.microsoft.com/fwlink/?LinkId=187762))，或者您可以建立自己的測試用戶端叫用轉換 Web 服務。  
  
 若要使用.NET Web 服務 Studio 測試正確的轉換服務範例的安裝，輸入將 asmx 轉換 Web 服務的 URL **WSDL 端點**文字方塊，然後再按一下**取得** 按鈕。 這會產生用戶端的前端介面，可用來呼叫 ESB 轉換 Web 服務，如圖 1 所示。  
  
 ![Transformation Service](../esb-toolkit/media/ch6-transformationservice.gif "第 6 章第 TransformationService")  
  
 **圖 1**  
  
 **若要測試 「 轉換服務 」 範例使用 Studio.NET Web 服務**  
  
 「 轉換服務 」 範例包含兩個 Microsoft BizTalk 對應和兩個測試 XML 訊息文件。 您可以執行轉換 Web 服務以及名為 TEST_CanonicalOrder_to_OrderConfirmation.xml 和 TEST_RetailOrder_to_CanonicalOrder.xml （位於 \Source\Samples\TransformServices\Test\Data 資料夾） 的 XML 訊息。  
  
 服務會自動轉換訊息使用的結構描述 CanonicalOrder.xsd 和 RetailOrder.xsd OrderConfirmation.xsd （位於 \Source\Samples\TransformServices\Source\ESB。TransformServices.Schemas 資料夾） 和 Studio.NET Web 服務將會顯示產生轉換後的訊息。 下列程序顯示如何測試 CanonicalOrder_To_OrderConfirmation 對應。  
  
 **若要測試 GlobalBank.ESB.TransformServices.Maps.CanonicalOrder_To_OrderConfirmation 對應**  
  
1.  如果 GlobalBank.ESB 應用程式未執行，使用 BizTalk 管理主控台來啟動它。  
  
2.  輸入下列字串表示的 TEST_CanonicalOrder_to_OrderConfirmation.xml 檔案做為值**訊息**中的參數**輸入**樹狀檢視 Studio.NET Web 服務。 這個字串會符合 GlobalBank.ESB.TransformServices.Schemas.CanonicalOrder 結構描述：  
  
    ```  
    <ns0:CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1"   
        Status="Status_2" xmlns:ns0=  
        "http://schemas.globalbank.esb.transformservices.com">  
        <OrderHeader><CustomerName>CustomerName_0</CustomerName>  
        <CustomerID>CustomerID_0</CustomerID><ShipToLine1>  
        ShipToLine1_0</ShipToLine1><ShipToLine2>ShipToLine2_0  
        </ShipToLine2><BillToLine1>BillToLine1_0</BillToLine1>  
        <BillToLine2>BillToLine2_0</BillToLine2><OrderTotal>OrderTotal_0  
        </OrderTotal></OrderHeader><OrderDetails><LineItem Qty="Qty_0"   
        PartNum="PartNum_1" Description="Description_2"   
        UnitPrice="UnitPrice_3" Ext="Ext_4" /></OrderDetails>  
        <B2BPartnerDetails CreditLimit="CreditLimit_0"   
        AccountBalance="AccountBalance_1"   
        LastOrderedData="LastOrderedData_2"   
        DiscountLevel="DiscountLevel_3" /></ns0:CanonicalOrder>  
    ```  
  
3.  輸入下列字串做為值**mapName**中的參數**輸入**樹狀檢視 Studio.NET Web 服務。 這是要對訊息執行的 BizTalk 對應的完整輸入的名稱：  
  
    ```  
    GlobalBank.ESB.TransformServices.Maps.CanonicalOrder_To_  
        OrderConfirmation, GlobalBank.ESB.TransformServices.Maps,   
        Version=1.0.0.0, Culture=neutral, PublicKeyToken=<insertYourPublicKeyTokenHere>  
    ```  
  
4.  按一下**Invoke**按鈕以執行 Web 服務。 **輸出**測試 方塊中顯示結果。