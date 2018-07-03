---
title: 授權訊息接收器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, messages
- messages, receive authorization
- receive authorization
- messages, security
ms.assetid: c0cdb3ef-ee8e-40a1-9362-13cd26495951
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 612aa7cfca75e34248a094113258fc3c261ef14e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997231"
---
# <a name="authorizing-the-receiver-of-a-message"></a>授權訊息接收器
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可讓您限制您授權接收訊息的處理程序和合作對象。  
  
 下圖顯示您用來授權訊息接收器的 BizTalk Server 中的安全性功能。  
  
 ![授權訊息接收器的安全性功能](../core/media/ebiz-plan-secoverview-authz.gif "ebiz_plan_secoverview_authz")  
BizTalk Server 用來授權訊息接收器的安全性功能。  
  
 您可以使用下列安全性機制來建立具有接收您所傳送訊息的權限 (授權) 的使用者：  
  
-   **解密。** 請確定傳送訊息至 BizTalk Server 的合作對象持有用來加密其傳送至 BizTalk Server 之訊息的公開金鑰憑證。 BizTalk Server 使用私密金鑰憑證來解密訊息。  
  
-   **接收授權。** 您可以使用這個方法來控制 BizTalk Server 環境內的哪些主控件可以接收指定訊息。  
  
-   **加密。** 在 BizTalk 加密訊息時使用來自指定合作對象的公開金鑰憑證，可以確保只有預定的合作對象才可以讀取訊息。  
  
## <a name="receive-authorization"></a>接收授權  
 接收授權是可用來控制哪些主控件可以接收 (訂閱) 指定訊息的方法。 BizTalk Server 使用的憑證資訊，因為在訊息上的訂用帳戶的屬性，以符合述詞： MessageBox 資料庫只會標示為已主機，該訊息的解密憑證需要授權的訊息。 為了方便說明這個程序，請您考量下列實例：  
  
- **路由傳送未加密的訊息：** 時 BizTalk Server 收到訊息寄件者未加密時，沒有關於 BizTalk 如何路由傳送訊息的解密限制。 不論主控件有無設定接收授權憑證，都可以接收訊息。  
  
- **加密的訊息路由傳送：** 加密的訊息送達時，接收管線必須包含解密訊息的解碼元件。 當 BizTalk Server 在解密訊息後進行路由時，BizTalk 使用可用來解密訊息的憑證指紋做為 MessageBox 資料庫訂閱機制中的識別項，並且只有那些以該項憑證設定的主控件才能接收訊息。  
  
  如果要使用接收授權，則必須在您想要授權其接收訊息之主控件的屬性中提供解密憑證的指紋。 如需接收授權，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [輸入訊息驗證](../core/inbound-message-authentication.md)   
 [處理序之間的訊息驗證](../core/authentication-of-messages-between-processes.md)   
 [輸出訊息保護](../core/outbound-message-protection.md)   
 [驗證訊息的寄件者](../core/authenticating-the-sender-of-a-message.md)   
 [規劃訊息安全性](../core/planning-message-security.md)