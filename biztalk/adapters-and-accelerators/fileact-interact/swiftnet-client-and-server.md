---
title: SWIFTNet 用戶端和伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 89d9f54f-af16-4f14-bbe4-8306758320d8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ea3a1b974a26f90d03bb65675c1c4e8966720f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224654"
---
# <a name="swiftnet-client-and-server"></a>SWIFTNet 用戶端和伺服器
SWIFT 使用規定用戶端和伺服器來描述傳送和接收。 SWIFT 的用戶端會呼叫 SWIFTNet 連結 (SNL) 透過 SWIFTNet 啟始通訊的程序。 在 BizTalk Server 中，這稱為傳送配接器。 SWIFT 的伺服器是由 SNL 流量流入透過 SWIFTNet 時呼叫的程式。 在 BizTalk Server 中，這稱為接收配接器。  
  
 請勿混淆 SWIFT 的用戶端和商務用戶端與伺服器的伺服器。 例如，用戶端 （組織） 會依賴伺服器 （組織） 所提供的服務。 如果伺服器 （組織） 想要與用戶端 （組織） 進行通訊，則必須使用 SNL 用戶端應用程式，才能執行這項操作，和用戶端 （組織） 必須擁有 SNL 伺服器應用程式接收連入流量。 這會在下圖中說明。  
  
 ![用戶端與伺服器之間的 SWIFTNet 關係](../../adapters-and-accelerators/fileact-interact/media/7ad5d877-19d4-431f-9358-d5ae278cf945.gif "7ad5d877-19d4-431f-9358-d5ae278cf945")  
  
 SNL 假設用戶端和伺服器應用程式是從命令提示字元啟動的可執行檔。 它們都連結至 SNL API DLL，會與實際 SNL 執行個體處理序進行通訊。  
  
## <a name="snl-client-applications"></a>SNL 用戶端應用程式  
 SNL 用戶端應用程式依賴 SwCall API，如下所述。 就技術上來說，一般用戶端應用程式可以描述，如下所示：  
  
```  
Main:  
  Initialize SNL API  
  Repeat  
    Call SwCall API  
  Until shutdown  
```  
  
 SNL 用戶端應用程式必須在中執行專用的處理序，因為 SNL 參考用戶端內容的處理序識別碼。 SNL 同步處理使用 SwCall Tuxedo 資源的呼叫。 如此一來，只有單一用戶端一次可以有效地執行執行緒 SwCall。  
  
 用戶端支援的同步通訊模式。 這表示回應從伺服器傳回時發生 SWCall 報酬率。 這個傳回之後，才可以執行下一步 SwCall。  
  
## <a name="snl-server-applications"></a>SNL 伺服器應用程式  
 SNL 伺服器應用程式是用戶端應用程式比稍微更為複雜。 伺服器應用程式註冊之前執行封鎖 SNL DLL 呼叫的回呼函式。 就技術上來說，一般的伺服器應用程式可以描述，如下所示：  
  
```  
Main:  
  Initialize SNL API  
  Call SwRegisterSwCallback, registering the Callback function  
  Call SwServer, block and receive callbacks  
  
Callback(Request):  
  Process Request  
  Return Response  
```  
  
 伺服器應用程式可以呼叫的回呼函式中 SwCall API。 在某些情況下，它必須呼叫 SwCall 能夠產生想要的結果或回應。 不過，伺服器應用程式可以永遠不會透過網路初始通訊。 伺服器應用程式不可以用戶端應用程式。  
  
 在下圖中，呼叫標示**初始化**是 SNL API 初始化程序，需要多次呼叫的抽象概念。 標示為呼叫**SwCallback()** 重複數次，而且呼叫標示**SwCall()** 是選擇性的。  
  
 ![SNL 伺服器功能](../../adapters-and-accelerators/fileact-interact/media/42395775-cdbc-4e36-8b36-566caefa2aaf.gif "42395775-cdbc-4e36-8b36-566caefa2aaf")  
  
 伺服器和 SNL API DLL 之間的所有呼叫都都標準的 C 呼叫慣例同步函式呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [了解 FileAct 和互動的配接器架構](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md)   
 [SWIFT 傳送配接器架構](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md)   
 [SWIFT 接收配接器架構](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)