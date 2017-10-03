---
title: "啟動者公開程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public processes, initiator
- CIDX, 0A1 messages
- messages, 0A1 messages
- messages, message flow
- messages, public processes
- 0A1 messages
- public processes, message flow
ms.assetid: 371d0792-d346-405b-a8f4-2dfa64dd1566
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df1565915d36f3036543ff69c5da680d5949dc74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="initiator-public-process"></a>啟動者公開程序
此程序會建立並傳送初始 RNIF 商務訊息，以在啟動者系統上初始 RosettaNet 實作架構 (RNIF) 訊息。  
  
## <a name="message-flow-in-the-initiator-public-process"></a>啟動者公開程序中的訊息流程  
 通過啟動者公開程序的訊息流程如下所示：  
  
1.  啟動者公開程序透過服務內容傳輸埠，從私用程序接收服務內容以及附件。  
  
2.  公開程序傳送回應至私用程序，但不會進一步處理。  
  
3.  如果公開程序會收到通知， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]未能成功傳送訊息，公開程序傳回給啟動者私用程序，會將該狀態，然後結束。  
  
4.  如果公開程序收到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 成功傳送訊息的通知，程序便會進入等候狀態 (等候回應者的動作)。  
  
5.  下列動作可以結束等候狀態：  
  
    1.  公開程序接收來自回應者的確認信號。  
  
         如果需要不可否認性信號 (在程序組態設定中設定)，程序便會讀取摘要，並設定信號中的摘要與原始動作訊息摘要的關聯，然後持續發出信號。  
  
         公開程序傳送信號的標頭以及服務內容至私用程序。  
  
    2.  公開程序接收來自回應者的雙向動作回應訊息。  
  
         程序從回應訊息取出服務內容以及標頭，然後傳送至私用程序。  
  
         如果活動是同步的，公開程序便會將服務內容訊息部分與前序、服務標頭及傳遞標頭 (僅針對 RNIF 2.01) 包裝起來以建構 RNIF 信號訊息。 程序使用關於來源和合作對象的組態資訊以建立前序和標頭，以及儲存在不同合作對象之間交易夥伴協議中的 PIP 變數。 接著，程序傳送信號訊息至回應者。  
  
         如果活動為非同步，程序便會結束。  
  
    3.  公開程序接收來自回應者的「失敗通知」(NoF) 訊息。 公開程序傳送相對的狀態訊息至啟動者私用程序。 接著，私用程序會處理錯誤且一併結束兩個程序。  
  
    4.  公開程序在「通知時間」時段 (在程序組態設定中設定) 之內不會接收來自回應者的確認信號。 若是如此，會發生下列其中一種狀況：  
  
         如果重試次數 (在程序組態設定中設定) 未達到零，並且活動為非同步，公開程序便會再次傳送訊息。  
  
         如果重試次數 (在程序組態設定中設定) 未達到零，並且活動是同步的，公開程序便會初始 0A1 訊息。  
  
        > [!NOTE]
        >  CIDX 不支援 0A1 訊息。  
  
         如果重試次數在沒有成功傳送的情況下達到零，公開程序會張貼錯誤訊息，且如果不是 CIDX，公開程序便會傳送 0A1 訊息。  
  
         如果此活動為同步，而且這不是 CIDX，則公開程序會初始 0A1 訊息。  
  
    5.  如果在「執行時間」內未發生任何動作，而且這不是 CIDX，則公開程序會傳送 0A1 訊息。  
  
## <a name="see-also"></a>另請參閱  
 [公開程序](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md)   
 [回應者公開程序](../../adapters-and-accelerators/accelerator-rosettanet/responder-public-process.md)