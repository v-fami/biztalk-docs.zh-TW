---
title: ESB JMS 編碼器和解碼器元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e5591c2-d2ca-4168-8026-059fe51dd588
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f39f4ab1b0650a8ad6fa1ff35d62b4807995237
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295678"
---
# <a name="the-esb-jms-encoder-and-decoder-components"></a>ESB JMS 編碼器和解碼器元件
Java 訊息服務 (JMS)，或從 IBM WebSphere MQ; 傳送 SOAP 訊息，牽涉到某些整合解決方案[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含兩個以 managed 程式碼，在這些情況下使用 JMS 管線元件。 元件會讀取或寫入 MQ 訊息標頭使用的值與訊息相關聯的內容屬性的 JMS 部分。 目前，有超過 60 的不同類型的 JMS 與 WebSphere MQ Series 系統; 使用中的標頭ESB JMS 元件僅適用於 MQRFH2 標頭。  
  
## <a name="installation"></a>安裝  
 自動安裝 ESB 核心會 JMS 編碼器和 JMS 解碼器元件安裝在 BizTalk Server 管線元件資料夾中。  
  
## <a name="how-it-works"></a>運作方式  
 JMS 管線元件檢查訊息標頭，並只在訊息上運作**MQMD_Format**標頭設定為**RFH (MQRFH2)**。 不過，即使設定這個屬性，元件會檢查以確認它們符合 IBM RFH2 格式的標頭。 如果標頭不符合這種格式，元件都會產生剖析錯誤，指出**MQMD_Format**參數已設為**RFH (MQRFH2)**，但標頭的結構並不符合RFH2 標準。 如果剖析的輸入的訊息標頭就會失敗，解碼器元件可讓訊息在傳遞，但它會將名為訊息內容屬性**MQRFH2_ParseError**至**True**。  
  
 **MQRFH2**屬性結構描述與 JMS 元件部署在 BizTalk 中不僅會公開所有 MQRFH2 標頭屬性。 在降級的內送訊息標頭之後, 從標頭的資料位於 XML 文件儲存在**MQRFH2_NameValueData**訊息內容屬性。 編碼器會調整的長度**NameValueData**資料夾，以確保它是正確的長度。 若要了解這些標頭，以及影響的使用方式，變更值時，檢閱適當的 IBM 文件。  
  
## <a name="using-the-jms-encoder-and-decoder-components"></a>使用 JMS 編碼器和解碼器元件  
 若要使用 JMS 編碼器和解碼器元件，開發人員將它們加入 BizTalk 應用程式中的管線。 傳送管線，JMS 編碼器元件應該位於 「 編碼 」 階段中。 接收管線，JMS 解碼器元件應該位於 「 解碼 」 階段中。 JMS 元件不會安裝任何其他管線階段中。  
  
 JMS 編碼器元件安裝在編碼階段中，讀取在 JMS 值**MQRFH2**標頭和寫入 （升級） 為訊息內容屬性。 當安裝在 「 解碼 」 階段，JMS 解碼器元件會讀取 （會降級） 的內容屬性值，並將它們插入到 JMS **MQRFH2**標頭。 這表示所有 MQ 標頭值都都可做為管線中訊息內容屬性。  
  
 若要偵測及管理的標頭解析錯誤，開發人員可以加入程式碼，以檢查的值**MQRFH2_ParseError**屬性。 它們可以實作訂閱失敗訊息的復原程序，或指定傳送埠的篩選**MQRFH2_ParseError**屬性將訊息保存於。 使用 JMS 訊息的訂閱者中應該包含篩選條件，指定的值**False**如**MQRFH2_ParseError**屬性，避免接收中的 「 訂閱者 」 訊息無法剖析處理序的標頭。  
  
 開發人員也可以更新的內容屬性值 (例如，變更**MQRFH2_Encoding**屬性值)，且元件會反映出這些變更的 MQ 訊息標頭，以便設定訊息抵達時其最終目的地。 元件會自動忽略無效的值，並且設定 「 安全 」 預設值的遺漏必要的標頭。 例如，如果開發人員有指定的值無效**MQRFH2_Encoding**屬性外, 寄訊息會有**MQRFH2_Encoding**標頭設定為**未知**. 如果開發人員會將值移除內容屬性，但**MQMD_Format**屬性仍設為**RFH**，元件將加入包含預設值，根據 IBM 規格的標頭。  
  
 如需如何使用這些元件的範例，請參閱[安裝和執行 JMS MQRFH2 元件範例](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md)。