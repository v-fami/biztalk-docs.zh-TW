---
title: 回應者私用程序 |Microsoft 文件
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
- LOBs
- messages, message flow
- private processes, responder
- private processes, message flow
ms.assetid: 69b58320-977c-44d2-a7d6-f986213aecf2
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8ba5ca38eb64859182242c944d260c9db15c880
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210894"
---
# <a name="responder-private-process"></a>回應者私用程序
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]會使用回應者私用程序 (PrivateResponder.odx) 來處理回應者電腦上的服務內容。 這包括下列項目：  
  
-   將內送訊息傳送到商務營運系統 (LOB) 應用程式  
  
-   在前往回應者電腦的途中，建立回應訊息的服務內容並將訊息傳送到公開程序  
  
 私用程序也會設定中繼資料，並新增任何附件到回應訊息。 私用程序會傳送外寄訊息到回應者公開程序，該程序會新增 RosettaNet 實作架構 (RNIF) 標頭並準備訊息進行傳輸。 在前往 LOB 應用程式的途中，私用程序會傳送內送訊息到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessagesToLOB 資料表。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含兩個回應者私用程序範例，您可以根據自己的特定商務程序進行自訂。 第一個是 PrivateResponder 程序範例，其中包含 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 所安裝回應者私用程序的程式碼。 如需詳細資訊，請參閱[PrivateResponder 範例](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)。  
  
 第二個範例是 PIP3A4PrivateResponder 私用程序，此範例會自動化使用 3A2 與 3A4 交易夥伴介面程序 (PIP) 的訂購查詢/訂單程序。 它也會處理任何其他 PIP 訊息。 如需詳細資訊，請參閱[3A4 私用回應者協調流程使用商務規則](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)。  
  
## <a name="message-flow"></a>訊息流程  
 透過回應者私用程序的訊息流程如下：  
  
1.  在前往啟動者電腦的途中，回應者私用程序從回應者公開程序接收原始內送訊息。  
  
2.  私用程序建構 LOB 應用程式訊息。 這包括取得 LOB 訊息範本、序列化 XML 服務內容以及載入 XML 訊息部分到 LOB 訊息。  
  
3.  在前往 LOB 應用程式的途中，私用程序會傳送訊息到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessagesFromLOB 資料表。  
  
4.  如果原始訊息有附件，私用程序會呼叫 AttachmentHelper 元件來處理附件。  
  
5.  私用程序傳送通知到 LOB 應用程式，而 LOB 應用程式已將回應訊息儲存在 MessagesToLOB 資料表。  
  
6.  如果訊息是單向動作訊息，私用程序就完成了。  
  
7.  如果訊息是雙向動作訊息，私用程序會接聽來自 LOB 應用程式的回應。  
  
8.  當私用程序接收來自 LOB 應用程式的回應時，會建構回應訊息，並傳送訊息到公開程序。  
  
9. 私用程序會等候來自公開程序的信號。 如果收到信號，便會建構 LOB 信號訊息並傳送到 LOB 應用程式。 如果 RNIF 是 1.1 版，私用程序將接聽第二個通知信號，而且在接收該信號時，將建構 LOB 信號訊息並傳送到 LOB 應用程式。 私用程序每次傳送信號訊息之後都會通知 LOB 應用程式。  
  
10. 從啟動者傳送過來的途中，如果私用程序從公開程序接收到「失敗通知」(NoF) 訊息，便會建構 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Exception 訊息並傳送到 LOB 應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [私用程序](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)   
 [啟動者私用程序](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md)   
 [協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [PrivateResponder 範例](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)