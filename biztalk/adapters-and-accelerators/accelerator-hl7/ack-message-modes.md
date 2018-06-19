---
title: ACK 訊息模式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message modes, ACK messages
- messages, acknowledgements
- acknowledgements, message modes
- ACK message modes
ms.assetid: ab4a9470-dab2-46d4-8d0a-54dc12f2fa90
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 122f0851005c7d8abba6c1739ae86a1d65d89625
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204398"
---
# <a name="ack-message-modes"></a>ACK 訊息模式
通知 (ACK) 訊息[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會決定通知模式以及要使用用來填入您想要產生的 ACK MSH15 和 MSH16 欄位的值。 這些值會出現在交易夥伴管理 (TPM) 組態。 通知模式可能會有下列值：  
  
> [!NOTE]
>  在下列清單中，HL7 規格會強制項目 1 至 3，且包含 MSH15 和 MSH16 值。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]定義項目 4，表示不應該產生通知。  
  
1.  原始-一個通知之後驗證標頭和本文傳送。 此模式中包含結構描述驗證。  
  
2.  增強的兩個傳送的通知訊息：  
  
    -   接受通知 – 接收端系統的標頭驗證之後傳送這種類型的通知。 這 ACK 通知起始應用程式訊息是向資料庫認可。  
  
    -   應用程式通知接收系統會傳送這種類型的通知之後完成的訊息驗證，包括標頭和主體。  
  
3.  延後的兩個傳送的通知訊息。  
  
    -   原始模式： 接收端系統的標頭和主體的驗證之後傳送這種類型的通知。 此模式中包含結構描述驗證。  
  
    -   延後的模式： 特定業務應用程式確認訊息之後加以處理。 應用程式能夠提供延後的訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，其處理做為獨立的訊息，並將其傳遞到目的地。  
  
4.  靜態-在成功或失敗認可。  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [程式設計手冊](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [ACK 處理序模型](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md)   
 [靜態通知](../../adapters-and-accelerators/accelerator-hl7/static-acknowledgments.md)