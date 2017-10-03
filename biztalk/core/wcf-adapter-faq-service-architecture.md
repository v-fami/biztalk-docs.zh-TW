---
title: "WCF 配接器 FAQ： 服務架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bad0063-ccff-41f4-b4e0-a02b49403c2d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b73b70474fd30e3a571f59558d6dc439cb981f64
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapter-faq-service-architecture"></a>WCF 配接器 FAQ： 服務架構
## <a name="what-is-the-difference-between-a-wcf-custom-behavior-and-a-biztalk-pipeline-component"></a>WCF 自訂行為與 BizTalk 管線元件之間的差異為何？  
 在初始檢查時，WCF 自訂行為非常類似傳統 BizTalk 管線。 同時利用的中斷訊息至其目的地的資料流程，請執行一些自訂的訊息處理中，訊息攔截的基本概念，並將它轉寄至其目的地。 可以進行此攔截 （繫結至接收位置） 之前或之後 （繫結至傳送埠） 的訊息已由 BizTalk Server 處理。 這個攔截就會發生在兩個方法不只是在內攔截點，但也會從實作不同。 以下是一些差異：  
  
-   管線可供協調流程。 WCF 行為會限制為 WCF 配接器從 BizTalk Server 中所呼叫。  
  
-   管線是 BizTalk Server 專屬的舊式技術。 BizTalk Server，以及在其他純 WCF 案例中，可以使用 WCF 行為。  
  
-   設定管線階段，例如解碼、 驗證等內的即時管線。WCF 行為可插入至訊息流程，在任何其四個攔截進入點 （稍後說明）。  
  
-   管線是單純地在其功能的執行階段。 雖然 WCF 行為以及，他們也能強制執行為關聯式或從 BizTalk Server 管理主控台中的組態期間設定的資料值的條件約束。  
  
-   管線可以操作 BizTalk 訊息，而 WCF 行為對 WCF 訊息。 這表示管線可以一些作業，例如升級 BizTalk 內容屬性，而 WCF 行為可以存取 WCF 訊息屬性。  
  
-   沒有模型的 WCF 配接器或 WCF 中的多部分訊息。 不過，管線元件可以使用 BizTalk 訊息的任何需要的方式操作，因為它可以處理多部分訊息，如有必要。  
  
## <a name="for-the-receive-locations-or-send-ports-using-the-wcf-basichttp-and-wcf-wshttp-adapters-what-type-of-encoding-should-i-select"></a>使用 Wcf-basichttp 和 Wcf-wshttp 配接器的傳送埠或接收位置，何種編碼方式應該選取？  
 每張介面卡沒有 HTTP 為基礎之訊息和文字編碼。 訊息編碼指定的訊息，也就是文字或 MTOM （訊息傳輸組織機制） 所使用的 SOAP 編碼器。 如果選擇文字，則文字編碼方式必須選取。 這個選項有 unicodeFFF (big endian)、 utf-16 （16 位元編碼） 和 utf-8 （8 位元編碼）。  
  
 MTOM 是二進位資料的建議且最有效率的傳輸機制。 不過它需要服務能夠處理 MTOM 資料，這可讓此選項較可攜式比純文字。 如果用來傳輸標準、 非二進位資料，MTOM 實際上會更沒效率比使用 [文字] 選項。 文字普遍接受及可讓更多的跨平台互通性，但它比較沒有效率的兩個選擇如果傳輸的資料包含非文字內容。 使用 WCF 服務合約時，選取繫結的編碼方式的選項時，這是重要的因素。 了解 WCF 作業將會傳送的資料和程序會影響訊息編碼正確的選擇。