---
title: "BizTalk Server 使用的憑證加密的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, message flow [encrypted messages]
- encrypted messages
- messages, encryption
ms.assetid: 44b06488-4ecd-436d-af3d-b95e285ecb3e
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4eb1e9629b56fa667d68c246645d00416de221a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="certificates-that-biztalk-server-uses-for-encrypted-messages"></a>BizTalk Server 會使用加密訊息的憑證
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 以「安全多用途網際網路郵件延伸」(Secure Multipurpose Internet Mail Extension，S/MIME) 為基礎，支援輸出訊息的公開金鑰加密以及輸入訊息的解密。 BizTalk Server 在輸出訊息加密中使用 S/MIME 第 3 版，而在輸入訊息解密方面使用 S/MIME 第 2 和 3 版。  
  
-   BizTalk Server 支援 RSA 和 Diffie Hellman 加密憑證。  
  
-   BizTalk Server 支援「資料加密標準」(Data Encryption Standard，DES)、3DES 和 RC2 加密演算法。  
  
 下圖顯示 BizTalk Server 接收加密訊息時的訊息流程。  
  
 ![當接收加密的訊息時，訊息流程](../core/media/bpi-sp-msgsec-inboundencryption.gif "BPI_SP_MSGSEC_InboundEncryption")  
  
 BizTalk Server 接收加密訊息時的訊息流程如下：  
  
1.  夥伴傳送訊息給 BizTalk Server。 夥伴使用 BizTalk Server 公開金鑰來加密訊息。  
  
2.  適當的 BizTalk Server 接收處理常式會接收訊息。  
  
3.  在接收管線執行期間，MIME/SMIME 解碼器管線元件會使用 BizTalk Server 私密金鑰來解密訊息。  
  
    > [!NOTE]
    >  IIS 7.0 電腦上成功解密管線，請對 IIS 應用程式集區帳戶和相關聯的接收處理常式的主控件執行個體所使用的帳戶都相同，而且此帳戶的成員\<machineName> \IIS_WPG 群組。 如需有關設定 IIS 處理序識別，如 IIS 7.0，請參閱的[解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)。 這些處理序必須在相同的帳戶下執行，以確保可載入帳戶設定檔，而這樣會載入在管線中執行解密所需的登錄機碼。 基於效能考量，IIS 7.0 時並未載入帳戶設定檔啟動關聯的 w3wp.exe 處理序，因此必須使用相同的帳戶設定 BizTalk 主控件執行個體，以便讓 BizTalk 載入帳戶設定檔和登錄機碼。  
  
4.  進行其他處理。  
  
 下圖顯示 BizTalk Server 傳送加密訊息時的訊息流程。  
  
 ![傳送加密的訊息時，訊息流程](../core/media/bpi-sp-msgsec-outboundencryption.gif "BPI_SP_MSGSEC_OutboundEncryption")  
  
 BizTalk Server 傳送加密訊息給夥伴的訊息流程如下：  
  
1.  適當的 BizTalk Server 傳送處理常式將訊息傳送給夥伴。  
  
2.  在傳送管線執行期間，MIME/SMIME 編碼器管線元件會使用夥伴的公開金鑰來加密訊息。  
  
3.  夥伴從 BizTalk Server 接收訊息。 夥伴使用自己的私密金鑰來解密訊息。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)   
 [BizTalk Server 使用的憑證存放區](../core/certificate-stores-that-biztalk-server-uses.md)   
 [加密和簽章憑證](../core/encryption-and-signing-certificates.md)   
 [傳送和接收加密的訊息](../core/sending-and-receiving-encrypted-messages.md)