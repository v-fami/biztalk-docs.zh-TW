---
title: 建立 TIBCO EMS 傳送成品 |Microsoft Docs
description: 建立傳送埠，並設定 BizTalk Server 中使用 TIBCO Enterprise Message Service 配接器的傳輸屬性
ms.custom: ''
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f82609c-1847-4796-a24c-28cb350ec739
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98bc13b59826c7f5e938d4749776adb742f70133
ms.sourcegitcommit: a124b58c1ff73c201d17993c3a5f07f41836b0a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2018
ms.locfileid: "24014181"
---
# <a name="creating--tibco-enterprise-message-service-send-handlers"></a>建立 TIBCO 企業訊息服務傳送處理常式
本節說明如何設定傳送埠以連線至 TIBCO Enterprise Message Service (EMS)，以及如何在協調流程中納入 XML 以在執行階段與 TIBCO EMS 互動。  


## <a name="create-a-send-port"></a>建立傳送埠  
  
1.  在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，展開**應用程式**，然後展開您的應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態請求-回應傳送埠**。  
  
3.  在 **傳送埠屬性**，執行下列動作：  
  
    1.  輸入傳送埠名稱，例如`SendToTIBCOEMS`。  
  
    2.  從**型別**下拉式清單中，選取**TIBCO EMS**。  
  
    3.  從**傳送處理常式**下拉式清單中，選取的 URI。  
  
    4.  從**傳送管線**下拉式清單中，選取**Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。 從**接收管線**下拉式清單中，選取 **[microsoft.biztalk.defaultpiplelines.xmlreceive]**。  

        > [!NOTE]
        > BizTalk Adapter for TIBCO Enterprise Message Service 需要傳送、 和 XMLReceive 選取 XMLTransmit，接收。  
  
    6.  選取 **設定**以設定傳送埠。  
  
4.  在  **TIBCO EMS 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    1.  請輸入**訊息處理**，**伺服器連線定義**，**交易支援**， **Username**，而**密碼**。  
  
         您不需要設定登入資訊。  
  
    2.  在此清單中，選取您建立用來代表 TIBCO EMS 系統的分支機構應用程式。  
  
    3.  針對**使用 SSO**，選取**是**。  
  
    4.  選取 [確定]。  
  
5.  選取 [確定]。 

## <a name="set-send-port-transport-properties"></a>設定傳送埠傳輸屬性
TIBCO Enterprise Message Service 傳輸屬性是在設計階段設定、在執行階段使用。 在 **傳輸屬性**，您將設定的連接和認證參數特定為伺服器系統與您嘗試存取的物件。  
  
 ![](../core/media/tib-tibcoemssendtransportpropertiess.gif "TIB_TIBCOEMSSendTransportPropertiess")  
  
  
1.  在 **傳輸屬性**，展開**系統定義**，然後輸入 TIBCO EMS 伺服器連線的所有必要的資訊。  
  
     您必須設定組態參數，Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 才能連線至 TIBCO EMS。 **這項資料會區分大小寫。**  
  
2.  依序展開**訊息處理**，然後輸入所有必要的資訊。  
  
    |參數|描述|  
    |---------------|-----------------|  
    |`Message Expiration Time`|整數，描述訊息停留在佇列或主題上的時間長短；過了這段時間後，TIBCO EMS 伺服器就會刪除該訊息。<br /><br /> 此意義同於 EMS.Expiration 訊息屬性標頭。 可以用協調流程覆寫。<br /><br /> 預設值為 0 毫秒，意思就是訊息在抵達目的地後永遠不會到期。|  
    |`Message is Persistent`|TIBCO EMS 伺服器會先將訊息寫入磁碟，然後才送出收到訊息的通知。<br /><br /> 這是 TibcoEMS.DeliveryMode 標頭屬性。 它指示伺服器先將送達的訊息保存在佇列中，再通知配接器已收到訊息。<br /><br /> 預設值為 [True]。|  
    |`Message Priority`|從 0 到 9 的數字排名，用以定義訊息的優先順序；此值越大，表示優先順序越高。<br /><br /> 優先順序會影響伺服器將訊息傳遞至取用者的順序 (較高的數值優先)。<br /><br /> JMS 規格定義了從 0 (優先順序最低) 到 9 (優先順序最高) 的 10 個優先順序值等級。 此規格的建議是用戶端可以考慮用 0–4 的優先順序值做為一般優先順序，並用 5–9 的優先順序值做為急件優先順序。<br /><br /> 預設值是**4**。|  
  
