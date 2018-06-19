---
title: 啟動者私用程序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- line-of-business applications (LOBs)
- messages, private processes
- erros
- LOBs
- messages, message flow
- private processes, initiator
- private processes, message flow
- private processes, errors
ms.assetid: 8444a5c8-445a-4bbd-a793-a16816fcb397
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 569d176a15ba5236d5f44d87406d9bbc0a19fca9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22211022"
---
# <a name="initiator-private-process"></a>啟動者私用程序
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]會使用啟動者私用程序 (PrivateInitiator.odx) 來處理啟動者電腦上的服務內容。 這包括下列項目：  
  
-   建立原始訊息的服務內容，並在送至交易夥伴的電腦途中，將訊息傳送到公開程序  
  
-   處理傳回的信號訊息並傳送到商務營運系統 (LOB) 應用程式  
  
-   如果是雙向動作 PIP，處理回應傳回訊息並傳送到 LOB 應用程式。  
  
 私用程序也會設定中繼資料，並新增任何附件。 私用程序傳送外寄訊息到公開程序，該程序會新增 RosettaNet 實作架構 (RNIF) 標頭並準備訊息進行傳送。 在前往 LOB 應用程式的途中，私用程序會傳送內送訊息到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessagesToLOB 資料表。  
  
 此私用程序自動化使用 3A2 與 3A4 交易夥伴介面程序 (PIP) 的訂購查詢/訂單程序， 它也會處理任何其他 PIP 訊息。 您可以依照自己的特定商務程序自訂私用程序。  
  
## <a name="message-flow"></a>訊息流程  
 透過啟動者私用程序的訊息流程如下：  
  
1.  啟動者私用程序從 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessagesFromLOB 資料表接收原始訊息。 後端 LOB 應用程式傳送訊息到此資料表。  
  
2.  私用程序準備已初始化訊息的服務內容，然後傳送到公開程序。  
  
3.  接著，啟動者私用程序進入等候狀態，接聽傳回信號。  
  
4.  私用程序接收到公開程序的傳回信號時，會建構信號訊息，然後在送至 LOB 應用程式的途中，將信號傳送到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫的 MessagesToLOB 資料表。  
  
5.  私用程序傳送通知到 LOB 應用程式，而 LOB 應用程式會將信號訊息放置在 MessagesToLOB 資料表。  
  
6.  如果 RNIF 是 1.1 版，私用程序會等候接收通知信號訊息。 如果接收到信號，私用程序會建構信號訊息，並在送至 LOB 應用程式的途中，將信號傳送到 MessagesToLOB 資料表。  
  
7.  如果原始訊息是單向動作訊息，私用程序傳回信號訊息到 LOB 應用程式後就完成了。 如果原始訊息是雙向動作訊息，私用程序會接聽回應訊息。  
  
8.  如果私用程序從公開程序接收回應訊息，便會以 LOB 應用程式的格式建構回應訊息。 這包括取得 LOB 訊息範本、序列化 XML 服務內容以及載入 XML 訊息部分到 LOB 訊息。  
  
9. 私用程序會將訊息傳送到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessagesToLOB 資料表。  
  
10. 如果回應訊息含有附件，私用程序會呼叫 AttachmentHelper 工具來處理附件。  
  
11. 私用程序傳送通知到 LOB 應用程式，而 LOB 應用程式會將回應訊息放置在 MessagesToLOB 資料表，這樣程序就完成了。  
  
## <a name="handling-of-incorrect-messages"></a>不正確訊息的處理方式  
 當啟動者私用程序從 LOB 應用程式接收不正確的訊息時，私用程序會將例外狀況訊息傳回至 LOB。 然而，私用程序不會將不正確的訊息發佈到 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] BizTalk 管理主控台。 因此，您無法從 BizTalk 管理主控台檢視不正確的訊息。 您可以使用例外狀況訊息存取不正確的訊息，以判斷何者為不正確的訊息，再從 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA 資料庫的 MessagesFromLOB 資料表存取不正確的訊息。 不過，此訊息可能與私用程序所使用的訊息不同，因為用來處理訊息的預存程序和配接器會編輯訊息。 這兩者會將根項目與命名空間新增至訊息。 預存程序和配接器可能還會傳回多筆記錄。  
  
## <a name="see-also"></a>另請參閱  
 [私用程序](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)   
 [回應者私用程序](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md)   
 [協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [PrivateInitiator 範例](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)