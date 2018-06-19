---
title: 批次處理的已知的問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, known issues
- known issues, batching
ms.assetid: 25c645eb-845d-483a-8f77-398e7dfe0c8f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b47246662c5945f8ef09040ec7a8aa49326f59db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204494"
---
# <a name="batching-known-issues"></a>批次處理的已知的問題
本節包含可協助您避免批次錯誤的有用資訊。  
  
## <a name="batch-trailer-segment-fts-and-bts-fields-are-accepted-even-if-they-are-strings"></a>批次 （FTS 和 BTS） 欄位所接受，即使它們是字串的結尾區段  
 HL7 FTS 與 BTS HL7 的各種版本不同的區段中指定的欄位。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]定義的所有欄位，以字串資料類型，以避免不一致。  
  
## <a name="data-type-of-an-ack-to-a-batch-message"></a>資料類型的批次訊息的通知  
 在批次訊息，如果來源合作對象的片段已關閉，然後 MSH10 回應中產生的通知 (ACK) 訊息欄位 (訊息控制項 ID) 就是 GUID，而不是 MSH10 欄位批次訊息中的任何其他資料類型。  
  
## <a name="btahl7-configuration-explorer-and-create-batch-orchestrations-are-not-two-way-synchronized"></a>BTAHL7 Configuration 總管 」 和 「 建立批次協調流程不是雙向同步處理  
 貴用戶無法檢視批次控制排程的目前狀態，即使您按下 F5 中的[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管 中，而可能同時檢查[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]目前組態總管和狀況與活動追蹤 (HAT) 工具批次控制排程的狀態。  
  
## <a name="two-parsing-errors-logged-when-messages-in-batch-inbatch-out-scenario-contain-validation-errors"></a>兩個剖析錯誤時記錄訊息中批次處理 / 批次出案例包含驗證錯誤  
 當第一個訊息批次中在 / 批次出情節 （不含批次標頭中批次處理多個訊息） 都會包含驗證錯誤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]事件記錄檔中記錄兩個錯誤。 第一個錯誤相關的批次中的第一個訊息，訊息的其餘部分都屬於第二個錯誤。  
  
## <a name="subscription-using-the-btsmessagetype-property-for-the-batch-inbatch-out-scenario-with-fragmentation-disabled-is-not-supported"></a>使用 BTS 的訂用帳戶。MessageType 屬性批次中不支援與停用的片段的批次出案例  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不支援訂用帳戶使用**BTS。MessageType**屬性批次中 / 片段停用，可能包含多個訊息類型的交換與批次出案例。  
  
## <a name="entire-batch-suspended-after-erroneous-message-in-the-batch-inbatch-out-scenario"></a>處理批次中的錯誤訊息後被擱置整個批次中 / 批次出案例  
 如果發生嚴重的剖析器錯誤訊息 (比方說，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不會剖析 MSH 9 或無法載入訊息的 MSH 12 或內文結構描述) 發生分散的批次中在批次出案例中，錯誤訊息將遭擱置之後的任何資料即使 / 如果可復原交換支援已啟用。  
  
## <a name="batch-of-acks-get-routed-to-the-source-party-of-the-first-message-in-batch-inbatch-out-scenario"></a>認可的批次會路由至第一個訊息批次中的來源合作對象中 / 批次出案例  
 在批次處理中 / 批次出案例的批次認可取得路由，根據來源合作對象資訊的第一個訊息，因為這項功能會假設輸入中的所有訊息批都次的來源和目的合作對象都相同。  
  
## <a name="batch-of-acks-does-not-get-routed-to-the-source-party-when-two-way-receive-port-is-used-in-batch-in-batch-out-scenario"></a>認可的批次不會不會路由至雙向時的來源合作對象接收批次中使用連接埠中 / 批次出案例  
 如果要求-回應接收的埠 ACK/NACK 批次並不會路由至 BIBO 實例的來源合作對象。  
  
## <a name="see-also"></a>另請參閱  
 [已知問題](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)