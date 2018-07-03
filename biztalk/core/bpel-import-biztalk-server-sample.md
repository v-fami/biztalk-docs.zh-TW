---
title: BPEL 匯入 （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BPEL, orchestrations
- examples, orchestrations
- examples, BPEL Import Wizard
- BPEL, examples
- BPEL Import Wizard, examples
- BPEL Import Wizard, orchestrations
ms.assetid: 3fc70608-ccd9-4249-b238-c09fc6551db1
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62eb5603ffca6f22e0e22f185886d0cfefb17746
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012551"
---
# <a name="bpel-import-biztalk-server-sample"></a>BPEL 匯入 （BizTalk Server 範例）
BPEL 匯入範例示範如何從商務程序執行語言 (Business Process Execution Language, BPEL) 程序描述及其相關成品建立協調流程。  

## <a name="what-this-sample-does"></a>此範例的用途  
 Wide World Importers 是一個為零售商提供自動化出貨服務的託運公司。 具體來說，Wide World Importers 可讓零售商可以：  

- 要求訂單出貨  

- 追蹤出貨  

- 確認出貨  

- 確認出貨的發票開立和付款  

  雖然這些服務的可用性可透過 Web 服務描述語言 (WSDL) 文件來說明，但 BPEL 文件描述了產品公司應該如何呼叫服務以及應該如何從 Wide World Importers 取得回應的典型方式。  

  當 Northwind Traders 雇用 Wide World Importers 來處理其出貨時，他們會收到一個 BPEL 檔案，以及一些描述整個互動的相關成品。 Northwind Traders 可使用該 BPEL 檔案建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式 (BPELShipping)，以透過 Wide World Importers 自動處理訂單。  

  此範例為您逐步解說此案例，其中 BPELShipping 應用程式會：  

1. 從 Northwind Traders 客戶訂單系統接收訂單。  

2. 將出貨要求傳送到 Wide World Importers 並要求確認。  

3. 從 Wide World Importers 接收出貨要求確認。  

4. 從 Wide World Importers 接收取件通知。  

5. 接收客戶收到貨品之前 (時) 的出貨狀態訊息。  

6. 從 Wide World Importers 接收發票。  

7. 使用發票通知回應 Wide World Importers。  

8. 從 Wide World Importers 接收付款確認。  

9. 將最後出貨確認傳送到訂單系統。  

   此範例使用個別的 BizTalk 應用程式 (ShipperProcess) 來模擬 Wide World Importers。 BPELShipping 應用程式使用 FILE 傳輸 (此傳輸使用常用檔案系統位置進行通訊) 與 ShipperProcess 通訊。  

## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 供 Web 服務使用的 BPEL 是一種 XML 語言，可描述商務程序，以便讓想要使用 Web 服務進行業務往來的不同公司可以輕鬆共用此商務程序。 BPEL 描述如何在商務通訊協定層級處理商務程序，但未描述公司的內部程序，例如公司從合作對象收到訂單之後要如何處理訂單的步驟。 此範例依其設計可說明如何匯入 BPEL 和對應的 WSDL 檔案，並將它們轉換為協調流程，然後開始執行與合作對象之間的商務程序。  

 以下是逐步程序，顯示如何匯入 BPEL 和 WSDL 檔案，以及如何將它們轉換為協調流程，以和預先建置的 BizTalk 應用程式 (ShipperProcess) 進行互動。 如果您完成下列步驟，就不需要執行＜建置和初始化 BPELShipping 應用程式＞中的步驟。  

#### <a name="to-import-from-bpel-and-build-a-working-solution"></a>從 BPEL 匯入並建置有效的方案  

1. 在 Microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，按一下 **新增**，然後按一下**專案**。  

   > [!NOTE]
   >  完成此程序之前，您必須先設定 ShipperProcess 應用程式，以建立支援的程序和結構描述專案。  

2. 在 **新的專案**對話方塊中，專案類型窗格中，選取**BizTalk （專案）**。 在 [範本] 窗格中，選取**BizTalk (Server) BPEL 匯入專案**。  

