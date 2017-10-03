---
title: "BizTalk Server 使用的憑證簽署的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, signed messages
- messages, message flow [digital signatures]
- S/MIME messages
- signed messages
- digital signatures, message flow
- messages, certificates
ms.assetid: 0b521e11-73ef-424f-9e6a-4fb42dc263ff
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cce82b634fffac4af0f75cdff26c7f512a132de9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="certificates-that-biztalk-server-uses-for-signed-messages"></a>BizTalk Server 用於簽章訊息的憑證
BizTalk Server 支援「安全多用途網際網路郵件延伸」(Secure Multipurpose Internet Mail Extensions，S/MIME) 輸入訊息的簽章輸出訊息及簽章驗證。 BizTalk Server 使用 S/MIME 版本 2 和 3 來簽署輸出訊息及驗證輸入訊息的簽章。 同樣的，您可以設定 BizTalk Server 來簽署傳送給夥伴的訊息，然後將其加密。  
  
-   BizTalk Server 支援用於驗證數位簽章的 SHA-1 和 MD5 簽章演算法。 BizTalk Server 使用 SHA-1 簽章演算法來簽署輸出訊息。  
  
-   由 BizTalk Server 所支援用於簽章金鑰的金鑰交換系統是 Rivest-Shamir-Adleman (RSA) 演算法和「數位簽章標準」(Digital Signature Standard，DSS)。 BizTalk Server 不支援簽章金鑰的「先進加密標準」(Advanced Encryption Standard，AES) 交換系統。  
  
-   BizTalk Server 支援的簽章憑證為 x.509 第 3 版。  
  
 下圖顯示當 BizTalk Server 接收數位簽章訊息，並選擇使用簽章將夥伴識別解析為 BizTalk Server 環境中的合作對象時的訊息流程。  
  
 ![傳送已簽署的訊息時，訊息流程](../core/media/6fd1674d-5a21-4272-83ca-608d7b400de7.gif "6fd1674d-5a21-4272-83ca-608d7b400de7")  
  
 BizTalk Server 接收數位簽章訊息的訊息流程如下：  
  
1.  夥伴傳送訊息給 BizTalk Server。 夥伴以其私密金鑰憑證簽署訊息。  
  
2.  適當的 BizTalk Server 接收處理常式會接收訊息。  
  
3.  在接收管線執行期間，MIME/SMIME 解碼器管線元件會使用夥伴的公開金鑰來驗證數位簽章。  
  
4.  如果已設定合作對象解析元件，便會在接收管線合作對象解析元件的執行期間，使用夥伴的公開金鑰憑證來識別 BizTalk Server 系統中的合作對象。  
  
5.  進行其他處理。  
  
 下圖顯示 BizTalk Server 傳送數位簽章訊息的訊息流程。  
  
 ![](../core/media/bts-bpi-sp-msgsec-outboundsigning-r2c.gif "bts_BPI_SP_MSGSEC_OutboundSigning_R2c")  
  
 BizTalk Server 將數位簽章訊息傳送給夥伴的訊息流程如下：  
  
1.  適當的 BizTalk Server 傳送處理常式將訊息傳送給夥伴。  
  
2.  在傳送管線執行期間，MIME/SMIME 編碼器管線元件會使用 BizTalk Server 私密金鑰來簽署訊息。  
  
3.  夥伴從 BizTalk Server 接收訊息。 夥伴使用 BizTalk Server 公開金鑰來驗證數位簽章。  
  
 BizTalk Server 會驗證憑證的憑證授權單位 (CA) 信任鏈及憑證的有效期限，以確認內送簽章訊息的關聯憑證之有效性。 執行 CA 信任鏈的驗證程序時，需要遍歷憑證上的信任鏈結，直到到達根憑證授權單位為止。 這麼做會驗證用來簽章訊息的憑證確實來自同一個合作對象。 此驗證工作會在執行階段針對每一個簽章的訊息執行。  
  
 此外，BizTalk Server 可以確認憑證授權單位未撤銷用來簽章或加密訊息的憑證。 若要這麼做，您必須下載憑證授權單位的憑證撤銷清單 (CRL)，然後使用 Windows 檔案總管進行安裝。 如需如何驗證憑證的詳細資訊，請參閱[如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 會使用加密訊息的憑證](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)   
 [BizTalk Server 使用的憑證存放區](../core/certificate-stores-that-biztalk-server-uses.md)   
 [加密和簽章憑證](../core/encryption-and-signing-certificates.md)   
 [傳送及接收簽署的訊息](../core/sending-and-receiving-signed-messages.md)