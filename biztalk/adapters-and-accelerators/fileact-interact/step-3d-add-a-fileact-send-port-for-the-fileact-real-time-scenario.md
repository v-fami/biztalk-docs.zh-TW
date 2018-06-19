---
title: 步驟 3D： 新增 FILEACT 傳送埠 FileAct 即時案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a22ba41-4f43-4fbb-92f7-a0fd7558d2ce
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f7440a0bad39fbfddb6319f4051a397f08ac09f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966372"
---
# <a name="step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario"></a>步驟 3D: FileAct 即時案例新增 FILEACT 傳送埠
在開始此步驟之前，您必須完成[步驟 3c: FileAct 即時案例中，將檔案傳送埠新增至擷取 Sw:HandleRequest 訊息](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md)。  
  
### <a name="to-add-a-fileact-send-port"></a>若要新增 FILEACT 傳送埠  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。  
  
4.  在**傳送埠屬性**視窗中，傳送埠，Tutorial_FA_SendRequest_RealTime。  
  
5.  在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**FILEACT**，然後按一下 **設定**。  
  
6.  在**FILEACT 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**密碼**|視 SAG 連線設定的密碼。|  
    |**使用者名稱**|視 SAG 連線設定的使用者名稱。|  
    |**配接器模式**|從下拉式清單選取**存放與轉寄**。|  
    |**不可否認性指標**|從下拉式清單選取**FALSE**。|  
    |**要求類型**|設定為適當\<RequestType\> SWIFT 與您佈建為基礎的字串。|  
    |**ResponseCrypto**|從下拉式清單選取**FALSE**。|  
    |**要求者**|設定為適當\<要求者\>SWIFT 與您佈建為基礎的字串。|  
    |**回應者**|設定為適當\<回應\>字串根據 SWIFT 與您佈建。|  
    |**服務名稱**|設定為適當\<服務名稱\>SWIFT 與您佈建為基礎。|  
    |**通知標記**|從下拉式清單選取**FALSE**。|  
    |**事件端點**|從下拉式清單選取**FALSE**。|  
    |**檔案壓縮**|從下拉式清單選取**無**。|  
    |**實體的資料夾名稱**|輸入 C:\SWIFTAdapterTutorial\Fileact\ClientLocation。|  
    |**轉送端點**|輸入適當的端點 SAG 路由集合。 這個值應該符合您設定在 SAG SnL 端點。|  
    |**ServiceProfile**|從下拉式清單選取**交易計數**。|  
    |**傳遞通知**|從下拉式清單選取**FALSE**。|  
    |**通知佇列**|輸入佇列的名稱，根據 SWIFT 與您佈建。|  
  
    > [!NOTE]
    >  如果要傳送訊息的交易計數，服務設定檔中設定模式以 「 交易計數 」 FileAct 傳送埠。  
  
7.  按一下 **[確定]**。  
  
8.  在**傳送埠屬性**視窗中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**傳送處理常式**|從下拉式清單中，選取 Fileact 主機。|  
    |**傳送管線**|從下拉式清單選取**XMLTransmit**。|  
    |**接收管線**|從下拉式清單選取**XMLReceive**。|  
  
9. 在 [傳送埠屬性] 視窗上**篩選**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**屬性**|從下拉式清單選取**BTS。ReceivePortName**。|  
    |**運算子**|從下拉式清單選取 **==** 。|  
    |**值**|型別 Tutorial_FA_InputRequest_RealTime。|  
    |**群組依據**|保留預設值。|  
  
10. 按一下 **[確定]**。  
  
## <a name="see-also"></a>請參閱  
 [步驟 3： 建立傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [步驟 3A： 新增 FILE 接收位置 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md)   
 [步驟 3B： 新增 FILEACT 接收位置 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md)   
 [步驟 3c： 加入擷取 FileAct 即時案例 Sw:HandleRequest 訊息的 FILE 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md)   
 [步驟 3E：針對 FileAct 即時案例新增 FILE 傳送埠以擷取 Sw:ExchangeFileResponse 訊息](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)