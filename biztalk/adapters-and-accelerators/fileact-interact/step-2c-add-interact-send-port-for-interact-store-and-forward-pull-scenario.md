---
title: '步驟 2c: 互動存放區和轉送 （提取） 案例中加入互動的傳送埠 |Microsoft 文件'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57038f77-85c3-4811-ab3d-df6e2da8fbcf
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb46943b20676dbe98f79db8760043bb51606c56
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964172"
---
# <a name="step-2c-add-an-interact-send-port-for-the-interact-store-and-forward-pull-scenario"></a>步驟 2c: 互動存放區和轉送 （提取） 案例中加入互動的傳送埠
在開始此步驟之前，必須先完成[步驟 2B： 將檔案傳送連接埠，以擷取 Sw:HandleRequest 訊息互動存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md)。  
  
### <a name="to-add-an-interact-send-port"></a>若要加入互動的傳送埠  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。  
  
4.  在**傳送埠屬性**視窗中，傳送埠， **Tutorial_IA_SendRequest_SnF**。  
  
5.  在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**互動**，然後按一下 **設定**。  
  
6.  在**互動傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**密碼**|視 SAG 連線設定的密碼。|  
    |**使用者名稱**|視 SAG 連線設定的使用者名稱。|  
    |**訊息格式**|**InteractMessage**|  
    |**不可否認性指標**|**FALSE**|  
    |**要求類型**|輸入適當\<RequestType\> SWIFT 與您佈建為基礎的字串。|  
    |**ResponseCrypto**|**FALSE**|  
    |**要求者**|輸入適當\<RequestorDN\> SWIFT 與您佈建為基礎的字串。|  
    |**回應者**|輸入適當\<ResponderDN\> SWIFT 與您佈建為基礎的字串。|  
    |**服務名稱**|輸入適當\<服務名稱\>根據 SWIFT 與您佈建。|  
    |**傳遞通知**|從下拉式清單選取**FALSE**。|  
    |**通知佇列**|輸入適當的佇列名稱，根據 SWIFT 與您佈建。|  
  
    > [!NOTE]
    >  如果只裝載為傳輸時，設定 「 內容 」 中的互動 MessageFormat 接收連接埠和互動傳送埠。 將接收和傳送管線設定為 PassThru。  
  
7.  按一下 **[確定]**。  
  
8.  在**傳送埠屬性**視窗中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**傳送處理常式**|從下拉式清單中，選取主機互動。|  
    |**傳送管線**|從下拉式清單選取**XMLTransmit**。|  
    |**接收管線**|從下拉式清單選取**XMLReceive**。|  
  
9. 在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**屬性**|從下拉式清單選取**BTS。ReceivePortName**。|  
    |**運算子**|從下拉式清單選取 **==** 。|  
    |**值**|型別**Tutorial_IA_InputRequest_SnF**。|  
    |**群組依據**|保留預設值。|  
  
10. 按一下 **[確定]**。  
  
## <a name="see-also"></a>請參閱  
 [步驟 2A： 新增檔案接收位置的互動存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md)   
 [步驟 2B：新增 FILE 傳送埠以擷取 InterAct 儲存和轉寄 (Pull) 案例的 Sw:HandleRequest 訊息](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md)