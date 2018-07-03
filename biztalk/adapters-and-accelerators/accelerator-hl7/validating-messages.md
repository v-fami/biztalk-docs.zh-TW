---
title: 驗證訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- validating, acknowledgements
- messages, acknowledgements
- acknowledgements, validating
- validating, messages
- acknowledgements, messages
- messages, validating
ms.assetid: 7dba0f40-5e19-4598-82cb-22c71e9536c6
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35894722d2c95f197a1fe4072c2229cf96fea64f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010055"
---
# <a name="validating-messages"></a>驗證訊息
Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 輸入訊息的傳送通知 (ACK)，從應用程式，或交易夥伴可能需要轉換到 HL7 HL7 XML 回條的形式支援編碼通知訊息。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 通常會產生一個回條之後它會檢查傳入的訊息和相關輸入 （交易夥伴格式） 文件規格。 當所有區段都通過驗證，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳回回條，表示應用程式的接受度。 否則，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生表示錯誤或失敗/拒絕的回條。  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通知傳輸報告對 HL7 標準的語法和圖解錯誤。 如果驗證失敗，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]置於擱置的訊息佇列中的文件，並傳回詳細說明拒絕的回條。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析器會執行牽涉到檢查資料型別、 語法和結構描述驗證的驗證。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 在接收位置的詳細資料以及剖析記錄發生的任何圖解錯誤。  
  
 在設定階段中，您需要建立[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]通知以回應所需的成品 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析器會建立標準 HL7 通知 XML 執行個體。 BizTalk 會將此轉換成適當的 BizTalk 對應中的所需的版本格式，並驗證目的格式。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式則會將訊息轉換成 HL7 編碼的執行個體。  
  
> [!NOTE]
>  如果傳入訊息的分隔符號之間沒有衝突，而且中所指定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態，然後[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生通知訊息會使用相同的分隔符號的輸入訊息，並覆寫組態設定。  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [程式設計手冊](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [ACK 訊息模式](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)