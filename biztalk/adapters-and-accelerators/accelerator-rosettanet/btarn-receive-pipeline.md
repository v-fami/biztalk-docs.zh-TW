---
title: BTARN 接收管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BTARN, receive pipelines
- RNMimeDecoder component
- ReceiveMessageNonRepudiate component
- RNDAsm component
- receive pipelines, message flow
- RNPartyRes component
- receive pipelines, BTARN
- MessageUpdater component
- messages, message flow
ms.assetid: 811f2a6a-ddd2-49cc-a00b-4c9d0110a0d1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31b841048f79f460ec3c8098d63eec5cf348b6a1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991919"
---
# <a name="btarn-receive-pipeline"></a>BTARN 接收管線
Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]執行 RosettaNet 實作架構 (RNIF) 訊息接收，會使用 RNIFReceive 管線 (RNIFReceive.btp)。 接收管線包含下列元件：  
  
-   ReceiveMessageNonRepudiate  
  
-   RNMimeDecoder (MIME 前置處理器/解碼器)  
  
-   RNDAsm (XML 解譯器)  
  
-   RNPartyRes (「合作對象解析」元件)  
  
-   MessageUpdater  
  
## <a name="receivemessagenonrepudiate"></a>ReceiveMessageNonRepudiate  
 此元件將接收到的訊息儲存於 MessageStorageIn 資料表。 元件會執行 RNIF 標準所需的不可否認性處理作業。  
  
## <a name="rnmimedecoder"></a>RNMimeDecoder  
 此元件是以在原生 BizTalk Server MIME 前置處理器/解碼器為基礎。 RNMimeDecoder 為 RNIF 處理作業新增下列功能：  
  
- 對於 RNIF 2.01，解密服務內容和附件 (如果有的話)。  
  
- 對於 RNIF 1.1，在承載結束時處理 8 位元組標頭及卸離的簽章標頭。  
  
  如需有關原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]前置處理器/解碼器，請參閱 「 MIME/SMIME 解碼器管線元件 」 在 BizTalk Server 說明中。  
  
## <a name="rndasm"></a>RNDAsm  
 此元件是以原生的 BizTalk Server XML 解譯器為基礎。 RNDAsm 為 RNIF 處理作業新增下列功能：  
  
- 如果內送文件含有 DOCTYPE 標頭，此元件會經由該標頭產生命名空間，並將內送文件中的所有節點移到該命名空間。  
  
- 執行訊息關聯以判斷內送訊息是否重複，若訊息重複，則會產生錯誤訊息。  
  
- 將附件另存為訊息的額外部分。  
  
- 升級訊息屬性。  
  
  如需有關原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解譯器，請參閱 「 XML 解譯器管線元件 」 在 BizTalk Server 說明中。  
  
## <a name="rnpartyres"></a>RNPartyRes  
 此元件是以原生的 BizTalk Server 合作對象解析元件為基礎。 RNPartyRes 為 RNIF 處理作業新增下列功能：  
  
- 如果內送訊息簽署為 BizTalk 合作對象，則對應至傳送者憑證。 如果內送訊息未經簽署，且交易夥伴協議允許這種情形，此元件會從 RNIF 2.01 的傳遞標頭或 RNIF 1.1 的服務標頭擷取傳送者合作對象。  
  
- 驗證傳送者是否存在，以及傳送者與主要組織是否有交易夥伴協議。  
  
  如需有關原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]合作對象解析元件，請參閱 「 合作對象解析管線元件 」 在 BizTalk Server 說明中。  
  
## <a name="messageupdater"></a>MessageUpdater  
 此元件為 RNIF 處理作業新增下列功能：  
  
-   使用 ReceiveMessageNonRepudiate 元件所儲存傳輸訊息的 PIP 代碼、PIP 版本、來源合作對象、目的合作對象及訊息追蹤識別碼，更新 MessageStorageIn 資料表。  
  
-   如果 PIP 不需要不可否認性，則標示要刪除的記錄，設定 `ToBePurged = True`。  
  
## <a name="message-flow"></a>訊息流程  
 透過 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 接收管線的訊息流程如下：  
  
1. HTTP 配接器透過 HTTP POST 接收 RNIF 1.1 物件或 RNIF 2.01 商務訊息。  
  
2. 如果配接器成功接收訊息，就會擷取 RosettaNet 物件或商務訊息，然後傳送到接收管線。  
  
3. 如果物件或商務訊息已簽署，MIME 前置處理器/解碼器會移除簽章。  
  
4. 如果簽章有效，解譯器會讀取前序。  
  
5. 如果訊息是動作訊息，而且需要不可否認性 (**來源與內容的不可否認**程序組態設定中設定`True`)，解碼器會計算並保留摘要。  
  
6. 解譯器會驗證前序 (使用全域變數中的訊息 (MSG) 指導方針和前序結構描述)。  
  
7. 對於 RNIF 2.01，解譯器會讀取傳遞標頭，並使用全域變數中的 MSG 指導方針和傳遞標頭結構描述來驗證標頭。  
  
8. 對於 RNIF 2.01，解譯器會從傳遞標頭擷取交易夥伴資訊，並檢查簽章以確認是否屬於交易夥伴。  
  
9. 對於 RNIF 2.01，如果內容已加密，解碼器會解密內容容器。  
  
10. 解譯器會讀取服務標頭，並使用全域變數中的 MSG 指導方針及服務標頭結構描述來驗證標頭。  
  
11. 對於 RNIF 1.1，解譯器會從服務標頭擷取交易夥伴資訊，並檢查簽章以確認是否屬於交易夥伴。  
  
12. 解譯器會檢查交易夥伴是否具有 PIP 的授權。 如果沒有，解譯器將以 HTTP 403 狀態訊息回覆 HTTP POST (如有必要)，然後發佈錯誤。  
  
13. 如果訊息是已簽署的動作訊息並**來源與內容的不可否認**設定為`True`，ReceiveMessageNonRepudiate 元件會保留原始訊息於 MessageStorageIn 資料表。  
  
14. 如果訊息是已簽署的信號訊息並**不可否認性所需**設定為`True`，則 ReceiveMessageNonRepudiate 元件會保留信號訊息於 MessageStorageIn 資料表。  
  
15. 如果訊息基於不可否認性而保留於 MessageStorageIn 資料表，則 MessageUpdater 會使用訊息的程序組態屬性更新 MessageStorageIn 資料表。  
  
16. 如果訊息是先前處理動作訊息的重複動作訊息，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將發佈錯誤。  
  
17. 對於 RNIF 2.01，如果動作訊息已加密，且 HTTP 同步性 (Synchronicity) 與 PIP 同步性的需求相符，解碼器將解密內容。  
  
18. 解譯器會讀取服務內容，並使用 MSG 指導方針及結構描述加以驗證。  
  
19. 對於 RNIF 2.01，解譯器會驗證資訊清單是否有效，以及是否有內容識別碼。  
  
20. 對於 RNIF 2.01，解譯器將讀取任何附件。  
  
21. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會傳送 RosettaNet 標頭、服務內容和附件至公開程序。  
  
## <a name="see-also"></a>另請參閱  
 [BTARN 中的訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)