---
title: '教學課程 3: AS2 教學課程 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 018829a9-e670-4b87-bac5-7f7b1332d90e
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b629d1390b6471fb85a0b9e6fb6b605bedb043a6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013463"
---
# <a name="tutorial-3-as2-tutorial"></a>教學課程 3: AS2 教學課程
在本教學課程中，您將設定透過 HTTP 傳輸接收和傳送 EDIINT/AS2 編碼訊息的解決方案。  
  
 **教學課程解決方案的運作方式**  
  
 解決方案會執行下列作業：  
  
- 從夥伴 (Fabrikam) 接收 AS2 訊息  
  
- 以非同步方式將 MDN 回應傳回給夥伴  
  
- 處理 AS2 訊息的 EDI 內容  
  
- 透過 AS2 將 997 通知傳回給夥伴 (Fabrikam)  
  
- 將含有 EDI 訊息內容的 XML 檔案路由傳送至主要組織 (Contoso) 的後端應用程式。  
  
  > [!NOTE]
  >  這個解決方案不會使用簽章或加密來協助確保 AS2 訊息的安全性。  
  
  **教學課程元件**  
  
  這個解決方案將使用下列項目：  
  
- BTS Http 接收 ISAPI 篩選器來接收 AS2/EDI 訊息寄件者 **(/Contoso/BTSHTTPReceive.dll**)。  
  
- 若要透過傳回 997 通知和 MDN 模擬夥伴的 ASPX 網頁 (**http://localhost/Fabrikam/Default.aspx**)。  
  
- 您用來部署 864 結構描述和其他結構描述的專案檔案 (**Schemas.btproj**)。  
  
- 單向 HTTP 接收位置來接收 EDI 檔案 (**Receive_AS2**)。 這個接收位置會使用含有 AS2 解碼器和 EDI 解譯器的預設 AS2EdiReceive 管線。  
  
- 動態 HTTP 傳送埠以傳回非同步 MDN (**Send_Async_MDN**)。 這個傳送埠會使用含有 AS2 編碼器的 AS2Send 管線。  
  
- 靜態單向 FILE 傳送埠以將 EDI 內容路由至後端資料夾的 XML 檔案中 (**Send_Payload_EdiXml**)。 這個傳送埠會使用 PassThruTransmit 傳送管線。  
  
- 靜態單向 HTTP 傳送埠以透過 AS2 將 997 通知傳回給夥伴 (**Send_Async_997**)。 這個傳送埠會使用包含 AS2 編碼器 (但不需要 EDI 組合器) 的 AS2Send 管線。  
  
- 您將用來建置應用程式以將 EDI 檔案從 Fabrikam 夥伴傳送至 BizTalk 專案檔 (**Sender.csproj**)。  
  
  **訊息流程**  
  
  已完成解決方案的訊息流程將顯示在下圖中：  
  
  ![AS2 教學課程訊息流程](../core/media/31710c1d-4070-433e-953d-dcbfd0bb07a0.gif "31710c1d-4070-433e-953d-dcbfd0bb07a0")  
  
  教學課程元件會依照下列方式處理訊息：  
  
1. 您使用**sender.exe 應用程式**將原始 EDI/AS2 訊息從夥伴 Fabrikam 傳送到 BizTalk Server 電腦。 Sender.exe 會將 EDI/AS2 訊息傳送至 Contoso 虛擬目錄。  
  
   > [!NOTE]
   >  這份清單中的事件可能不會按照所示的順序發生。  
   >   
   >  測試訊息是 \Program Files\Microsoft BizTalk Server 20xx\SDK\AS2 教學課程中的 X12_00401_864.edi。  
  
2. **Receive_AS2**單向接收位置會從 Fabrikam，挑選該檔案從 Contoso 虛擬目錄使用 BTSHTTPReceive.dll ISAPI 延伸模組來接收 EDI 訊息。 此接收管線會解碼 AS2 訊息、解譯 EDI 交換，然後將訊息 XML 放置在 MessageBox 中。  
  
3. 此接收管線會產生 AS2 訊息的 MDN，而且因為 MDN 設定為非同步，所以此接收管線會將 MDN 放置在 MessageBox 中。  
  
4. 此接收管線會產生 997 通知，以便回應 EDI 交換，然後將 997 放置在 MessageBox 中。  
  
5. **Send_Payload_EdiXml**靜態單向傳送埠會拾取 EDI 內容 MessageBox 的 BTS 進行篩選。MessageType 的內容屬性。  
  
6. 裝載傳送埠將包含後端 Contoso 應用程式，由 EDI 內容的 XML 檔案\\_EDIXMLToContoso 資料夾。 這個傳送埠會使用 PassThruTransmit 傳送管線。  
  
7. **Send_Async_MDN**動態傳送埠取用非同步 MDN 從 MessageBox 中，針對 EdiIntAS.IsAS2AsynchronousMdn 內容屬性進行篩選。  
  
8. MDN 傳送埠傳回 MDN \\_MDNToFabrikam 資料夾。 由於這是動態傳送埠時，它會在訊息的標頭中的回條傳遞選項列中使用的位址 (**http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam**) 來將訊息路由至\\_MDNToFabrikam 資料夾。  
  
9. **Send_Async_997**傳送埠會拾取 997 從 MessageBox 的 BTS 進行篩選。MessageType 的內容屬性。  
  
10. 997 傳送埠會使用 HTTP 傳輸來傳送 997 訊息產生 EdiReceive 接收管線，以\\_997ToFabrikam 資料夾。 傳送埠將訊息傳送至 Fabrikam default.aspx 頁面，使用 URI **http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam**。 Default.aspx 頁面接著會傳送到 997 \\_997ToFabrikam 資料夾。  
  
    若要進行這個教學課程，您應該具備下列項目的相關知識：  
  
-   BizTalk Server 管線和管線元件  
  
-   HTTP 配接器  
  
-   接收埠與位置  
  
-   傳送埠  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1：準備 AS2 教學課程](../core/step-1-prepare-for-the-as2-tutorial.md)  
  
-   [步驟 2：建立和部署範例 X12 結構描述](../core/step-2-create-and-deploy-the-sample-x12-schema.md)  
  
-   [步驟 3：為組織設定合作對象和商務設定檔](../core/step-3-configure-a-party-and-business-profile-for-your-organization2.md)  
  
-   [步驟 4：為交易夥伴設定合作對象和商務設定檔](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner2.md)  
  
-   [步驟 5：設定交易夥伴網頁](../core/step-5-configure-the-trading-partner-web-pages.md)  
  
-   [步驟 6：設定 EDI-AS2 接收位置](../core/step-6-configure-the-edi-as2-receive-location.md)  
  
-   [步驟 7：設定 MDN 傳送埠](../core/step-7-configure-the-mdn-send-port.md)  
  
-   [步驟 8：設定 997 傳送埠](../core/step-8-configure-the-997-send-port.md)  
  
-   [步驟 9：設定 EDI 內容傳送埠](../core/step-9-configure-the-edi-payload-send-port.md)  
  
-   [步驟 10：設定 X12 和 AS2 交易夥伴協議](../core/step-10-configure-the-x12-and-as2-trading-partner-agreement.md)  
  
-   [步驟 11：測試 AS2 解決方案](../core/step-11-test-the-as2-solution.md)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 教學課程](../core/biztalk-server-tutorials.md)