3. 在 **名稱**方塊中，輸入**BPELShipping**。  

   > [!NOTE]
   >  如果您使用不同的名稱，可能會在進行最後一個繫結步驟時發生問題。  

4. 選取專案的位置，然後按一下**確定**啟動 「 BPEL 匯入精靈 」。  

5. 在 [**歡迎**頁面上，按一下**下一步]**。  

6. 在 **選取 BPEL、 WSDL 與 XSD 檔案**頁面上，按一下**瀏覽**。  

7. 選取的所有檔案\<*範例路徑*\>\Orchestrations\BPELImport\BPELSource 資料夾中，按一下 **開啟**，然後按一下 **下一步**.  

   > [!NOTE]
   >  在此步驟中，您會選取 BPEL 和 WSDL 檔案，描述商務程序和 XSD 檔案來表示商務文件結構描述。  

8. 在 **選取用於叫用 Webservice 的 WSDL 檔案**頁面上，按一下**完成**。  

9. 在「BPEL 匯入精靈」報告成功匯入後，關閉該精靈。 專案現已建立。  

10. 在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄 (**cd**) 至專案位置。  

11. 執行下列命令：  

     **sn – k BPELShipping.snk**  

12. 在 [方案總管] 中，以滑鼠右鍵按一下**BPELShipping**專案，然後再按一下**屬性**。  

13. 底下**Common Properties\Assembly**，選取組件金鑰檔案**BPELShipping.snk**步驟 11 中建立，然後按一下 **確定**。  

14. 在 [方案總管] 中選取所有的 .xsd 檔案，然後將其刪除。  

15. 在 方案總管 中，選取**加入參考**，然後在**專案**索引標籤上，按一下 **瀏覽**。  

16. 選取  **ShippingSchemas.dll**從位置\<*範例路徑*\>\Orchestrations\BPELImport\Solution\ShipperProcess\ShippingSchemas\bin\Development，及然後按一下**確定**。  

    > [!NOTE]
    >  ＜建置和初始化 ShipperProcess 應用程式＞一節中包含如何建置此檔案的指示。  

17. 在 [方案總管] 中，按兩下 **[ordershippingprocess.bpel.odx]**。  

18. 在 **檢視**功能表上，選取**其他的 Windows/協調流程檢視**。  

19. 在 協調流程檢視 視窗中，以滑鼠右鍵按一下**協調流程屬性**，然後按一下**屬性 視窗**。  

20. 在 [屬性] 視窗中，設定**協調流程可匯出**屬性設**False**。  

21. 在 [方案總管] 中，按兩下 **[ordershipping.wsdl.odx]**。  

22. 在 [協調流程檢視] 視窗中，依序展開**型別/多部分訊息類型**。  

23. 依序展開 **[invoiceackmessagetype]** ，然後按一下 **[invoiceackmessagepart]**。  

24. 在 [屬性] 視窗中，依序展開**型別**欄位，然後選取**從參考的組件的結構描述/選取**。  

25. 在 **選取成品類型** 對話方塊中，按一下**ShippingSchemas**，選取**Imported_InvoiceAckMessage**輸入，然後再按一下**確定**.  

    > [!NOTE]
    >  在步驟 23 到 25 中，您會將參與 BPEL 程序的服務訊息類型取代成 ShippingSchemas 中的對應訊息類型。  

26. 使用下列值對每個訊息類型重複步驟 23 到 25。  


    |          訊息部分          |                    訊息類型                     |
    |--------------------------------|-----------------------------------------------------|
    |       InvoiceMessagePart       |       ShippingSchemas.Imported_InvoiceMessage       |
    |      OrderAckMessagePart       |      ShippingSchemas.Imported_OrderAckMessage       |
    |        OrderMessagePart        |        ShippingSchemas.Imported_OrderMessage        |
    | PaymentConfirmationMessagePart | ShippingSchemas.Imported_PaymentConfirmationMessage |
    | PickupNotificationMessagePart  | ShippingSchemas.Imported_PickupNotificationMessage  |
    |  ShipConfirmationMessagePart   |  ShippingSchemas.Imported_ShipConfirmationMessage   |
    |      ShippingHistoryPart       |      ShippingSchemas.Imported_ShippingHistory       |
    |   ShipRequestAckMessagePart    |   ShippingSchemas.Imported_ShipRequestAckMessage    |
    |     ShipRequestMessagePart     |     ShippingSchemas.Imported_ShipRequestMessage     |
    |     ShipStatusMessagePart      |     ShippingSchemas.Imported_ShipStatusMessage      |


