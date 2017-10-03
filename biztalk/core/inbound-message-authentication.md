---
title: "輸入訊息驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, authenticating
- processing, inbound messages
- messages, inbound
- processing, security
- security, messages
- inbound messages
ms.assetid: 34c06283-667d-4498-8544-dea6e87f276f
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49ada514c771f4e6dbf0abad3f23cab54721299d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="inbound-message-authentication"></a>輸入訊息驗證
BizTalk Server 可以驗證訊息的傳送者 (使用憑證資訊或 Windows 整合安全性)，以驗證訊息傳送者的識別。 下圖顯示可在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中用來驗證輸入訊息的安全性功能。  
  
 ![驗證輸入的訊息的安全性功能](../core/media/ebiz-plan-secoverview-auth-inbound.gif "ebiz_plan_secoverview_auth_inbound")  
BizTalk Server 用來驗證輸入訊息的安全性功能。  
  
 當 BizTalk Server 收到加密簽署的訊息時，會採取下列步驟來確定已辨識傳送端合作對象。  
  
1.  當訊息抵達 BizTalk Server 接收位置時，接收處理常式會嘗試從傳送程序中取得傳送者的 Windows 安全性識別碼 (SSID)。 接收位置會向下游傳遞 SSID 以支援簽章訊息通過待命程式驗證的事例。 如果能取得用戶端憑證資訊 (例如由 BizTalk 訊息佇列或 HTTP 配接器取得)，BizTalk Server 接收位置就可以取得該項憑證資訊來一併傳送，以便稍後在接收管線進行合作對象解析。 如果接收處理常式無法取得 SSID，這個欄位將保留空白。  
  
     接收處理常式會傳送訊息至接收管線，這個管線將會解密訊息、驗證數位簽章，並進行合作對象解析 (管線有合作對象解析元件的話)。 如果傳送者在內送訊息上使用簽章憑證，則 MIME/SMIME 解碼器元件會覆寫從配接器取得的任何憑證資訊。  
  
2.  如果傳送者加密了訊息，則 MIME/SMIME 解碼器會從主控件執行個體服務帳戶的個人憑證存放區中擷取解密憑證，然後使用私密金鑰來解密訊息。  
  
     如果傳送者簽署了訊息，則 MIME/SMIME 解碼器會檢查內容雜湊是否有遭修改的跡象以驗證數位簽章，然後從憑證存放區擷取憑證以驗證簽章。 如果簽章者的公開金鑰就在訊息中，則 MIME/SMIME 解碼器不會從憑證存放區擷取憑證，而會使用訊息提供的公開金鑰。  
  
3.  通常，管線內的最終處理步驟是合作對象解析。 使用 [BizTalk 總管] 或 [BizTalk Server 管理] 主控台時，您可以建立合作對象；將合作對象對應到簽章憑證；或建立合作對象別名。 在 [BizTalk 總管] 中定義的所有合作對象都會有唯一的合作對象識別項 (PID)。 BizTalk Server 會取得 PID，再放到訊息內容中。 BizTalk 使用下列其中一個方法來取得 PID：  
  
    1.  如果傳送者簽署了訊息，或接收處理常式能夠取得用戶端憑證，而且您選擇使用憑證解析合作對象的選項，則 BizTalk 會使用對應的簽章或用戶端憑證來尋查 PID。 您必須先將該憑證當做屬性值來設定合作對象，才能開始接收其訊息。 如需如何設定合作對象，請參閱[使用憑證進行合作對象解析](../core/using-certificates-for-party-resolution.md)。  
  
    2.  如果傳送者沒有使用訊息上的簽章憑證，而您選擇使用傳送者的安全性識別碼 (SSID) 解析合作對象的選項，則合作對象解析元件會使用 SSID 來尋查 PID。 您必須先設定合作對象以使用 SSID 做為別名，才能開始接收其訊息。 如需 「 合作對象解析 」 元件的詳細資訊，請參閱[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。  
  
        > [!NOTE]
        >  在定義合作對象的別名時，BizTalk Server 會使用帳戶名稱，而非實際的 Windows SID。  
  
    3.  如果無法解析合作對象，則管線會將 PID 設定為 Guest。  
  
4.  如果將接收埠標示成「需要驗證」，而且 BizTalk Server 取得有效的 PID 並解析成已知的合作對象，則訊息會排入 MessageBox 資料庫的佇列等待處理。 如果 SSID 是空白，或 PID 為 Guest 識別碼，則 BizTalk Server 會捨棄訊息，或將其傳送至擱置的佇列 (視 [需要驗證] 屬性的組態而定)。 您可以使用 [需要驗證] 屬性做為對策，以降低可能從未知合作對象接收大量訊息的負面影響。 如需接收埠的驗證選項的詳細資訊，請參閱[如何設定接收埠的驗證選項](../core/how-to-configure-authentication-options-for-a-receive-port.md)。  
  
## <a name="see-also"></a>另請參閱  
 [驗證的處理序之間的訊息](../core/authentication-of-messages-between-processes.md)   
 [輸出訊息保護](../core/outbound-message-protection.md)   
 [驗證訊息的寄件者](../core/authenticating-the-sender-of-a-message.md)   
 [授權訊息接收器](../core/authorizing-the-receiver-of-a-message.md)   
 [如何設定 BizTalk Server 來接收簽署的訊息](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md)   
 [BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)