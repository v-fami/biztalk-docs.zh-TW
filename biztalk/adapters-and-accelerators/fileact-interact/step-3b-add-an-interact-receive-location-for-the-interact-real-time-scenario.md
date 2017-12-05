---
title: "步驟 3B： 加入互動接收位置互動即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59780635-e1b6-4e74-a89a-73ec26d6c670
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa1a98f97cba9f46b43b92128a6585ad18afb894
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario"></a>步驟 3B： 加入互動接收位置互動即時案例
完成[步驟 3A: FILE 接收位置新增互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)開始此步驟之前。
  
## <a name="add-an-interact-receive-location"></a>加入互動接收位置  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**  
  
4.  在**接收埠屬性**視窗中，接收埠， **Tutorial_IA_HandleRequestOneWay_RealTime**。  
  
5.  在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。  
  
6.  在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**互動**，然後按一下 **設定**。  
  
7.  在**互動傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**密碼**|輸入您用來連接到 SAG 的密碼。 如需詳細資訊，請參閱 SAG 說明。|  
    |**使用者名稱**|輸入您用來連接到 SAG 的使用者名稱。|  
    |**應用程式名稱**|輸入伺服器\<*應用程式的介面名稱*\>如 SAG 方塊路由的集合。|  
    |**密碼編譯模式**|從下拉式清單選取**進階**。|  
    |**LogMessageBody**|從下拉式清單選取**FALSE**。 **注意：**如果設為 TRUE 時，它會保留的訊息本文的 「 追蹤 」 資料庫。 不過，基於安全性理由，訊息本文可以永遠不會在檢視 BAM 入口網站。|  
    |**記錄訊息**|從下拉式清單選取**TRUE**。 這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。|  
    |**訊息格式**|從下拉式清單選取**InterActMessage**。|  
    |**MemberRef**|從下拉式清單選取**ResponseHeader**。|  
    |**不可否認性指標**|從下拉式清單選取**FALSE**。|  
    |**回應者**|輸入適當\< *ResponderDN* \> SWIFT 與您佈建為基礎的字串。|  
    |**ResponseCrypto**|從下拉式清單選取**FALSE**。|  
    |**逾時**|發生連接逾時之前的秒數的類型。|  
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
  
## <a name="see-also"></a>請參閱  
 [步驟 3： 建立傳送和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [步驟 3A： 新增 FILE 接收位置的互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)   
 [步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)   
 [步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)   
 [步驟 3E：針對 InterAct 即時案例新增 INTERACT 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)