27. 在 [方案總管] 中，以滑鼠右鍵按一下**BPELShipping**專案，指向**新增**，然後按一下**現有項目**。  

28. 選取所有的.btm 檔案從位置\<*範例路徑*\>\Orchestrations\BPELImport\Solution\BPELShipping\BPELShipping。  

29. 在 [協調流程檢視] 視窗中，找出**訊息指派**圖形為的 MessageAssignment_1 在 ConstructMessage1 中，並將它刪除。  

30. 從 [工具箱] 拖曳**轉換**圖形到 ConstructMessage1 圖形。  

31. 在 [屬性] 視窗中，按一下 [省略符號按鈕 (**...**)，然後開啟**轉換組態**] 對話方塊。  

32. 選取 **現有的對應**。  

33. 選取 完整格式的對應名稱為**BPELShipping.Order2ShipRequest**。  

34. 選取做為來源**順序。OrderMessagePart**。  

35. 選取做為目的地**ship_request。ShipRequestMessagePart** ，按一下  **確定**。  

36. 針對每個重複步驟 29 到 35**訊息指派**圖形，並將其取代為**轉換**根據下表的圖形。  


    |  要取代的圖形   |              要使用的對應              |      來源文件       |       目的文件        |
    |---------------------|--------------------------------------|----------------------------|-----------------------------------|
    | MessageAssignment_2 |     BPELShipping.Order2OrderAck      |   order.OrderMessagePart   |   order_ack.OrderAckMessagePart   |
    | MessageAssignment_3 |     BPELShipping.Order2OrderNAck     |   order.OrderMessagePart   |   order_ack.OrderAckMessagePart   |
    | MessageAssignment_4 |    BPELShipping.Order2ShipHistory    |   order.OrderMessagePart   | ship_history.ShippingHistoryPart  |
    | MessageAssignment_5 |  BPELShipping.ShipHistory2Completed  |   order.OrderMessagePart   | ship_history.ShippingHistoryPart  |
    | MessageAssignment_6 |       BPELShipping.Invoice2Ack       | invoice.InvoiceMessagePart | invoice_ack.InvoiceAckMessagePart |
    | MessageAssignment_7 | BPELShipping.Order2FinalConfirmation |   order.OrderMessagePart   | order_shipped.OrderAckMessagePart |


37. 儲存此協調流程。  

38. 按兩下**Rule_1**中**決定**圖形**Decision_1**。  

39. 在 [BizTalk 運算式編輯器] 中，將  

     ship_request_ack(BPELShipping.Ship_Acknowledged) == true  

     取代為  

     ship_request_ack(ShippingSchemas.Ship_Acknowledged) == true  

40. 按兩下**迴圈**設為圖案**Loop_1**。  

41. 在 [BizTalk 運算式編輯器] 中，將  

     ship_history(BPELShipping.Ship_Completed) == true  

     取代為  

     ship_history(ShippingSchemas.Ship_Completed) == true  

42. 按兩下**Rule_2**中**決定**圖形**rule_2**。  

43. 在 [BizTalk 運算式編輯器] 中，將  

     ship_status(BPELShipping.ShipStatus) == "DONE"  

     取代為  

     ship_status(ShippingSchemas.ShipStatus) == "DONE"  

44. 在 [協調流程] 檢視中，依序展開**類型/相互關聯類型**然後按一下***OrderCorrelationSet_Type\\***。  

45. 在 屬性 視窗中，按一下 省略符號按鈕 (**...**) 上**相互關聯屬性**。  

46. 在屬性窗格上相互關聯中，按一下 **[bpelshipping.orderid]**，然後按一下**移除**。  

