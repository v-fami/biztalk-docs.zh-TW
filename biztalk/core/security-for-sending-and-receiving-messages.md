---
title: "傳送和接收訊息的安全性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, receiving
- messages, sending
- messages, processing
- security, messages
- security, message processing
- messages, security
ms.assetid: 9bcd01e4-245a-4f4c-b65c-89d7cd3d1b68
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1328eb98cbf94b85cda16eda431da197c6d0126
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-for-sending-and-receiving-messages"></a>傳送與接收訊息的安全性
下圖顯示當 BizTalk Server 接收、處理訊息以及將其傳送至其他應用程式或夥伴時，會發生的狀況。  
  
 ![安全訊息的安全性功能](../core/media/ebiz-plan-secoverview.gif "ebiz_plan_secoverview")  
在訊息的整個存留期間使用安全性功能  
  
1.  配接器的接收位置會接收訊息。 依通訊協定而定，配接器會執行傳送者的通訊協定層級驗證，以識別代表訊息傳送者的 Windows 使用者帳戶。  
  
2.  配接器接著將訊息傳遞給管線；如果配接器中沒有發生訊息層級驗證，便會在此管線中進行這個驗證。  
  
    1.  在「解碼」階段，管線會解密訊息並使用附加於訊息的憑證或本機電腦「其他人」憑證存放區中設定的憑證來驗證簽章的有效性。 管線驗證簽章之後，解碼元件會上至信任根憑證授權單位 (CA)，對憑證鏈結進行驗證。 如果您設定管線以解碼 S/MIME 訊息，而且傳送者已經使用 S/MIME 來加密訊息，則 MIME/SMIME 解碼器會驗證訊息的簽章，並使用憑證來識別傳送者。 如需如何使用 MIME/SMIME 解碼器管線元件的詳細資訊，請參閱[實作訊息安全性](../core/implementing-message-security.md)。  
  
    2.  在「合作對象解析」階段，BizTalk Server 會使用憑證資訊和從通訊協定層級驗證取得的「傳送者安全性識別碼」(SSID)，來判斷訊息傳送者是否為系統中辨識的合作對象。 傳送者 SSID 是由配接器所驗證的使用者的完整格式名稱。 例如， 如果 BizTalk Server 使用 Windows 驗證以透過 HTTP 配接器接收訊息，則傳送者 SSID 即是「網域\使用者名稱」。 BizTalk Server 會指派合作對象識別碼 (PID) 給訊息，該識別碼會是已辨識之合作對象的合作對象識別碼或訪客識別碼。 如需如何使用合作對象解析元件的詳細資訊，請參閱[使用憑證進行合作對象解析](../core/using-certificates-for-party-resolution.md)。  
  
    3.  如果您已設定接收埠要求傳送者必須經過驗證、確實為系統中已知的合作對象，而 BizTalk Server 卻無法找到訊息傳送者的 PID，則 BizTalk Server 會依接收埠的組態而定，卸除或擱置訊息。 BizTalk Server 提供這項功能來減輕「拒絕服務」攻擊的威脅。 如需接收埠的驗證選項的詳細資訊，請參閱[如何設定接收埠的驗證選項](../core/how-to-configure-authentication-options-for-a-receive-port.md)。  
  
3.  管線驗證訊息之後，會傳送訊息至 MessageBox 資料庫。  
  
    1.  如果加入佇列的主控件 (管線執行所在的主控件) 無法識別為驗證信任的主控件，則 MessageBox 資料庫會以 Guest 識別碼覆寫 PID，而以加入佇列的主控件執行個體執行時所用的服務帳戶來覆寫 SSID。 如需驗證信任的主控件的詳細資訊，請參閱[驗證的訊息之間的處理序](../core/authentication-of-messages-between-processes.md)。 如需如何設定驗證信任的主控件的詳細資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。  
  
    2.  如果管線執行所在的主控件標示為信任的驗證，則 MessageBox 資料庫將信任 PID 和 SSID，並在訊息的內容中留下這個資訊，如此下游程序就可以使用這個資訊來對訊息的原始傳送者進行驗證和/或授權。  
  
    3.  如果 BizTalk Server 必須有接收授權，則 MessageBox 資料庫會確認訂閱訊息的主控件是否有權接收訊息。 如需有關接收授權，請參閱[授權訊息接收器](../core/authorizing-the-receiver-of-a-message.md)。  
  
4.  BizTalk Server 處理訊息之後，輸出管線會在編碼階段中對訊息進行加密和/或數位簽署。  
  
## <a name="see-also"></a>另請參閱  
 [實作訊息安全性](../core/implementing-message-security.md)   
 [規劃訊息安全性](../core/planning-message-security.md)