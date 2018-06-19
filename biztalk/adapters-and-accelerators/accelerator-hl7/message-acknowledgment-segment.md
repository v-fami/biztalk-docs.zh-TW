---
title: 訊息通知區段 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- segments, acknowledgements
- acknowledgements, segments
ms.assetid: 6f2b9f6f-a328-4a0f-9e7d-edba32cc045a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9547b6d8ddf3013facd94930b5d91ec42db0e5d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204934"
---
# <a name="message-acknowledgment-segment"></a>訊息通知區段
通知 (ACK) 訊息的訊息通知 (MSA) 區段會識別哪些類型的通知系統傳送，並指出哪些訊息認可通知。 它包含兩個必要區段： 認可程式碼和訊息的控制項識別碼。  
  
## <a name="acknowledgment-code-msa1"></a>通知程式碼： MSA1  
 下表列出可用的 MSA1 欄位值，指出訊息接收的結果。  
  
|值|意義|Description|  
|-----------|-------------|-----------------|  
|AA|應用程式通知|系統已收到訊息並處理沒有解決問題。|  
|AE|應用程式錯誤|此訊息或其結構與相關的處理問題發生在接收應用程式。 傳送系統應該診斷並更正問題，再嘗試重新傳送訊息。|  
|AR|應用程式的拒絕|問題發生在接收位置相關 MSH9 中的值 （訊息類型），MSH11 （處理識別碼），或 MSH12 （版本識別碼），在此情況下傳送系統應該診斷並更正問題後再重新傳送訊息。或在接收端系統的相關訊息或它的結構，在其中傳送系統案例應重新傳送訊息適當的時間，而不需要變更至訊息後發生的問題。|  
  
## <a name="message-control-id-msa2"></a>訊息控制項 ID (MSA2)  
 MSA2 欄位識別認可通知訊息。 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 產生認可模式為基礎的 MSA2 中的值。 這個值會啟用傳送和接收應用程式，讓訊息維持與處理通知。 下表列出可用 MSA2 欄位的值。  
  
|認可模式|MSA2 中的值|  
|-------------------------|-------------------|  
|原始模式|MSH10 中的值已轉置的值 （訊息控制項 ID） 的原始訊息欄位|  
|增強的模式： 認可通知|MSH10 中的值已轉置的值 （訊息控制項 ID） 的原始訊息欄位|  
|增強的模式： 應用程式通知|所產生的 GUID[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通知|  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [ACK 訊息結構描述類型](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md)   
 [設定傳送埠來接收通知](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)   
 [通知錯誤狀況](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)