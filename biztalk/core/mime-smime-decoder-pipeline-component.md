---
title: MIME SMIME 解碼器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, MIME/SMIME Decoder
- MIME/SMIME Decoder [pipeline component]
ms.assetid: ff6c963c-1b5c-4be4-9eef-3ec9a018e7fd
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d85fe099cb876156410ba86c5f204a154dfbac36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263222"
---
# <a name="mime-smime-decoder-pipeline-component"></a>MIME SMIME 解碼器管線元件
MIME/SMIME 解碼器管線元件可為訊息提供 MIME 解碼功能。 此管線元件可放入接收管線的解碼階段，並支援 7 位元、8 位元、二進位、quoted-printable、UUEncode 以及 base64 解碼。 當地語系化資料字元集變更不會影響解碼。  
  
 MIME/SMIME 解碼器元件可以解密和簽章-驗證內送訊息。 從服務執行的目前使用者之個人憑證存放區使用解密憑證。 從本機電腦的通訊錄存放區或訊息本身使用簽章-驗證憑證。  
  
 當訊息解密成功時，MIME/SMIME 解碼器管線元件會與用來將訊息解密為訊息述詞的解密憑證指紋相關聯。 這表示訂閱該訊息的任何服務 (協調流程或傳送埠) 都必須與擁有該金鑰的主控件相關聯。 可以在 [BizTalk 管理] 主控台完成主控件與金鑰之間的關聯，作為主控件的屬性。 如需在 BizTalk 管理主控台中設定主機的詳細資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。  
  
 MIME/SMIME 解碼器管線元件是唯一現成的接收管線元件，可處理多部分訊息，包括多部分 MIME/SMIME 訊息。 管線元件會剖析訊息並建立對等的多部分 BizTalk 訊息。 多部分 BizTalk 訊息中有一個稱為內文部分的唯一部分。 所有其他管線元件 (例如 XML 解譯器管線元件) 只處理 BizTalk 訊息的內文部分。 還有對應到 BizTalk 內文部分的 MessageType，可用以路由訊息至訂閱者。  
  
 下列條件由 MIME/SMIME 解碼器管線元件評估，以識別對應到多部分 MIME 訊息的 BizTalk BodyPart。 條件評估的順序如下：  
  
1.  具有設定為 "body" (區分大小寫) 的內容描述標頭的第一個 MIME/SMIME 部分。  
  
2.  具有設定為 "text/xml" (區分大小寫) 的內容類型標頭的第一個 MIME/SMIME 部分。  
  
3.  具有設定為 "text/" (區分大小寫) 的內容類型標頭的第一個 MIME/SMIME 部分。  
  
4.  第一個 MIME/SMIME 部分。  
  
> [!NOTE]
>  輸出 BizTalk 訊息中的部分順序與 MIME/SMIME 訊息中 MIME/SMIME 的部分順序相同。  
  
> [!NOTE]
>  若協調流程訂閱或取用多部分 BizTalk 訊息，則訊息中的部分數目必須符合啟動協調流程的訊息中的部分數目。  
  
 如需設定 MIME/SMIME 解碼器管線元件的資訊，請參閱[如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)。 如需 BizTalk Server 支援解密、 簽章驗證和憑證的使用方式的詳細資訊，請參閱[傳送和接收訊息的安全性](../core/security-for-sending-and-receiving-messages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管線元件](../core/pipeline-components.md)   
 [MIME SMIME 屬性結構描述和屬性](../core/mime-smime-property-schema-and-properties.md)   
 [MIME （BizTalk Server 範例）](../core/mime-biztalk-server-sample.md)