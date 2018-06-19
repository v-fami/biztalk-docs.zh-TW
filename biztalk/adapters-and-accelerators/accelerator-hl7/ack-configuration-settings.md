---
title: 通知設定的設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, configuring
- configuring, acknowledgements
ms.assetid: 46e92560-7b1e-4d53-9de8-8ded4de90695
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93dea42fd084f22b4644f0acbb21860d69f75027
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204406"
---
# <a name="ack-configuration-settings"></a>通知設定
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]剖析器產生根據交易夥伴管理 (TPM) 設定的通知。 這些是相依於交易夥伴資訊通知 (ACK) 設定。 不使用結構描述型別。 當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接收通知訊息與 MSH15 欄位包含 AL、 SU 或增，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可能會傳送此訊息的 ACK 標頭和 TPM 設定剖析的結果為基礎的通知。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]擷取夥伴通知設定，並傳回下列五個值之一：  
  
> [!NOTE]
>  HL7 規格會強制您使用 1 到 4，並填入 MSH15 ACK 訊息欄位所產生的項目。 項目 5 是[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]-特定代表不是用來產生通知。  
  
1.  AL – 永遠  
  
2.  NE – 永遠不會  
  
3.  SU-成功  
  
4.  ER： 錯誤  
  
5.  否-不會產生 ACK  
  
## <a name="ack-configuration-inconsistency"></a>通知組態不一致  
 在通知組態使用者介面設定與訊息執行個體 MSH15 和 MSH16 欄位內的值之間不一致的情況下[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]兩個通知產生觸發程序的其中一個在需要時傳送通知。 在其他的不一致的情況下執行個體中的資料將會覆寫組態使用者介面中的設定。  
  
## <a name="see-also"></a>另請參閱  
 [設定訊息通知](../../adapters-and-accelerators/accelerator-hl7/configuring-message-acknowledgments.md)   
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)