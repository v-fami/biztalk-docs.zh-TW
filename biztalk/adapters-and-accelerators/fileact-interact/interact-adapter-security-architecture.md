---
title: "互動的配接器安全性架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4924b8c-1fda-4a0c-b9be-8f2ccba38013
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de0eee57daec102507a9e502e3146e1cfcdec723
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-security-architecture"></a>互動的配接器安全性架構
訊息傳輸和接收的安全性是使用固有 SWIFTNet 連結 (SNL) 和 SWIFTAlliance 閘道 (SAG) 中的憑證和密碼編譯功能來實作。 SWIFT 建議服務設計的互動來 「 端對端 「 簽章套用 — 也就是登入要求和回應訊息。  
  
 SWIFTNet 連結的安全性模組實作密碼編譯作業。 此模組可讓簽章和加密使用 PKI 金鑰。 本質和程度加密編譯作業會指定傳遞至 Api 的要求和回應控制項資料結構的一部分。  
  
 SWIFTNet 支援簽署/加密 RequestPayload 或 ResponsePayload。 也可以簽署 RequestHeader 或 ResponseHeader。  
  
## <a name="signingencrypting-requests-and-responses"></a>簽署/加密要求和回應  
 密碼編譯操作，要求 SWIFTNet 互動項目上的套用的規則如下所示：  
  
-   RequestControl： 這被要以 SWIFTNet 只。 SWIFTNet 會 RequestDescriptor 傳遞至回應者 （和也給要求者的某些項目）。 因此，可以對其不執行至伺服器處理的密碼編譯作業的任何用戶端程序。  
  
-   RequestE2EControl： 這個項目包含的資訊，確保端對端的可信賴傳訊。 可以對其不執行任何密碼編譯作業。  
  
-   RequestHeader： 它是由 SWIFTNet 並傳達給回應者不變。 因此，這可以只是帶正負號。  
  
-   RequestPayload： 您可以在此執行任何密碼編譯作業。  
  
-   加密的項目： 這些與先前已啟動的密碼編譯作業，此要求相關聯。 這些可以不執行任何密碼編譯作業。  
  
 套用密碼編譯的函式 SWIFTNet 互動回應所引發的規則如下：  
  
-   ResponseControl： 這被要以 SWIFTNet 只。 SWIFTNet 將 ResponseDescriptor 傳遞給要求者。 因此，沒有伺服器處理序在用戶端處理密碼編譯作業，可以對其執行。  
  
-   ResponseE2EControl： 這個項目包含的資訊，確保端對端的可信賴傳訊。 可以對其不執行任何密碼編譯作業。  
  
-   ResponseHeader： 可以簽署這個項目 （傳送變更到要求者）。  
  
-   ResponsePayload： 可以進行加密及/或簽署。  
  
-   加密的項目： 這些與先前已啟動的密碼編譯作業，此要求相關聯。 這些可以不執行任何密碼編譯作業。  
  
## <a name="receiving-requests-with-cryptography"></a>接收要求使用密碼編譯  
 伺服器處理序可能會收到已進行要求者的密碼編譯作業的要求。 傳入的要求包含所有的相關資訊，若要啟用反向的密碼編譯作業。 CryptoInternal 資訊會解密和驗證函式現在會有效地運作。  
  
 伺服器處理序將需要啟動的 DN 進行哪些解密需求的安全性內容  
  
 要求將會加以修改反向的密碼編譯作業 （確認、 解密） 的方式，原始要求可供不變，與伺服器處理序，因為它原來隨選密碼編譯金鑰的用戶端程序作業。 回應，類似的處理會發生。 請務必了解，驗證簽章將只驗證功能已簽署已不變更，但它將會驗證是否簽署人為正版。 這需要 SignDN 使用有效的憑證。 有效的憑證是憑證已撤銷 （SWIFTNet 內集中保存在憑證撤銷清單中的查閱）。  
  
## <a name="activation"></a>啟用  
 SWIFTNet 連結可以操作驗證和解密在自動模式中的所有連入要求和內送回應。 這表示會自動處理 SWIFTNet 連結 （驗證和解密） 的所有內送要求 （伺服器端） 或連入回應 （用戶端） 區塊的最後一個密碼編譯。 必要條件是開啟的 （如果要求解密） 解密所需的安全性內容，且 SWIFTNet 連結，已在自動模式中 （此設定以自動模式由 Sw:InitRequest 或 Sw:HandleInitResponse，初始化設定為 「 自動 」 CryptoMode 或更好的仍 「 進階 」 的互動。 (我們將一律使用 [進階] 進行互動的介面卡，這可讓用戶端或伺服器應用程式復原表單未預期的加密，另一端，或從過期的憑證。  
  
 SWIFTNet 連結運作簽章及加密自動上一個連出要求 （或一個外寄回應），如果欄位 RequestCrypto (ResponseCrypto) 會初始化為"TRUE"的要求 （回應） RequestControl (ResponseControl) 中。  
  
 在此情況下 SWIFTNet 連結處理最後一個的加密區塊。 先決條件皆已開啟的簽章 （如果要求簽章） 所需的安全性內容，密碼編譯區塊是存在於具有簽章和加密所需，指示要求，而且 RequestCrypto (ResponseCrypto)旗標設定為"TRUE"RequestControl (ResponseControl) 中。 進行此設定一律，不論在初始化用戶端或伺服器使用 CryptoMode。  
  
## <a name="see-also"></a>另請參閱  
 [互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [配接器訊息互動的商務交換](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [配接器儲存與轉送互動](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [互動的介面卡狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [互動配接器不可否認性](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)