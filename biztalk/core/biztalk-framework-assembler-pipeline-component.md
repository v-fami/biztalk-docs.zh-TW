---
title: BizTalk Framework 組合器管線元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, BizTalk Framework Assembler
- BizTalk Framework Assembler [pipeline component]
ms.assetid: 116dff8d-b7f8-4564-a7fb-6440682683dc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50b1be8b898bc00e814bbb251682f2e2f474ade1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990247"
---
# <a name="biztalk-framework-assembler-pipeline-component"></a>BizTalk Framework 組合器管線元件
BizTalk Framework 是一種使用 HTTP 或 SMTP 這類透過網路的傳輸通訊協定，以執行只需一次保證傳遞的方法。 此架構從 1998 年開始出現，並被視為以 Web 服務 (尤其是 WSReliable) 為根據之擱置標準開發的先驅。 基本上，資料的保證只需一次傳遞的問題，一直是「訊息佇列」(也稱為 MSMQ) 這類技術的範疇。 不過，這類技術在資料流的兩端通常需要通用軟體，而且不會針對以公用網路為基礎的開放式傳輸通訊協定的使用做任何處理，例如，利用網際網路在企業界限之間流動的資料。  
  
 一如預期，BizTalk Framework 會實作部分先前用於嘗試解決此資料的保證只需一次傳遞問題之相同機制。 其他解決此問題方式的範例如電子資料交換 (EDI)，其中 ANSI X12 控制數目和標準 997 功能通知文件會形成保證資料只被接收一次的基礎，並且在接收端發生任何問題時通知傳送方。  
  
 BizTalk Framework 假設不論交易資料的系統之間差異多大，這些系統都瞭解 BizTalk Framework 通訊協定的需求：  
  
- 使用可預測的信封格式包裝傳輸。  
  
- 以全域唯一識別碼標記每個輸出傳輸。  
  
- 永遠將包含全域唯一識別碼的回條通知傳回傳送方，不論資料為已接收、已通知和已處理。  
  
- 傳送方可利用某些方法重複傳輸，直到接收方的回條送達，或是經過一段時間之後傳輸不再有效。  
  
  BizTalk Framework 組合器管線元件負責先將 BizTalk Framework 信封和內容序列化至訊息後，才進行傳送，且在回條未於規定的時間內抵達時重新傳送。 它也負責接收和處理回條，以及刪除訊息執行個體。 (已傳送的訊息之訊息執行個體複本會保存在 MessageBox 資料庫中，直到 BizTalk 收到來自目的地的確認回條。 在收到確認回條之後，傳訊引擎會刪除該訊息執行個體。)  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 BizTalk Framework 組合器管線元件](../core/how-to-configure-the-biztalk-framework-assembler-pipeline-component.md)   
 [管線元件](../core/pipeline-components.md)