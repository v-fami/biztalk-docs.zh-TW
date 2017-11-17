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
# <a name="running-the-transformation-service-sample"></a><span data-ttu-id="c3dba-102">執行 「 轉換服務 」 範例</span><span class="sxs-lookup"><span data-stu-id="c3dba-102">Running the Transformation Service Sample</span></span>
<span data-ttu-id="c3dba-103">您可以執行轉換服務 」 範例使用任何工具或公用程式可執行 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="c3dba-103">You can execute the Transformation Service sample using any tool or utility that can execute Web service methods.</span></span> <span data-ttu-id="c3dba-104">例如，您可以使用出現，可從[CodePlex](http://go.microsoft.com/fwlink/?LinkId=187762) ([http://go.microsoft.com/fwlink/?LinkId=187762](http://go.microsoft.com/fwlink/?LinkId=187762))，或者您可以建立自己的測試用戶端叫用轉換 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c3dba-104">For example, you can use Storm, available from [CodePlex](http://go.microsoft.com/fwlink/?LinkId=187762) ([http://go.microsoft.com/fwlink/?LinkId=187762](http://go.microsoft.com/fwlink/?LinkId=187762)), or you can create your own test client that invokes the Transformation Web service.</span></span>  
  
 <span data-ttu-id="c3dba-105">若要使用.NET Web 服務 Studio 測試正確的轉換服務範例的安裝，輸入將 asmx 轉換 Web 服務的 URL **WSDL 端點**文字方塊，然後再按一下**取得** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c3dba-105">To use the .NET Web Service Studio to test for correct installation of the Transformation Service sample, enter the URL for the ASMX-based Transformation Web service into the **WSDL EndPoint** text box, and then click the **Get** button.</span></span> <span data-ttu-id="c3dba-106">這會產生用戶端的前端介面，可用來呼叫 ESB 轉換 Web 服務，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="c3dba-106">This generates a client front-end interface that you can use to call the ESB Transformation Web Service, as shown in Figure 1.</span></span>  
  
 <span data-ttu-id="c3dba-107">![Transformation Service](../esb-toolkit/media/ch6-transformationservice.gif "第 6 章第 TransformationService")</span><span class="sxs-lookup"><span data-stu-id="c3dba-107">![Transformation Service](../esb-toolkit/media/ch6-transformationservice.gif "Ch6-TransformationService")</span></span>  
  
 <span data-ttu-id="c3dba-108">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="c3dba-108">**Figure 1**</span></span>  
  
 <span data-ttu-id="c3dba-109">**若要測試 「 轉換服務 」 範例使用 Studio.NET Web 服務**</span><span class="sxs-lookup"><span data-stu-id="c3dba-109">**Using the .NET Web Service Studio to test the Transformation Service sample**</span></span>  
  
 <span data-ttu-id="c3dba-110">「 轉換服務 」 範例包含兩個 Microsoft BizTalk 對應和兩個測試 XML 訊息文件。</span><span class="sxs-lookup"><span data-stu-id="c3dba-110">The Transformation Service sample contains two Microsoft BizTalk maps and two test XML message documents.</span></span> <span data-ttu-id="c3dba-111">您可以執行轉換 Web 服務以及名為 TEST_CanonicalOrder_to_OrderConfirmation.xml 和 TEST_RetailOrder_to_CanonicalOrder.xml （位於 \Source\Samples\TransformServices\Test\Data 資料夾） 的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="c3dba-111">You can execute the Transformation Web service with the XML messages named TEST_CanonicalOrder_to_OrderConfirmation.xml and TEST_RetailOrder_to_CanonicalOrder.xml (located in the \Source\Samples\TransformServices\Test\Data folder).</span></span>  
  
 <span data-ttu-id="c3dba-112">服務會自動轉換訊息使用的結構描述 CanonicalOrder.xsd 和 RetailOrder.xsd OrderConfirmation.xsd （位於 \Source\Samples\TransformServices\Source\ESB。TransformServices.Schemas 資料夾） 和 Studio.NET Web 服務將會顯示產生轉換後的訊息。</span><span class="sxs-lookup"><span data-stu-id="c3dba-112">The service will automatically transform the messages using the schemas CanonicalOrder.xsd and RetailOrder.xsd and OrderConfirmation.xsd (located in the \Source\Samples\TransformServices\Source\ESB.TransformServices.Schemas folder), and .NET Web Service Studio will display the resulting transformed messages.</span></span> <span data-ttu-id="c3dba-113">下列程序顯示如何測試 CanonicalOrder_To_OrderConfirmation 對應。</span><span class="sxs-lookup"><span data-stu-id="c3dba-113">The following procedure shows how you can test the CanonicalOrder_To_OrderConfirmation map.</span></span>  
  
 <span data-ttu-id="c3dba-114">**若要測試 GlobalBank.ESB.TransformServices.Maps.CanonicalOrder_To_OrderConfirmation 對應**</span><span class="sxs-lookup"><span data-stu-id="c3dba-114">**To test the GlobalBank.ESB.TransformServices.Maps.CanonicalOrder_To_OrderConfirmation map**</span></span>  
  
1.  <span data-ttu-id="c3dba-115">如果 GlobalBank.ESB 應用程式未執行，使用 BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="c3dba-115">If the GlobalBank.ESB application is not running, use the BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="c3dba-116">輸入下列字串表示的 TEST_CanonicalOrder_to_OrderConfirmation.xml 檔案做為值**訊息**中的參數**輸入**樹狀檢視 Studio.NET Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c3dba-116">Enter the following string representation of the TEST_CanonicalOrder_to_OrderConfirmation.xml file as the value of the **message** parameter in the **Input** tree view of .NET Web Service Studio.</span></span> <span data-ttu-id="c3dba-117">這個字串會符合 GlobalBank.ESB.TransformServices.Schemas.CanonicalOrder 結構描述：</span><span class="sxs-lookup"><span data-stu-id="c3dba-117">This string conforms to the GlobalBank.ESB.TransformServices.Schemas.CanonicalOrder schema:</span></span>  
  
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
  
3.  <span data-ttu-id="c3dba-118">輸入下列字串做為值**mapName**中的參數**輸入**樹狀檢視 Studio.NET Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c3dba-118">Enter the following string as the value of the **mapName** parameter in the **Input** tree view of .NET Web Service Studio.</span></span> <span data-ttu-id="c3dba-119">這是要對訊息執行的 BizTalk 對應的完整輸入的名稱：</span><span class="sxs-lookup"><span data-stu-id="c3dba-119">This is the fully typed name of the BizTalk map to execute against the message:</span></span>  
  
    ```  
    GlobalBank.ESB.TransformServices.Maps.CanonicalOrder_To_  
        OrderConfirmation, GlobalBank.ESB.TransformServices.Maps,   
        Version=1.0.0.0, Culture=neutral, PublicKeyToken=<insertYourPublicKeyTokenHere>  
    ```  
  
4.  <span data-ttu-id="c3dba-120">按一下**Invoke**按鈕以執行 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c3dba-120">Click the **Invoke** button to execute the Web service.</span></span> <span data-ttu-id="c3dba-121">**輸出**測試 方塊中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="c3dba-121">The **Output** test box displays the results.</span></span>