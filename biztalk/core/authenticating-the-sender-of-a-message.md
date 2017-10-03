---
title: "驗證訊息的傳送者 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parties, authenticating
- authenticating, authentication required
- messages, authenticating
- security, authenticating
- digital signatures, authenticating
- security, messages
- MessageBox database, authenticating
- authenticating, authentication trust
- messages, message flow
- authenticating, security
- authenticating, party resolution
- authenticating, digital signatures
- authenticating, messages
ms.assetid: 813a2fb9-0346-4129-9cc5-1713f72a491e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86bc83238d9cdfb435bd26264891ff699cbc3b48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="authenticating-the-sender-of-a-message"></a>驗證訊息的寄件者
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用各種不同機制來確認合作對象確實是其所自稱的身分，或處理程序確實是其所自稱的處理程序。 此外，您可以指定程序是否能轉送到本身是訊息原始傳送者的 BizTalk Server，以及 BizTalk Server 是否應將合作對象辨識為夥伴。  
  
 下圖顯示可讓您對訊息傳送者進行驗證與授權的 BizTalk Server 中的安全性功能。  
  
 ![安全訊息的安全性功能](../core/media/ebiz-plan-secoverview.gif "ebiz_plan_secoverview")  
BizTalk Server 用來驗證及授權訊息傳送者的安全性功能。  
  
 可讓您驗證訊息傳送者的功能為：  
  
-   **數位簽章驗證。** 如果訊息具有數位簽章，BizTalk Server 就會將它用來驗證傳送者的識別。 如需如何設定數位簽章驗證的詳細資訊，請參閱[如何設定接收簽署訊息的 BizTalk 伺服器](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md)。  
  
-   **合作對象解析。** 插入 MessageBox 資料庫中的所有訊息 (不論其源自 BizTalk Server 內部或外部) 都帶有透過將數位憑證或 Windows 帳戶對應到 PID 的作法所決定的合作對象識別碼 (PID)。 如需如何設定合作對象解析元件的詳細資訊，請參閱[使用憑證進行合作對象解析](../core/using-certificates-for-party-resolution.md)。  
  
-   **需要驗證。** 如果接收埠無法判定訊息傳送者，BizTalk 主控件則可能將其當做「Guest」訊息接受，或完全不予理會。 這項功能可讓您保護系統不受「拒絕服務」攻擊的威脅，因為「追蹤」資料庫將不會處理或儲存來自未知合作對象的訊息。 如需接收埠的驗證選項的詳細資訊，請參閱[如何設定接收埠的驗證選項](../core/how-to-configure-authentication-options-for-a-receive-port.md)。  
  
-   **驗證信任。** 如果 MessageBox 資料庫從無法識別為驗證信任的主控件收到訊息，MessageBox 資料庫將會以 Guest 識別碼覆寫 PID，而以主控件執行個體執行所用的服務帳戶來覆寫 SSID。 BizTalk Server 可讓識別為驗證信任的主控件指出信任的主控件佇列至 MessageBox 資料庫的訊息傳送者為實體，而不是信任的主控件本身。 「驗證信任」的主要目的是要讓管線可以解析成 PID，然後再將該 PID 一併傳遞到目前耗用的服務以供授權和輸出合作對象解析之用，以及允許將傳送者的 Windows 安全性識別碼 (SSID) 一併傳輸到目前耗用的服務以供協調流程動作授權之用。 如需驗證信任的主控件的詳細資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。 如需如何使用 BizTalk Server 協調流程與合作對象解析的詳細資訊，請參閱[PartyResolution （BizTalk Server 範例）](../core/partyresolution-biztalk-server-sample.md)。  
  
 您可以依是否需要知道訊息傳送者、訊息原始傳送者或收件者或訊息檢視者而定，使用圖中顯示的部分或所有功能。  
  
 如果「讓夥伴確知訊息來自於您，而且其他人無法在傳輸過程中讀取這些訊息」非常重要，您應該考慮使用下列技術，協助確保只有指定的收件者和收件者應用程式才可以接收訊息：  
  
-   在輸出訊息中使用數位簽章，這樣您的夥伴就可以確認您是訊息傳送者。  
  
-   加密輸出訊息，協助確保未經授權的合作對象無法在傳輸過程中檢視訊息。  
  
 如果「判斷是誰將訊息傳送給貴公司，而且其他人無法在傳輸過程中讀取該訊息」非常重要，您應該考慮使用下列技術，協助確保只有指定的收件者和收件者應用程式才可以接收訊息：  
  
-   確定 BizTalk Server 只接受包含數位簽章的訊息，這樣您就知道是誰傳送訊息。  
  
-   確定您已將用來加密由夥伴傳送至 BizTalk Server 之訊息的公開金鑰憑證傳送給夥伴。 藉由使用加密，您可以協助確保未經授權的合作對象無法在傳輸過程中檢視訊息。  
  
-   在接收埠中使用 [需要驗證] 屬性，以確定訊息是來自已知的合作對象。  
  
 經過一個以上的主控件處理訊息之後，您可能就會搞不清楚誰是訊息的原始傳送者。 為了避免在必須知道原始傳送者的識別時 (例如，授與存取權以傳送或接收訊息時) 發生上述情形，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供了可通過許多主控件來傳播原始傳送者識別的安全性機制，以便根據該識別驗證下游主控件的存取權。 在 BizTalk Server 中，這個機制稱為「程序驗證信任」。 如需詳細資訊，請參閱[驗證的訊息之間的處理序](../core/authentication-of-messages-between-processes.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [輸入訊息驗證](../core/inbound-message-authentication.md)  
  
-   [驗證的處理序之間的訊息](../core/authentication-of-messages-between-processes.md)  
  
-   [輸出訊息保護](../core/outbound-message-protection.md)