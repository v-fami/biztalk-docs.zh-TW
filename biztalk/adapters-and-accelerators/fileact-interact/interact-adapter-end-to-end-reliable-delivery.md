---
title: 互動配接器端對端可靠傳遞 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac7c22f2-ee4a-4e9b-af40-da7eb58daf51
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90ca0fc7ae5872598ed9a61cd7541017a6a39667
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222990"
---
# <a name="interact-adapter-end-to-end-reliable-delivery"></a>互動配接器端對端可靠傳遞
將訊息或檔案傳送給收件者中，我們建議您確認已傳遞的訊息或檔案，以及的商務交易包含在這些執行沒有更多的時間比預期。  
  
 當這兩個實體互相通訊可以使用永續性儲存體 （例如，持續性的訊息導向中介軟體和使用它的介面應用程式所提供） 時，所以可以輕鬆地實作可靠的傳遞，如果通訊的方式標準化察覺到的訊息的狀態。  
  
 下圖顯示的 E2EControl 結構的範例。  
  
 ![結束 &#45; 若要 &#45; 結束控制項](../../adapters-and-accelerators/fileact-interact/media/63e39b43-118e-4572-9d75-21770253a1ee.gif "63e39b43-118e-4572-9d75-21770253a1ee")  
  
 下圖所示的範例中的項目是 SwInt:Request 內傳送，並傳遞至接收應用程式 SwInt:RequestHandle 內不變。 行 02 可讓您將指派給要求的唯一識別碼。 以相同的要求每個後續重新傳輸重複這個唯一識別碼。  
  
 建構這個識別項的方法，則會留給實施者，但通常根據系統呼叫，例如 uuidgen()，或者可能是運算 sha-1 上傳送要求的結果 （帶有前置詞的 Sw:MsgId 與然後取代它藉由 base64 編碼的 sha-1 s置於雙引號）。 主要的需求是全域唯一 （使用非常高的機率）。  
  
 Sw:CreationTime 就是建立的原始要求時間。 這是選擇性參數，但可以限制針對此訊息的先前通訊嘗試的最終搜尋。  
  
 項目 Sw:PDIndication 存在於，指出這是第二個或更進一步來傳輸訊息的嘗試。 接收應用程式感知的 E2EControl 然後可以使用 Sw:MsgId 回尋找是否已收到的訊息。 選擇性 Sw:EmissionList 包含先前嘗試的時間。 這次使用 Sw:GetDateTime 函式時，寄件者收到為本地時間 （以國際標準時間） 寄件者。 再次會很有用限制搜尋。  
  
## <a name="see-also"></a>另請參閱  
 [互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [配接器訊息互動的商務交換](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [配接器儲存與轉送互動](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [互動的配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [互動的介面卡狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [互動配接器不可否認性](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)