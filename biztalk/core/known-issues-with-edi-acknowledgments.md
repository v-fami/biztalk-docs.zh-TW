---
title: EDI 通知的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a769a78e-8a49-4aa4-899e-e9f54fdd5f37
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f02ef54ed8786f8ead12e16fad880040dbcadc8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262238"
---
# <a name="known-issues-with-edi-acknowledgments"></a>EDI 通知的已知問題
本主題說明 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中有關 EDI 通知的已知問題。  
  
## <a name="ak102-in-a-997-acknowledgment-can-be-negative"></a>997 通知中的 AK102 可能為負值  
 X12 997 通知中的 AK102 資料元素 (群組控制編號) 可能為負值。 即使負值的群組控制編號沒有意義，含負 AK102 資料元素的通知仍然會通過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所執行的驗證。  
  
## <a name="a-contrl-receipt-may-report-a-status-of-accepted-when-part-of-the-message-is-rejected"></a>CONTRL 回條可能在部分訊息遭拒時報告已接受狀態  
 CONTRL 回條 (EDIFACT 技術通知) 只會在內送 EDIFACT 訊息發生重複或是信封中發生錯誤 (例如，字元集發生問題) 時報告「已拒絕」狀態。 不同於 X12 在 TA1 通知中 TA104 欄位，EDIFACT 不會在 CONTRL 技術通知中報告「交換已接受，發生錯誤」狀態。 若已接受部分 EDIFACT 訊息，CONTRL 技術通知將會報告「已接受」。 在一些情況下，部分訊息雖然將遭到拒絕，但是 CONTRL 通知仍會報告「已接受」狀態。 在這種情況下，UCI5 元素可能會報告此等錯誤。  
  
## <a name="x12-acknowledgments-will-show-accepted-for-a-preserved-interchange-suspend-interchange-on-error-when-a-group-header-or-trailer-is-in-error"></a>群組標題或結尾發生錯誤時，X12 通知會顯示已接受保留的交換 (發生錯誤時暫停交換)  
 如果 X12 訊息的輸入批次處理選項設定為「保留交換 - 發生錯誤時暫停交換」，而且群組標題或結尾內有一個欄位無效，則 TA1 和 997 通知中將報告「已接受」狀態。 EDI 狀態報告和交易集詳細資料也會指出「已接受」的狀態。 即使交換將遭擱置，也會出現這種情形，而且「事件檢視器」中的錯誤會指出交換已經遭擱置。  
  
 TA1 通知會顯示「已接受」的狀態，因為它的目的在於驗證 ISA 標頭和 ISA 結尾的正確性，不是 GS 標頭和 GE 結尾的正確性。 然而，997 通知還是會顯示「已接受」的狀態。  
  
## <a name="if-groups-in-an-interchange-have-the-same-name-the-status-report-will-show-twice-as-many-acknowledgments"></a>若交換中的群組有相同名稱，則狀態報告會顯示兩倍的通知。  
 若 BizTalk Server 處理的 EDI 交換有多個群組名稱相同，EDI 交換和相互關聯的 ACK 狀態報表，會列出比預期多一倍的功能通知。 例如，若某個交換中有兩個群組的名稱相同，則狀態報告會列出四則通知而不是兩則通知。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 處理的已知的問題](../core/known-issues-with-edi-processing.md)   
 [傳送 EDI 通知](../core/sending-an-edi-acknowledgment.md)   
 [處理接收的通知](../core/processing-a-received-acknowledgment.md)   
 [設定 EDI 通知](../core/configuring-edi-acknowledgments.md)