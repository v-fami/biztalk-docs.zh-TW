---
title: InterAct 配接器安全性架構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a4924b8c-1fda-4a0c-b9be-8f2ccba38013
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fb4234c72ad1d44fd1ca157ae031a73e2dbbd9a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971847"
---
# <a name="interact-adapter-security-architecture"></a>InterAct 配接器安全性架構
訊息傳輸和接收的安全性是使用 SWIFTNet 連結 (SNL) 及 SWIFTAlliance 閘道 (SAG) 中具有憑證] 和 [密碼編譯功能來實作。 SWIFT 建議服務設計為要套用的 「 端對端 「 簽章的互動 — 也就是登入要求和回應訊息。  
  
 SWIFTNet 連結的安全性模組實作密碼編譯作業。 此模組可讓簽章和使用 PKI 的金鑰加密。 本質和程度加密編譯作業會指定為傳遞至 Api 之要求和回應控制資料結構的一部分。  
  
 SWIFTNet 支援簽署/加密 RequestPayload 或 ResponsePayload。 也可以簽署 RequestHeader 或 ResponseHeader。  
  
## <a name="signingencrypting-requests-and-responses"></a>簽署/加密要求和回應  
 套用 SWIFTNet 互動要求的項目上的密碼編譯作業的規則如下所示：  
  
- RequestControl： 這送往 SWIFTNet 只。 SWIFTNet 提供 RequestDescriptor 回應者 （和某些項目也給要求者）。 因此，用戶端程序可處理密碼編譯作業時，伺服器可以對其執行。  
  
- RequestE2EControl： 這個項目包含的資訊，以確保可靠的端對端傳訊。 可以對其不執行任何密碼編譯作業。  
  
- RequestHeader： 它是使用 SWIFTNet 並傳達給回應者不變。 因此，這可以都只簽署了。  
  
- RequestPayload： 您可以在此執行任何密碼編譯作業。  
  
- 加密的項目： 這些的先前已啟動的密碼編譯作業，此要求相關。 這些可以不執行任何密碼編譯作業。  
  
  將密碼編譯函式套用 SWIFTNet 互動回應所引發的規則如下：  
  
- ResponseControl： 這送往 SWIFTNet 只。 SWIFTNet 提供 ResponseDescriptor 給要求者。 因此，任何的伺服器處理序，至用戶端處理密碼編譯作業，可以對其不執行。  
  
- ResponseE2EControl： 這個項目包含的資訊，以確保可靠的端對端傳訊。 可以對其不執行任何密碼編譯作業。  
  
- ResponseHeader： 可以簽署這個項目 （傳輸變更至要求者）。  
  
- ResponsePayload： 可以進行加密及/或簽署。  
  
- 加密的項目： 這些的先前已啟動的密碼編譯作業，此要求相關。 這些可以不執行任何密碼編譯作業。  
  
## <a name="receiving-requests-with-cryptography"></a>接收要求使用密碼編譯  
 伺服器處理序可能會收到已限於由要求者的密碼編譯作業的要求。 連入要求包含所有相關的資訊，以啟用反向的密碼編譯作業。 CryptoInternal 資訊的是，這類的解密和驗證函式現在會有效地運作。  
  
 需要伺服器處理序啟用的 DN，而解密您必須進行的安全性內容  
  
 反向的密碼編譯作業則會修改要求確認 (解密） 的方式，原始要求可供原封不動地伺服器處理序，因為它原本要傳遞至密碼編譯金鑰的用戶端程序作業。 等候回應，類似的處理會進行。 請務必了解，驗證簽章不會只驗證內容簽署已不變更，但它將會驗證是否簽署者為正版。 這需要 SignDN 使用有效的憑證。 有效的憑證是憑證已撤銷 （查閱在憑證撤銷清單中，保持集中 SWIFTNet 內）。  
  
## <a name="activation"></a>啟用  
 SWIFTNet 連結能驗證和解密在自動模式中的所有連入要求和內送回應。 這表示會自動處理 SWIFTNet 連結 （驗證和解密） 最後一個密碼編譯區塊的所有連入要求 （伺服器端） 或內送回應 （用戶端）。 必要條件如下 （如果要求解密） 解密所需的安全性內容會開啟和，以自動模式 （此設定以自動模式會對 Sw:InitRequest 或 Sw:HandleInitResponse，藉由初始化 SWIFTNet 連結設定為 「 自動 」 CryptoMode 或更好的還是 「 進階 」 的互動。 (我們一律會使用 「 進階 」 互動的介面卡，因為這可讓用戶端或伺服器應用程式復原表單未預期的加密，另一端，或從過期的憑證。  
  
 SWIFTNet 連結運作簽章和加密在一個連出要求 （或一個傳出的回應） 時自動 RequestCrypto (ResponseCrypto) 欄位會初始化為"TRUE"RequestControl (ResponseControl) 的要求 （回應） 中。  
  
 在此情況下 SWIFTNet 連結處理最後一個的加密區塊。 必要條件如下 （如果要求簽章），所需的簽章的安全性內容會開啟，加密的區塊是存在於要求上的簽章和加密需要此項目，表示與所 RequestCrypto (ResponseCrypto)旗標設為"TRUE"RequestControl (ResponseControl) 中。 一律這麼做，不論在初始化用戶端或伺服器使用 CryptoMode。  
  
## <a name="see-also"></a>另請參閱  
 [InterAct 配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [商務交換的 interAct 配接器訊息](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [InterAct 配接器儲存和轉寄](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [InterAct 配接器狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [InterAct 配接器不可否認性](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)