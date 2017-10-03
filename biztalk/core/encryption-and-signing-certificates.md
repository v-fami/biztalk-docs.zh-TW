---
title: "加密和簽章憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, security
- security, certificates
- security, messages
- certificates, encryption
- encryption certificates, messages
- messages, encryption
- messages, certificates
- security, encryption
ms.assetid: 3c3f9de5-4156-4133-8d5e-c30b142b6d61
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 633484a6c5599b9323bfd7798f621b27a501ce6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="encryption-and-signing-certificates"></a>加密和簽章憑證
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 非常依賴憑證提供的安全性。 將憑證用於加密和數位簽章，BizTalk Server 就可以傳送並接收可信任的資料，同時也可以協助確保其處理的資料安全無虞。 在加密和數位簽章這兩方面，都需要用到公開金鑰憑證和私密金鑰憑證。 就加密而言，訊息傳送者會使用接收器的公開金鑰憑證來加密訊息，而訊息接收器 (BizTalk Server) 則使用自己的私密金鑰來解密訊息。 就數位簽章而言，訊息傳送者會使用私密金鑰憑證來簽署訊息，而訊息接收器 (BizTalk Server) 則使用傳送者的公開金鑰憑證來驗證簽章。  
  
 BizTalk Server 使用公開金鑰憑證來驗證輸入訊息的數位簽章並加密輸出訊息。 BizTalk Server 使用私密金鑰憑證以解密輸入訊息並簽署輸出訊息。  
  
 在 BizTalk 總管 和 BizTalk 管理主控台中，您可以設定 BizTalk Server 使用的憑證。  
  
 如需有關數位簽章的詳細資訊，請參閱 Microsoft TechNet 網站，網址[http://go.microsoft.com/fwlink/?LinkId=60508](http://go.microsoft.com/fwlink/?LinkId=60508)。  
  
> [!NOTE]
>  處理「安全多用途網際網路郵件延伸」(Secure Multipurpose Internet Mail Extension，S/MIME) 訊息時，您可以選擇讓 BizTalk Server 引擎檢查「憑證撤銷清單」(CRL) 來確保憑證沒有過期，並確定下至「根憑證授權單位」(CA) 都受到信任。 這個驗證會在管線處理訊息時，於 MIME/SMIME 解碼器元件中進行。 如需有關如何設定**檢查撤銷清單**屬性，請參閱[如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk Server 使用的憑證存放區](../core/certificate-stores-that-biztalk-server-uses.md)  
  
-   [BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)  
  
-   [BizTalk Server 會使用加密訊息的憑證](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)