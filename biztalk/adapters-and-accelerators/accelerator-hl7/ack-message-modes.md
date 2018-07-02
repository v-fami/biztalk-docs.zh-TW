---
title: ACK 訊息模式 |Microsoft Docs
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
ms.openlocfilehash: 181617a41ba892a8ac04f2bf2154bbe78e8c892e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967849"
---
# <a name="ack-message-modes"></a>ACK 訊息模式
針對通知 (ACK) 訊息，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 決定要用於填入您想要產生通知的電子郵件地址 和 MSH16 MSH15 欄位值與通知模式。 這些值會出現在交易夥伴管理 (TPM) 組態。 下列是可能值為 ACK 模式：  
  
> [!NOTE]
>  在下列清單中，HL7 規格會強制項目 1 到 3，以及它們包含 MSH15 和 MSH16 值。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 定義項目 4，表示不產生通知。  
  
1. 原始-一個通知之後驗證標頭和本文傳送。 此模式都會涉及結構描述驗證。  
  
2. 增強式-傳送兩則通知訊息：  
  
   -   接受通知 – 接收端系統的標頭驗證之後傳送這種類型的通知。 此通知告知起始應用程式的訊息是認可到資料庫。  
  
   -   應用程式通知接收系統會傳送這種類型的通知之後完成的訊息驗證，包括標頭和主體。  
  
3. 延遲-傳送兩則通知訊息。  
  
   - 原始的模式： 接收端系統會在驗證標頭和本文之後，傳送這種類型的通知。 此模式都會涉及結構描述驗證。  
  
   - 延後模式： 特定業務應用程式會在處理它之後，確認訊息。 應用程式提供的延後的訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，其處理為獨立的訊息，並將其傳遞到目的地。  
  
4. 靜態-在成功或失敗傳送通知。  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [程式設計手冊](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [ACK 處理序模型](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md)   
 [靜態通知](../../adapters-and-accelerators/accelerator-hl7/static-acknowledgments.md)