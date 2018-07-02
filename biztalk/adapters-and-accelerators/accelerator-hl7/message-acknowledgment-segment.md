---
title: 訊息通知區段 |Microsoft Docs
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
ms.openlocfilehash: a8f771968e6d7c7f58ccd8d3e68b43aac0eb64e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968495"
---
# <a name="message-acknowledgment-segment"></a>訊息通知區段
通知 (ACK) 訊息的訊息通知 」 (MSA) 區段識別何種系統傳送，並指出哪些訊息通知認可通知。 它包含兩個必要區段： 認可程式碼和訊息的控制項識別碼。  

## <a name="acknowledgment-code-msa1"></a>通知程式碼： MSA1  
 下表列出可用的 MSA1 欄位值，指出訊息接收的結果。  

|ReplTest1|意義|描述|  
|-----------|-------------|-----------------|  
|AA|應用程式通知|系統已收到訊息，並處理任何問題。|  
|AE|應用程式錯誤|訊息或其結構與相關的處理問題發生在接收應用程式。 傳送的系統應該診斷並更正問題，然後再嘗試重新傳送訊息。|  
|AR|應用程式的拒絕|問題發生在接收位置相關 MSH9 中的值 （訊息類型）、 MSH11 （處理識別碼），或 MSH12 （版本識別碼），在此情況下傳送的系統應該診斷並更正問題後再重新傳送訊息，或在已不相關的訊息或它的結構，在其中情況下，傳送端系統應重新傳送訊息後，不會變更訊息至接收端系統發生問題。|  

## <a name="message-control-id-msa2"></a>訊息的控制項 ID (MSA2)  
 MSA2 欄位識別認可通知訊息。 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會產生在 MSA2 通知模式為基礎的值。 這個值會啟用傳送和接收應用程式，讓訊息維持和同步處理通知。 下表列出可用的值，以 MSA2 欄位。  


|            通知模式            |                                                           MSA2 中的值                                                            |
|-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
|               原始的模式               |                  已轉置 MSH10 中值的值 （訊息的控制項 ID），原始訊息的欄位                   |
|   增強的模式： 認可通知    |                  已轉置 MSH10 中值的值 （訊息的控制項 ID），原始訊息的欄位                   |
| 增強的模式： 應用程式通知 | 所產生的 GUID[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通知 |

## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [ACK 訊息結構描述類型](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md)   
 [設定傳送埠來接收 Ack](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)   
 [通知錯誤狀況](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)