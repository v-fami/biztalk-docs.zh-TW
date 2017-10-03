---
title: "建立傳送埠和接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, receive ports
- adapters [JD Edwards OneWorld adapters], receive ports
- creating, receive ports [JD Edwards OneWorld adapters]
- send ports, creating [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], send ports
- adapters [JD Edwards OneWorld adapters], transport properties
- JD Edwards OneWorld adapters, send ports
- JD Edwards OneWorld adapters, transport properties
- receive ports, creating [JD Edwards OneWorld adapters]
- creating, send ports [JD Edwards OneWorld adapters]
ms.assetid: fb4ca8b1-40d9-4beb-a791-554086f8ca98
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 217a1d79dc4079c8f092985e00a1cd5636788e7b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-send-and-receive-ports"></a>建立傳送埠和接收埠
使用下列程序為 BizTalk Adapter for JD Edwards OneWorld 建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送埠和接收埠。  
  
## <a name="creating-a-port"></a>建立連接埠  
  
#### <a name="to-create-a-send-port"></a>建立傳送埠  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，並展開**應用程式**，然後展開您要建立傳送埠的應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**按一下**新增**，然後按一下 **靜態請求-回應連接埠**。  
  
4.  在**傳送埠屬性**對話方塊方塊中，執行下列動作：  
  
    -   在**名稱**方塊中，輸入傳送埠名稱 (例如， `SSOSendToJDE OneWorld`)。  
  
    -   從**類型**下拉式清單中，選取**JDEdwards**。  
  
    -   從**傳送處理常式**下拉式清單中，選取傳送處理常式位址。  
  
    -   如**傳送管線**，選取**Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。  
  
    -   如**接收管線**，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。  
  
5.  按一下 **[確定]**。  
  
## <a name="creating-a-receive-port"></a>建立接收埠  
  
#### <a name="to-create-a-receive-port"></a>建立接收埠  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，並展開**應用程式**，然後展開您要建立傳送埠的應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**按一下**新增**，然後按一下 **單向接收埠**。  
  
     在**單向接收埠屬性**畫面上，在**名稱**欄位中，輸入`ReceiveFromHttp`，然後按一下 **確定**。  
  
4.  輸入中的下列資訊**單向接收埠屬性**視窗：  
  
    -   在**名稱**欄位中，輸入`ReceiveFromHTTP`。  
  
    -   如**傳輸類型**，選取**HTTP**。  
  
5.  按一下 [位址 (URI)] 中的省略符號 (? 按鈕。  
  
     ![](../core/media/siebeladapter-32-ssodemo-httptransport.gif "SiebelAdapter_32_SSODemo_HTTPTransport")  
  
    1.  將 [虛擬目錄加 ISAPI 延伸模組] 設定為 /mySSODemo/BTSHTTPReceive.dll。  
  
    2.  選取**成功時傳回相互關聯控制代碼**。  
  
    3.  選取**使用單一登入**，然後按一下 **確定**。  
  
6.  在**接收處理常式**下拉式清單中，選取**BizTalkServerIsolatedHost**。  
  
     ![](../core/media/siebeladapter-33-ssodemo-receivelocationproperty.gif "SiebelAdapter_33_SSODemo_ReceiveLocationProperty")  
  
7.  如**接收管線**，選取**microsoft.biztalk.defaultpiplelines.xmlreceive**，然後按一下 **確定**。  
  
## <a name="see-also"></a>另請參閱  
 [建立 JD Edwards OneWorld 傳送處理常式](../core/creating-jd-edwards-oneworld-send-handlers.md)   
 [如何設定 JD Edwards OneWorld 傳輸屬性](../core/how-to-set-jd-edwards-oneworld-transport-properties.md)   
 [使用單一登入](../core/using-single-sign-on3.md)