3.  依序展開**伺服器連線定義**並輸入所有必要的資訊。  
  
    |參數|描述|  
    |---------------|-----------------|  
    |`Destination`|必要設定。 定義目的地的名稱與類型。 例如： staticqueue [Q1]。<br /><br /> 定義佇列或主題，以下列格式: {static} {dynamic] Queue [queuename] 或 {static} {dynamic] Topic [topicname]。 **注意：** 您可以傳送訊息至目的地不存在。 在此情況下，TIBCO Enterprise Message Service 會建立目的地;這指*動態目的地*。 這是由產生者所建立的目的地，當訊息使用完畢和當產生者中斷連線時即會刪除。 A*靜態目的地*是目的地可以只建立由 TIBCO Enterprise Message Service 系統管理員。 由於 BizTalk Adapter for TIBCO Enterprise Message Service 在伺服器上使用名稱對應機制，因此您無法在開啟目的地連線期間連線至動態連接埠。 當您使用名稱對應功能時，只會顯示靜態連接埠。 連線至動態連接埠時，可以使用靜態目的地；但是，如果該名稱的目的地不存在，則系統會建立一個目的地。 目的地可讓您明確指定，定義連接埠時要使用的目的地類型。 目的地語法不區分大小寫： staticqueue [queue_name]，statictopic [topic_name]，dynamicqueue [queue_name];dynamictopic [topic_name]。|  
    |`Port Number`|TIBCO EMS 伺服器所收聽的連接埠。|  
    |`Server Name`|必要設定。 裝載 TIBCO EMS 伺服器的系統名稱。|  
  
4.  提供使用單一登入 (SSO) 的認證。  
  
     您可以透過兩種方式來存取 TIBCO EMS 系統。 您可以使用認證 (使用者名稱和密碼參數) 或單一登入。  
  
    -   選取  **是**中**使用 SSO**使用單一登入。  
  
    -   從清單中選取一個分支機構應用程式。  
  
         由企業單一登入工具所建立的分支機構應用程式代表如 TIBCO EMS 之類的應用程式。 BizTalk Adapter for TIBCO EMS 會使用應用程式使用者的認證。 這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。  
  
         如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications5.md)。  
  
5.  在 **交易支援**，選取**是**如果此傳送埠支援交易。  
  
     如果您在連接埠上啟用交易支援，所有使用此連接埠的協調流程都必須是交易式的；否則，所有呼叫都會回復 (例如，不會認可呼叫)。 新增至協調流程的範圍物件控制了交易的生命週期。  
  
6.  依序展開**使用者認證**，然後輸入**使用者名稱**並**密碼**來存取 TIBCO EMS 伺服器。  
  
    |參數|描述|  
    |---------------|-----------------|  
    |`Password`|用來與 TIBCO EMS 精靈通訊的使用者密碼。<br /><br /> 如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。|  
    |`User Name`|用來與 TIBCO EMS 精靈通訊的使用者名稱。<br /><br /> 如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。|  
  
7.  按一下 **套用**，然後按一下**確定**。  

   
## <a name="next-steps"></a>後續步驟
[建立接收成品](../core/creating-tibco-enterprise-message-service-receive-handlers.md)  
[TIBCO EMS 訊息內容屬性](../core/message-context-properties-in-biztalk-server.md)