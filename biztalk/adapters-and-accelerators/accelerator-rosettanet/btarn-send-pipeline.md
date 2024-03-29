---
title: BTARN 傳送管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML Assembler
- send pipelines, message flow
- DOCTYPE headers
- MIME/SMIME Encoder
- send pipelines, BTARN
- BTARN, send pipelines
- XML Preprocessor
- messages, message flow
ms.assetid: 88562132-0ea4-4b5a-9445-b69f6c84e5ea
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0791ab4714e1e8a9de847a60d17d14e38f095ecf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011631"
---
# <a name="btarn-send-pipeline"></a>BTARN 傳送管線
Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFSend 管線 (RNIFSend.btp) 中的傳輸會準備 RosettaNet 實作架構 (RNIF) 訊息。 傳送管線包含下列元件：  
  
-   XML 前置處理器  
  
-   XML 組合器  
  
-   多用途網際網路郵件延伸標準/安全多用途網際網路郵件延伸 (MIME/SMIME) 編碼器  
  
## <a name="xml-preprocessor"></a>XML 前置處理器  
 XML 前置處理器會將訊息中的 DOCTYPE 標頭。 標頭會識別與訊息相關聯的文件類型定義 (DTD) 結構描述。 RNIF 規格要求必須有 DOCTYPE 標頭才能進行 RNIF 傳輸。  
  
## <a name="xml-assembler"></a>XML 組合器  
 「 XML 組合器 」 根據 「 BizTalk Server XML 組合器 」。 它會將訊息內容的屬性傳送到信封和文件中， 並從訊息的 XML 部分和附件組合訊息。 它並不會執行訊息驗證。  
  
 如需有關原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]XML 組合器，請參閱 「 XML 組合器管線元件 」 在 BizTalk Server 說明中。  
  
## <a name="mimesmime-encoder"></a>MIME/SMIME 編碼器  
 MIME/SMIME 編碼器是以 BizTalk Server MIME/SMIME 編碼器為基礎。 根據交易夥伴協議和 BizTalk Server MIME/SMIME 編碼器的設定中的通訊協定設定[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]編碼器會執行下列：  
  
- 新增 8 位元組二進位標頭到訊息，這是 RNIF 1.1 訊息的要求。  
  
- 編碼訊息部分，並計算摘要。  
  
- 加密內容 (服務內容加上附件) 或內容容器 (服務內容加上服務標頭及附件)。 如果您已將**編碼所有的連接埠**上設定**通訊協定**至交易夥伴協議索引標籤`False`，編碼器將加密只裝載。 如果您已將**編碼所有的連接埠**設為  `True`，編碼器將加密內容容器。  
  
  如需有關原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]MIME/SMIME 編碼器，請參閱 「 MIME/SMIME 編碼器管線元件 」 在 BizTalk Server 說明中。  
  
## <a name="message-flow"></a>訊息流程  
 透過 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 傳送管線的訊息流程如下：  
  
1.  如果您已將**編碼所有部分**交易夥伴協議，以設定`True`，MIME/SMIME 編碼器會都編碼所有的訊息部分。 MIME/SMIME 編碼器將會使用協議的 `Encoding` 屬性中設定的編碼方式。  
  
2.  對於 RNIF 2.01，如果訊息是動作訊息且有附件，編碼器將對每個附件執行下列動作：  
  
    1.  如果附件是二進位，編碼器將編碼該附件。  
  
    2.  編碼器將產生附件的內容識別碼。  
  
    3.  編碼器將建立附件的 MIME 部分。  
  
3.  對於 RNIF 2.01，管線會將加密訊息部分，然後建立 RNIF 訊息，視設定而定**需要持續的機密性**（在程序組態設定）：  
  
    1.  如果您已將**需要持續的機密性**要**承載**，編碼器將加密服務內容和附件。 接著，組合器會新增服務標頭、傳遞標頭和前序，以建構最後的 RNIF 訊息。  
  
    2.  如果您已將**需要持續的機密性**要**承載容器**，編碼器將加密服務標頭、 服務內容以及附件。 接著，組合器會新增傳遞標頭和前序，以建構最後的 RNIF 訊息。  
  
    3.  如果您已將**需要持續的機密性**要**無**，組合器會新增服務標頭、 傳遞標頭和前序編碼的服務內容和附件 （不含「 加密 」） 以建構最後的 RNIF 訊息。  
  
4.  對於 RNIF 1.1，組合器將建構未加密的最後 RNIF 訊息。  
  
5.  在以下情況中，編碼器將簽署訊息：  
  
    1.  訊息是信號訊息，而**不可否認性所需**屬性 （在程序組態設定中） 是`True`。  
  
    2.  訊息是動作訊息，而**來源與內容的不可否認**屬性 （在程序組態設定中） 是`True`。  
  
6.  對於 RNIF 2.01，編碼器將計算 MIME 訊息第一個內文部分的摘要，並保留摘要。 它將使用交易夥伴協議 (SHA-1 或 MD5) 中 `Digest` 方法屬性所設定的方法來計算摘要。  
  
## <a name="see-also"></a>另請參閱  
 [BTARN 中的訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)