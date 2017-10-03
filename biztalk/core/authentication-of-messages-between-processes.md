---
title: "驗證的處理序之間的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PID
- security, warnings
- processing, messages
- processing, security
- messages, processing
- security, messages
- MessageBox database, authenticating
- SSID
- authenticating, warnings
ms.assetid: fa746ee3-fc22-4e63-a5cc-8bc0cbeb536b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c54fb463353ed6551dcbf5764fae05e63fdb778
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="authentication-of-messages-between-processes"></a>驗證的處理序之間的訊息
下圖顯示 BizTalk Server 中可讓您在不同 BizTalk 主控件之間驗證訊息的安全性功能。  
  
 ![驗證訊息的安全性功能](../core/media/ebiz-plan-secoverview-auth-process.gif "ebiz_plan_secoverview_auth_process")  
BizTalk Server 用來驗證程序之間訊息的安全性功能。  
  
 在 BizTalk Server 接收訊息、解密和驗證訊息，以及取得有效的合作對象識別碼 (PID) 和憑證以識別訊息傳送者之後，MessageBox 資料庫即可開始驗證訊息所符合的訂閱，然後將這個訊息傳送給其他主控件做進一步的處理。  
  
 訊息從一個程序流動到另一個程序時，通常必須將訊息原始傳送者的識別傳遞至下游程序以供授權、合作對象解析和傳送者的相關商務邏輯運作之用。 不過，如果讓所有主控件流通這項資訊，而沒有使用某種安全性或信任機制，將會大幅增加必須確認所有使用者物件和程式碼 (例如，協調流程、配接器、管線元件、運算質等) 是否可信賴的需求。  
  
 為了提供區別使用者物件和程式碼信任層級的方法，BizTalk Server 提供「驗證信任」做為主控件的屬性。 當 MessageBox 資料庫從尚未設定為驗證信任的主控件接收訊息時，MessageBox 資料庫會以 Guest 識別碼覆寫 PID，而以主控件執行個體執行時所用的服務帳戶來覆寫 SSID。 當主控件標示為信任的驗證時，BizTalk 允許主控件指定任何傳送者 SID (SSID) 以及在排入 MessageBox 資料庫佇列之訊息上的任何合作對象識別碼 (PID)。  
  
 藉由指定哪些主控件可信任而哪些不可信任，您就能定義可否信任使用者物件和程式碼的安全性範圍。 也就是說，部署到設定為驗證信任主控件中的使用者物件和程式碼，必須比部署到尚未設定為驗證信任主控件中的使用者物件和程式碼更可信賴。 如需如何設定驗證信任的主控件的詳細資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。  
  
 MessageBox 資料庫接收訊息時，BizTalk Server 會採取下列步驟以強制對傳送訊息至 MessageBox 資料庫的主控件執行個體使用驗證信任：  
  
1.  MessageBox 資料庫首先檢查 SSID 是否屬於信任主控件的主控件執行個體服務帳戶，以判斷傳送訊息的主控件是否已經設定為信任的驗證。  
  
2.  如果傳送訊息至 MessageBox 資料庫的主控件是信任的驗證，MessageBox 資料庫便會將 SSID 和 PID 如實保留在訊息內容中，除非其為空白。 如果 SSID 為空白，則 MessageBox 資料庫會填入呼叫程序的 SID，也稱為主控件 SID (HSID)。 如果 PID 為空白，則會將 PID 設定為 Guest 識別碼。  
  
3.  如果傳送訊息至 MessageBox 資料庫的主控件尚未設定為信任的驗證，則不論這些欄位是否已有內容填入，都會以 HSID 填入 SSID，並將 PID 設定為 Guest。  
  
> [!IMPORTANT]
>  如果要讓下游程序知道訊息原始傳送者的 SSID 和 PID，您必須將訊息傳遞時會經過的所有主控件都設定為信任的驗證。 此外，像是在收到訊息時，隨後將之用於協調流程以建構輸出訊息的這種情況下，則必須明確地將輸入訊息上收到的 SSID 和 PID 當做屬性加入輸出訊息，才能使這些識別流通。  
  
> [!IMPORTANT]
>  如果您將管線執行所在的主控件設定為信任的驗證，BizTalk Server 便會將管線視為信任的環境。 因此，確認正執行於主控件之 BizTalk 管線所包含的任何驗證信任的自訂元件本身是否也是受信任的，極其重要。  
  
> [!NOTE]
>  對於驗證為信任的主控件以及未驗證為信任的主控件，不可以使用相同的服務帳戶。  
  
## <a name="see-also"></a>另請參閱  
 [輸入訊息驗證](../core/inbound-message-authentication.md)   
 [輸出訊息保護](../core/outbound-message-protection.md)   
 [驗證訊息的寄件者](../core/authenticating-the-sender-of-a-message.md)   
 [授權訊息接收器](../core/authorizing-the-receiver-of-a-message.md)