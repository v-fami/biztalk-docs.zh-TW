---
title: "輸出訊息保護 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing, outbound messages
- outbound messages
- security, messages
- authenticating, warnings
- messages, outbound
ms.assetid: 839d3b44-bb44-454b-817c-67b7c8cd74c9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7adbbae776edee8a4f563e2cd48ee035acc3fd7d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="outbound-message-protection"></a>輸出訊息保護
下圖顯示的 BizTalk Server 安全性功能可以用來協助您保護輸出訊息，以避免未經授權的合作對象讀取這些輸出訊息。  
  
 ![保護輸出訊息的安全性功能](../core/media/ebiz-plan-secoverview-auth-outbound.gif "ebiz_plan_secoverview_auth_outbound")  
BizTalk Server 用來保護輸出訊息的安全性功能。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送訊息時，會採取下列步驟協助確保其本身能夠安全地傳送訊息，而且接收端合作對象也可以判斷訊息傳送者的身分：  
  
1.  如果傳送管線包含設定為用於簽署所有輸出訊息的編碼元件 (如 S/MIME)，便會從管線執行時所用主控件執行個體服務帳戶的個人憑證存放區中擷取 BizTalk 群組的簽章憑證，並且會使用與憑證關聯的私密金鑰來簽署訊息。  
  
2.  如果傳送管線包含設定為用於加密所有輸出訊息的編碼元件 (如 S/MIME)，便會使用加密憑證指紋，從「其他人」憑證存放區擷取公開金鑰憑證，並且使用該憑證來加密訊息。  
  
> [!IMPORTANT]
>  雖然您會在 BizTalk 環境中針對所有傳送管線使用一個簽章憑證，但是仍須確定可以在傳送管線執行時所在的主控件之各個主控件執行個體服務帳戶的憑證存放區中取得這個簽章憑證。  
  
 如需如何傳送簽章的訊息的詳細資訊，請參閱[傳送簽署的訊息設定 BizTalk Server 如何](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [輸入訊息驗證](../core/inbound-message-authentication.md)   
 [驗證的處理序之間的訊息](../core/authentication-of-messages-between-processes.md)   
 [驗證訊息的寄件者](../core/authenticating-the-sender-of-a-message.md)   
 [授權訊息接收器](../core/authorizing-the-receiver-of-a-message.md)   
 [BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)