47. 在 [可用的屬性] 窗格中，依序展開**出貨結構描述**，選取**訂單識別碼**，然後按一下**新增**。  

48. 按一下 [確定] 。  

49. 儲存所有檔案，然後建置方案。  

50. 部署該方案。  

51. 瀏覽至位置\<*範例路徑*\>\Orchestrations\BPELImport\Solution\BPELShipping，然後按兩下**BindAndStartOnly.bat**繫結並啟動協調流程。  

## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>* \Orchestrations\BPELImport  

 下表顯示此範例中的檔案，並描述其用途。  

|檔案|描述|  
|---------------|-----------------|  
|BPELSource\InvoiceAckMessage.xsd|Invoice acknowledgment schema.|  
|BPELSource\InvoiceMessage.xsd|發票結構描述。|  
|BPELSource\OrderAckMessage.xsd|Order acknowledgment schema.|  
|BPELSource\OrderHeader.xsd|訂單標頭結構描述。|  
|BPELSource\OrderMessage.xsd|訂單訊息結構描述。|  
|BPELSource\OrderShipping.wsdl|BPEL 參考的 WSDL 檔案。|  
|BPELSource\OrderShippingProcess.bpel|BPEL 程序流程。|  
|BPELSource\PaymentConfirmationMessage.xsd|付款確認訊息。|  
|BPELSource\PickupNotificationMessage.xsd|取件通知訊息。|  
|BPELSource\ShipConfirmationMessage.xsd|出貨確認訊息。|  
|BPELSource\ShippingHistory.xsd|出貨歷程記錄文件。|  
|BPELSource\ShipRequestAckMessage.xsd|出貨要求通知。|  
|BPELSource\ShipRequestMessage.xsd|出貨要求訊息。|  
|BPELSource\ShipStatusMessage.xsd|出貨狀態訊息。|  
|Solution\bindings\BPELBindings.xml|指定 BPELShipping 協調流程之連接埠繫結的繫結檔案。|  
|Solution\bindings\ShipperBindings.xml|指定 ShipperProcess 協調流程之連接埠繫結的繫結檔案。|  
|Solution\BPELShipping\BindAndStartOnly.bat|在手動建置和部署 BPELImport 協調流程之後，用來繫結和啟動該協調流程的批次檔案。|  
|Solution\BPELShipping\cleanup.bat|用來移除 BPELShipping 程序的批次檔案。|  
|Solution\BPELShipping\Setup.bat|用來安裝和啟動所安裝之 BPELShipping 範例的批次檔案。|  
|Solution\BPELShipping\BPELShipping.sln|預先建置的 BPELShipping 範例。|  
olution\BPELShipping\BPELShipping\Invoice2Ack.btm|發票到發票通知的對應。|  
|Solution\BPELShipping\BPELShipping\Order2FinalConfirmation.btm|從訂單訊息轉換為最後出貨確認的對應。|  
|Solution\BPELShipping\BPELShipping\Order2OrderAck.btm|從訂單訊息轉換為訂單通知的對應。|  
|Solution\BPELShipping\BPELShipping\Order2OrderNack.btm|從訂單訊息轉換為訂單負值通知的對應。|  
|Solution\BPELShipping\BPELShipping\Order2ShipHistory.btm|從訂單訊息轉換為出貨歷程記錄文件的對應。|  
|Solution\BPELShipping\BPELShipping\Order2ShipRequest.btm|從訂單訊息轉換為訂單出貨要求的對應。|  
|Solution\BPELShipping\BPELShipping\ShipRequest2Completed.btm|設定要完成之出貨歷程記錄的對應。|  
|Solution\ShipperProcess\setup.bat|建置、部署、繫結和啟動 ShipperProcess 協助程式協調流程及其連接埠的批次檔案。|  
|Solution\ShipperProcess\cleanup.bat|停止、取消登錄和解除部署 ShipperProcess 協助程式協調流程及其連接埠的批次檔案。|  

## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 第一個步驟為建置和初始化用來模擬 Wide World Importers 的 ShipperProcess 應用程式。  

