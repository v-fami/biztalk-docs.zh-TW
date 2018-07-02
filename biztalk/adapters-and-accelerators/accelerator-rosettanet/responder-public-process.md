---
title: 回應者公開程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, message flow
- messages, public processes
- public processes, message flow
- public processes, responder
ms.assetid: 78d83954-2998-44ac-a527-5e5858c61009
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6565f10b311a504edbd3323cc0fe3b318c7b2410
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981063"
---
# <a name="responder-public-process"></a>回應者公開程序
回應者的這個公開程序會接收來自啟動者的 RosettaNet 實作架構 (RNIF) 訊息並依此回應。  
  
## <a name="message-flow-in-the-responder-public-process"></a>回應者公開程序中的訊息流程  
 透過回應者公開程序的訊息流程如下：  
  
1. 回應者公開程序從回應者 MessageBox 資料庫接收 RNIF 訊息。  
  
2. 公開程序從動作訊息擷取服務內容和標頭，然後傳送至私用程序。  
  
   > [!NOTE]
   >  回應者公開程序針對內送訊息執行標準驗證 (以及包含在驗證配接器中的任何其他驗證)。 如果驗證成功，公開程序將會初始化應用程式配接器，依照特定的實作方式來執行通知。 回應者公開程序會將訊息儲存在 MessageBox 資料庫中，並通知已經將訊息儲存至 MessageBox 的回應者私用程序 (使用 `BeginNotify` 類別中的 `ApplicationAdapter` 方法)。 如需有關驗證配接器和應用程式配接器的詳細資訊，請參閱 < [ValidationAdapter &#91;RN3&#93; ](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md)並[ApplicationAdapter &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md)。  
  
3. 如果活動是非同步且為單向動作，公開程序便會將服務內容訊息部分與前序、服務標頭及傳遞標頭 (僅針對 RNIF 2.01) 包裝起來以建構 RNIF 信號訊息 (通知接受)。 公開程序建構前序、 服務標頭和傳遞標頭使用儲存在合作對象之間交易夥伴協議的資訊： 程序組態設定、 有關來源的組態資訊和目的合作對象，以及交易夥伴介面程序 (PIP) 變數。 接著，程序會傳送信號訊息至啟動者。  
  
   > [!NOTE]
   >  如果訊息是單向動作訊息，訊息流程就完成了。  
  
4. 公開程序進入等候狀態 (等候回應者私用程序的動作)。  
  
5. 下列動作可以結束等候狀態 (等候回應者私用程序的動作)：  
  
   1. 回應者私用程序傳回回應服務內容和標頭，以回應原始動作訊息 (此為雙向動作訊息)。  
  
       如果公開程序會從私用程序接收回應服務內容，公開程序以建構 RNIF 訊息，其中包含服務內容。 它的做法是將服務內容訊息部分、包含來源合作對象和目的合作對象組態資訊的標頭，以及儲存於交易夥伴協議中的 PIP 變數包裝起來。  
  
       公開程序使用「動作/信號角色」(Action/Signal Role) 連結埠，傳送 RNIF 訊息給啟動者。  
  
       如果公開程序就會收到通知，Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]未能成功傳送訊息，公開程序會將該狀態回傳至私用程序，然後結束。  
  
       如果公開程序收到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 成功傳送訊息的通知，程序便會進入等候狀態 (等候啟動者的動作)。 此等候狀態與啟動者在等候回應者的動作時的等候狀態類似。  
  
   2. 公開程序接收來自啟動者的「失敗通知」(NoF) 訊息。  
  
   > [!NOTE]
   >  回應者私用程序將在成功處理內送訊息後，通知回應者公開程序。 只有在回應者公開程序接收到此通知之後 (透過 `EndNotify` 類別中的 `ApplicationAdapter` 方法)，回應者公開程序才算成功完成。  
  
6. 回應者公開程序進入等候狀態 (等候接收啟動者的信號，以對回應者公開程序所傳送的回應訊息發出回應)。  
  
## <a name="see-also"></a>另請參閱  
 [公開程序](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md)   
 [啟動者公開程序](../../adapters-and-accelerators/accelerator-rosettanet/initiator-public-process.md)   
 [ApplicationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md)   
 [ValidationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md)