---
title: "建立連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, creating
- receive ports
- creating, send ports
- creating, ports
- Configuration database [BizTalk Server], connecting
- receive ports, creating
- send ports
- send ports, creating
ms.assetid: 4f99f884-5b84-4f9f-8cec-dd5da259ba7f
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdb7ff7d93b754285e9ed0eb627ca24b113bd2a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-ports"></a>建立連接埠
請使用下列程序，為「單一登入」建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送和接收埠。  
  
## <a name="creating-a-send-port"></a>建立傳送埠  
  
#### <a name="to-create-a-send-port"></a>建立傳送埠  
  
1.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊方塊中，執行下列動作：  
  
    1.  輸入傳送埠名稱，例如`SSOSendToPeopleSoft`。  
  
    2.  從**類型**下拉式清單中，選取**PeopleSoft**。  
  
    3.  從**傳送處理常式**下拉式清單中，選取 URI。  
  
    4.  從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。  
  
    5.  從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。  
  
    6.  按一下**設定**以設定傳送埠。  
  
4.  在**PeopleSoft 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    1.  展開**配接器必要屬性**，並輸入**應用程式伺服器路徑**， **JAVA_HOME**，**使用者名**， **密碼**，以及 Jar 檔案，以連接至 Peoplesoft 系統。  
  
         您不需要設定登入資訊。  
  
    2.  在此清單中，選取您建立用來代表 PeopleSoft 系統的 SSO 分支機構應用程式。  
  
    3.  如**使用 SSO**，選取**是**。  
  
    4.  按一下 **[確定]**。  
  
5.  按一下 **[確定]**。  
  
## <a name="creating-a-receive-port"></a>建立接收埠  
  
#### <a name="to-create-a-receive-port"></a>建立接收埠  
  
1.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。  
  
2.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  
  
3.  在**接收埠屬性**視窗，請在**一般**頁面上，執行下列動作：  
  
    1.  在**名稱**欄位中，輸入`ReceiveFromTIBCOEMS`。  
  
    2.  在**驗證**群組方塊中，指定使用驗證時，如何處理的訊息。  
  
    3.  選取**啟用的路由失敗訊息**核取方塊。  
  
4.  在**接收位置**頁面上，執行下列動作：  
  
    1.  按一下 **[新增]**。  
  
    2.  在**接收位置**視窗，請在**一般**頁面上，輸入**名稱**接收位置。  
  
    3.  從**類型**下拉式清單中，選取傳輸類型，以及從**接收處理常式**下拉式清單中，選取傳輸位址。  
  
    4.  從**接收管線**下拉式清單中，選取接收管線。  
  
    5.  在**排程**頁面上，選取**開始日期**和**結束日期**限制接收文件。  
  
    6.  選取**啟用服務窗口**核取方塊。  
  
    7.  按一下 **[確定]**。  
  
5.  在**輸入對應**頁面上，選取輸入的對應轉換文件上選取的連接埠。  
  
6.  在**追蹤**頁面上，選取所需的追蹤訊息內文和追蹤訊息屬性。  
  
7.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [使用單一登入](../core/using-single-sign-on2.md)