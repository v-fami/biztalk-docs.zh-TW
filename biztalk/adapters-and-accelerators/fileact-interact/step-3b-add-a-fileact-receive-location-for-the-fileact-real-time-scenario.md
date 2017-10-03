---
title: "步驟 3B： 新增 FILEACT 接收位置 FileAct 即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e086c86-1525-4cef-b7e5-a66e14bd8d4f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d97c2f58639814bda45a23c115fea0c3708c2579
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario"></a>步驟 3B： 新增 FILEACT 接收位置 FileAct 即時案例
在開始此步驟之前，必須先完成[步驟 3A: FILE 接收位置新增 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md)。  
  
### <a name="to-add-a-fileact-receive-location"></a>若要加入 FILEACT 接收位置  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**  
  
4.  在**接收埠屬性**視窗中，接收埠，Tutorial_FA_HandleRequestOneWay_RealTime。  
  
5.  在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。  
  
6.  在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**FILEACT**，和然後按一下 **設定**。  
  
7.  在**FILEACT 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**密碼**|輸入您用來連接到 SAG 的密碼。 如需詳細資訊，請參閱 SAG 說明。|  
    |**使用者名稱**|輸入您用來連接到 SAG 的使用者名稱。|  
    |**應用程式名稱**|輸入伺服器\<應用程式的介面名稱 > 的 SAG 方塊路由的集合。|  
    |**密碼編譯模式**|從下拉式清單選取**進階**。|  
    |**FACrypto 模式**|從下拉式清單選取**進階**。|  
    |**記錄訊息**|從下拉式清單選取**TRUE**。 這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。|  
    |**MemberRef**|從下拉式清單選取**ResponsePayload**。|  
    |**不可否認性指標**|從下拉式清單選取**FALSE**。|  
    |**回應者**|輸入適當\<回應 > SWIFT 與您佈建為基礎的字串。|  
    |**ResponseCrypto**|從下拉式清單選取**FALSE**。|  
    |**通知標記**|從下拉式清單選取**ResponsePayload**。|  
    |**FileCompression**|從下拉式清單選取**無**。|  
    |**PhysicalFolderName**|在伺服器上，輸入資料夾的名稱。 例如，C:\Fileact\ServerLocation。|  
    |**SubscribeFileEvents**|從下拉式清單選取**FALSE**。|  
    |**TransferAnswer**|從下拉式清單選取**接受**。|  
    |**AllFileEvents**|從下拉式清單選取**TRUE**。|  
    |**事件端點**|輸入適當的端點 SAG 路由集合。 這個值應該符合您設定在 SAG SnL 端點。|  
    |**FullFileStatus**|從下拉式清單選取**TRUE**。|  
    |**逾時**|輸入適當應該發生逾時之前的秒數。|  
    |**取得佇列**|保留預設值，這個屬性。 這個屬性用於儲存和轉送案例。|  
    |**ForceAcquire**|保留預設值，這個屬性。 這個屬性用於儲存和轉送案例。|  
    |**排序依據**|保留預設值，這個屬性。 這個屬性用於儲存和轉送案例。|  
    |**推入工作階段**|保留預設值，這個屬性。 這個屬性用於儲存和轉送案例。|  
    |**復原模式**|保留預設值，這個屬性。 這個屬性用於儲存和轉送案例。|  
    |**SNL 端點**|保留預設值，這個屬性。 這個屬性用於儲存和轉送案例。|  
  
8.  按一下 **[確定]**。  
  
9. 在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**接收處理常式**|從下拉式清單選取**BizTalkServerIsolatedHost**。|  
    |**接收管線**|從下拉式清單選取**XMLReceive**。|  
  
10. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [步驟 3A： 新增 FILE 接收位置 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md)   
 [步驟 3c： 加入擷取 FileAct 即時案例 Sw:HandleRequest 訊息的 FILE 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md)   
 [步驟 3D: FileAct 即時案例新增 FILEACT 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md)   
 [步驟 3E： 加入擷取 FileAct 即時案例 Sw:ExchangeFileResponse 訊息的 FILE 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)