---
title: "步驟 9： 測試方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df446ccc-add3-4dd3-b674-253dda385541
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89a3722d6d8e1d4b730341dfaf16d60af1686f21
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-9-test-the-solution"></a>步驟 9： 測試方案
本主題中，您可以測試混合式應用程式所傳送的 X12 840 銷售訂單訊息至 HTTP 端點部署 EDI 協議的位置。 範例銷售訂單訊息看起來如下：  
  
```  
ISA*00*          *00*          *ZZ*CONTOSO        *ZZ*NORTHWIND      *991221*1226*U*00401*000000025*0*T*:~  
GS*PO*THEM*US*19991221*1226*1*X*004010~  
ST*840*0002~  
BQT*00*BQT02*20120619*001*20120719~  
PER*1A*John*EM*John@contoso.com~  
N1*001~  
N2*co~  
N3*Contoso*One Contoso Way~  
N4*Redmond*WA*98052*US~  
PO1*PO101*121*01*10*AA*A1*1~  
CTT*475~  
SE*10*0002~  
GE*1*1~  
IEA*1*000000025~  
```  
  
 在此訊息中，反白顯示的區段 (行開頭**PO1**) 包含訂單數量。 此訊息中的訂單數量是*121*。 因此，如果您傳送此訊息，它必須插入**SalesOrder**資料表。 您可以更新為小於 100 的數量，並重新傳送訊息，然後必須傳送至您在 FILE 傳送埠中指定的檔案位置。  
  
 若要將此訊息傳送至 EDI 協議，您可以使用**MessageSender**工具隨附的範例[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]。 您可以下載這些範例從[http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057)。  
  
### <a name="to-send-a-message"></a>傳送訊息  
  
1.  找出**MessageSender**範例封裝中的專案並建置該檔案。  
  
2.  使用產生**MessageSender**命令列可執行檔 （在專案的 \bin\Debug 資料夾） 下將訊息傳送至已部署 EDI 協議。 這項工具接受命令列參數，格式如下：  
  
    ```  
    MessageSender.exe <ServiceBusNamespace> <IssuerName> <IssuerKey> <EDI agreement endpoint> <MessageFilepath> <ContentType>  
    ```  
  
     其中，  
  
    |參數名稱|Description|  
    |--------------------|-----------------|  
    |ServiceBusNamespace|服務匯流排命名空間|  
    |IssuerName|指定的命名空間的簽發者名稱|  
    |IssuerKey|指定的命名空間的簽發者金鑰|  
    |EDI 協議端點|部署 EDI 協議的所在端點。 您可以取得此端點 URL，從 [接收設定] 索引標籤 （並在其中傳輸頁面） 的部署在 EDI 協議[(Azure) 的步驟 2： 建立 EDI 協議](../core/step-2-for-azure-create-an-edi-agreement.md)。|  
    |MessageFilePath|包含範例要求訊息的檔案路徑。|  
    |ContentType|本教學課程，請將此參數設定為**text/plain**。|  
  
     開啟命令提示字元並瀏覽至您建置的方案**MessageSender**專案。 執行下列命令，以傳送具有大於 100 的訂單數量的要求訊息：  
  
    ```  
    MessageSender.exe <service bus namespace> owner <issuer key>https://<namespace>.servicebus.appfabriclabs.com/7576ff3d-a0f3-4a46-a4f6-f5be4a50616a/DemoAgreement<path to the sample message> "text/plain"  
    ```  
  
3.  開啟 SQL Server Management Studio 中，連接到資料庫，其中包含**SalesOrder**資料表，並確認新記錄插入資料表。 中的值會注意到**Qty**資料行; 它必須是*121*。  
  
4.  使用**MessageSender**傳送另一則訊息，但這次設定的數量值已排序訊息中*99*。 您會注意到現在，沒有記錄插入在**SalesOrder**資料表。 相反地，訊息會複製到您指定用於接收訊息的訂單數量小於 100 的檔案位置。 收到的訊息如下所示：  
  
    ```  
    <ns1:SalesOrder xmlns:ns0="http://schemas.microsoft.com/BizTalk/EDI/X12/2006" xmlns:ns1="http://ECommerceSalesOrder.Inbound">  
      <CompanyCode>co</CompanyCode>  
      <PartID>1</PartID>  
      <Quantity>99</Quantity>  
      <AskPrice>10</AskPrice>  
      <RequestShipmentDate>2012-07-19</RequestShipmentDate>  
      <Address>  
        <Line1>Contoso</Line1>  
        <Line2>One Contoso Way</Line2>  
        <City>Redmond</City>  
        <State>WA</State>  
        <Country>US</Country>  
        <Zipcode>98052</Zipcode>  
      </Address>  
      <Contact>  
        <Firstname>John</Firstname>  
        <Lastname>John@contoso.com</Lastname>  
      </Contact>  
      <Comments>Order from Partnerco</Comments>  
      <DateNow>2012-06-19</DateNow>  
    </ns1:SalesOrder>  
  
    ```  
  
     中的值會注意到**數量**項目。 它是*99*。  
  
## <a name="see-also"></a>請參閱  
 [教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)