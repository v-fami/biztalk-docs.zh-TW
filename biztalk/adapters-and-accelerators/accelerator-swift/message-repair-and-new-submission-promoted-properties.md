---
title: "Message Repair 和 New Submission 升級屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- promoted properties, Message Repair and New Submission
- Message Repair and New Submission, promoted properties
ms.assetid: e980c905-d07f-4fc2-89ca-05e597410733
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76e4f57e9f5179ceea073ef281131a8cd3573703
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-repair-and-new-submission-promoted-properties"></a>Message Repair 和 New Submission 升級屬性
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair 和 New Submission 對帳包含下列的升級的屬性。  
  
|升級的名稱|Description|資料類型|數值範圍|使用範例|  
|-------------------|-----------------|---------------|-----------------|-------------------|  
|**BTS。作業**|表示狀態[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]處理。 可以是下列其中一項：<br /><br /> **A4SWIFT_MrsrCompleted**指出訊息修復和新送出程序成功。<br /><br /> **A4SWIFT_MrsrFailed**表示訊息修復和新送出程序失敗。<br /><br /> **A4SWIFT_MrsrUnparsedFailed**表示未剖析的訊息修復失敗。<br /><br /> **A4SWIFT_MrsrUnparsedComplete**表示成功的修復未剖析的訊息。<br /><br /> **A4SWIFT_DasmMarkedAsFailed**指示訊息未能在接收管線的解譯器 」 階段中處理。|字串|-A4SWIFT_MrsrCompleted<br />-A4SWIFT_MrsrFailed<br />-A4SWIFT_MrsrUnparsedFailed<br />-A4SWIFT_MrsrUnparsedCompleted<br />-A4SWIFT_DasmMarkedAsFailed|當 MrsrRepair 協調流程會在修復後收到修復未剖析的訊息時，它會設定**BTS。作業**"A4SWIFT_MRSRCompleted"的屬性和**A4SWIFT_Failed**屬性設定為 False，然後將訊息路由傳送至 MessageBox。 這些屬性確定，修復未剖析的訊息不會輸入訊息修復程序一次。|  
|**Microsoft.Solutions.A4SWIFT。Property.A4SWIFT_Failed**|指出是否[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]成功或失敗處理訊息。|布林|True、False|使用 MrsrRepair 協調流程只能訂閱訊息從 MessageBox 驗證失敗。|  
|**Microsoft.Solutions.A4SWIFT。Property.A4SWIFT_SwiftBound**|指出訊息 SWIFT 網路繫結。|布林|True、False|使用 MrsrRepair 協調流程只能訂閱訊息從 MessageBox SWIFT 網路繫結。|  
|**Microsoft.Solutions.A4SWIFT。MRSRProperty.A4SWIFT_MRSRIsNewSubmission**|指出正在處理的訊息是否為新送出。|布林|True、False|使用 MrsrRepair 協調流程來表示已在工作流程的建立階段中建立的訊息。|  
|**Microsoft.Solutions.A4SWIFT。MRSRProperty.A4SWIFT_MRSRLastStage**|表示已成功修復工作流程中的最後一個階段。|字串|-|其中一個部門工作流程定義的階段。 可以是 create、 修復、 重設金鑰驗證，或核准階段。|  
|**Microsoft.Solutions.A4SWIFT。MRSRProperty.A4SWIFT_ MRSRDepartment**|表示用於訊息修復和新送出，MrsrDepartmentPolicy BRE 原則所指定的部門。|字串|-|在中設定[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管理主控台。|  
|**Microsoft.Solutions.A4SWIFT。MRSRProperty.A4SWIFT_ MRSRFailedReason**|表示訊息修復和新送出程序失敗的原因。 可以是下列其中一項：<br /><br /> 拒絕表示使用者已拒絕的訊息內[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。<br /><br /> InvalidDigitalSignature 表示使用者的憑證無效。<br /><br /> Timeout 表示已達到 MRSROrchestration 逾時值。<br /><br /> InvalidWorkFlow 指出部門所定義的工作流程無效。<br /><br /> CantRepairIn[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]不可以在中開啟內送 XML 訊息會指出[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]。<br /><br /> 一般例外狀況|字串|-拒絕<br />-InvalidDigitalSignature<br />逾時<br />-InvalidWorkFlow<br />-一般例外狀況<br />-CantRepairIn[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]|設定由訊息修復和新送出的協調流程之後的處理序失敗。|  
  
## <a name="see-also"></a>另請參閱  
 [A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)   
 [FIN 回應對帳升級屬性](../../adapters-and-accelerators/accelerator-swift/fin-response-reconciliation-promoted-properties.md)