#### <a name="to-build-and-initialize-the-shipperprocess-application"></a>建置和初始化 ShipperProcess 應用程式  

1. 開始**Visual Studio 命令提示字元**。  

2. 從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄 (**cd**) 至下列資料夾：  

    *\<範例路徑\>* \Orchestrations\BPELImport\Solution\ShipperProcess  

3. 執行檔案 Setup.bat，這會執行下列動作：  

   -   建置 ShippingSchemas 專案，此專案包含用於 ShipperProcess 和 BPELShipping 程序中的結構描述  

   -   建置 ShipperProcess  

   -   部署 ShippingSchemas 和 ShipperProcess 專案  

   -   建立和繫結 ShipperProcess 使用的傳送和接收埠  

   -   啟動 ShipperProcess 使用的連接埠  

   -   登錄和啟動 ShipperProcess 協調流程  

   在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。 下列一或多個警告可能會顯示；您可忽略這些警告。  

```  
The 'http://contoso.org/samples/Fragments:XXXX' element is not declared. An error occurred at , (35, 16).  
<SAMPLE_LOCATION>\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(701,13): warning X4014: convoy processing will not occur -- check your protocol if you were expecting it  
<SAMPLE_LOCATION>\Samples\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(667,22): convoy found at 'activate receive(Receive_ShipOrder.Operation_1, Request, initialize Correl)'  
<SAMPLE_LOCATION>\Samples\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(701,13): and 'receive(ReceiveInvoiceAck.Operation_1, Invoice_Ack, Correl)'  
```  

> [!NOTE]
>  如果您已完成＜從 BPEL 匯入並建置有效的解決方案＞中所述的步驟，就不需要執行下列步驟。  

#### <a name="to-build-and-initialize-the-bpelshipping-application"></a>建置和初始化 BPELShipping 應用程式  

1. > [!WARNING]
   >  然後再執行這些步驟，您必須完成上述標題為 < 建置和初始化 ShipperProcess 應用程式 」 步驟。  

    從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄 (**cd**) 至下列資料夾：  

    *\<範例路徑\>* \Orchestrations\BPELImport\Solution\BPELShipping  

2. 執行檔案 Setup.bat，這會執行下列動作：  

   -   建置 BPELShipping 專案  

   -   部署 BPELShipping 專案  

   -   建立和繫結 BPELShipping 程序使用的傳送和接收埠  

   -   啟動 BPELShipping 程序使用的連接埠  

   -   登錄和啟動 BPELShipping 協調流程  

## <a name="running-this-sample"></a>執行此範例  

#### <a name="to-run-the-bpel-import-sample"></a>執行 BPEL 匯入範例  

1.  複製**Order.xml**檔案*\<範例路徑\>* \Orchestrations\BPELImport\Solution 資料夾\<*範例路徑\>* \Orchestrations\BPELImport\Solution\Ports\ReceiveOrder 資料夾。  

2.  BPELShipping 協調流程收取為訂單從客戶訂單處理系統，此檔案跑遍出貨程序，並產生一個檔案中的每個\<*範例路徑*\>\Orchestrations\BPELImport\Solution\Ports\SendOrder 資料夾和\<*範例路徑*\>\Orchestrations\BPELImport\Solution\Ports\FinalConfirmation 資料夾。 這些檔案的名稱的格式是\< *MessageID*\>.xml，其中*\<MessageID\>* 產生來唯一識別的 GUID訊息。  

## <a name="uninstalling-this-sample"></a>解除安裝這個範例  

#### <a name="to-uninstall-the-bpel-import-sample"></a>解除安裝 BPEL 匯入範例  

1. 在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄 (**cd**) 來\<*範例路徑*\>\Orchestrations\BPELImport\BPELShipping。  

2. 執行 Cleanup.bat。  

3. 瀏覽至\<*範例路徑*\>\Orchestrations\BPELImport\ShipperProcess。  

4. 執行 Cleanup.bat。  

## <a name="see-also"></a>另請參閱  
 [協調流程 (BizTalk Server Samples 資料夾)](../core/orchestrations-biztalk-server-samples-folder.md)