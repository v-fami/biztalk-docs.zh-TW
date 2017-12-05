---
title: "步驟 3B： 新增 FILEACT 接收位置 FileAct 存放與轉寄案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f30bb7d-1efb-4350-8809-be35f5634ea0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9357c172ff538bce73d3618739f3db4f98141814
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-3b-add-a-fileact-receive-location-for-the-fileact-store-and-forward-scenario"></a>步驟 3B： 新增 FILEACT 接收位置 FileAct 存放與轉寄的案例
在開始此步驟之前，必須先完成[步驟 3A： 新增檔案接收位置為 FileAct 存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md)。  
  
### <a name="to-add-an-fileact-receive-location"></a>若要加入 FILEACT 接收位置  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**  
  
4.  在**接收埠屬性**視窗中，接收埠，Tutorial_FA_HandleRequestOneWay_SnF。  
  
5.  在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。  
  
6.  在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**FILEACT**，和然後按一下 **設定**。  
  
7.  在**FILEACT 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**密碼**|輸入您用來連接到 SAG 的密碼。 如需詳細資訊，請參閱 SAG 說明。|  
    |**使用者名稱**|輸入您用來連接到 SAG 的使用者名稱。|  
    |**應用程式名稱**|輸入伺服器\<應用程式的介面名稱\>SAG 的方塊路由的集合。|  
    |**密碼編譯模式**|從下拉式清單選取**進階**。|  
    |**FACrypto 模式**|從下拉式清單選取**進階**。|  
    |**記錄訊息**|從下拉式清單選取**TRUE**。 這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。|  
    |**MemberRef**|從下拉式清單選取**ResponsePayload**。|  
    |**不可否認性指標**|從下拉式清單選取**FALSE**。|  
    |**回應者**|輸入適當\<回應\>SWIFT 與您佈建為基礎的字串。|  
    |**ResponseCrypto**|從下拉式清單選取**FALSE**。|  
    |**通知標記**|從下拉式清單選取**ResponsePayload**。|  
    |**FileCompression**|從下拉式清單中，選取 [無]。|  
    |**PhysicalFolderName**|在伺服器上，輸入資料夾的名稱。 例如，C:\Fileact\ServerLocation。|  
    |**SubscribeFileEvents**|從下拉式清單選取**FALSE**。|  
    |**TransferAnswer**|從下拉式清單選取**接受**。|  
    |**AllFileEvents**|從下拉式清單選取**TRUE**。|  
    |**事件端點**|輸入適當的 SAG 端點。|  
    |**FullFileStatus**|從下拉式清單選取**TRUE**。|  
    |**逾時**|輸入適當應該發生逾時之前的秒數。|  
    |**取得佇列**|輸入佇列的名稱，根據 SWIFT 與您佈建。|  
    |**ForceAcquire**|從下拉式清單選取**TRUE**。|  
    |**排序依據**|從下拉式清單選取**FileAct**。|  
    |**推入工作階段**|從下拉式清單選取**TRUE**。|  
    |**復原模式**|從下拉式清單選取**FALSE**。|  
    |**SNL 端點**|輸入適當的端點 SAG 路由集合。 這個值應該符合您設定在 SAG SnL 端點。|  
  
8.  按一下 **[確定]**。  
  
9. 在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**接收處理常式**|從下拉式清單選取**BizTalkServerIsolatedHost**。|  
    |**接收管線**|從下拉式清單選取**XMLReceive**。|  
  
10. 按一下 **[確定]**。  
  
## <a name="see-also"></a>請參閱  
 [步驟 3： 建立傳送埠和接收埠為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md)   
 [步驟 3A： 新增 FILE 接收位置為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md)   
 [步驟 3c： 加入擷取 FileAct 存放與轉寄案例的 Sw:HandleFileRequest 和 Sw:HandleSnFRequest 訊息的 FILE 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlefilerequest-and-sw-handlesnfrequest.md)   
 [步驟 3D：針對 FileAct 儲存和轉寄案例新增 FILEACT 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md)