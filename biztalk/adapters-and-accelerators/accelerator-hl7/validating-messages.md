---
title: "驗證訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, acknowledgements
- messages, acknowledgements
- acknowledgements, validating
- validating, messages
- acknowledgements, messages
- messages, validating
ms.assetid: 7dba0f40-5e19-4598-82cb-22c71e9536c6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1edaffcab50d6a8af508cb16c9eede39c5ddb952
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="validating-messages"></a>驗證訊息
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援的內送訊息傳送通知 (ACK)，從應用程式或交易夥伴的 HL7 XML 接收，這可能需要轉換成 HL7 形式編碼通知訊息。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]它會檢查傳入的訊息和相關輸入 （交易夥伴格式） 文件規格之後，通常會產生在回條。 當所有區段都通過驗證，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳回回條，表示接受應用程式。 否則，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]產生指出錯誤或失敗/拒絕的回條。  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ACK 傳輸報告針對 HL7 標準的語法和圖解錯誤。 如果驗證失敗，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]置於擱置的訊息佇列中的文件，並傳回詳述拒絕的回條。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析器會執行包含檢查資料型別、 語法和結構描述驗證的驗證。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]記錄發生的任何圖解錯誤以及位置詳細資料的回條的剖析。  
  
 在設定的時間，您必須建立[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]通知以回應所需的成品 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析器會建立標準 HL7 通知 XML 執行個體。 BizTalk 會將此轉換成適當的 BizTalk 對應的必要的版本格式，並驗證目的格式。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式再將訊息轉換成 HL7 編碼執行個體。  
  
> [!NOTE]
>  如果傳入訊息的分隔符號之間沒有衝突，而且在指定的那些[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態，然後[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生通知訊息，會使用相同的分隔符號輸入訊息，並覆寫組態設定。  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [程式設計手冊](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [ACK 訊息模式](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)