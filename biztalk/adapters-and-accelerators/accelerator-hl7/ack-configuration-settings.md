---
title: ACK 組態設定 |Microsoft Docs
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
ms.openlocfilehash: 06cedaee1ca0ad574920cfb646f69d63157c8e67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968055"
---
# <a name="ack-configuration-settings"></a>ACK 組態設定
Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]剖析器會產生交易夥伴管理 (TPM) 設定為基礎的通知。 通知 (ACK) 設定需仰賴夥伴資訊。 不使用結構描述型別。 當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]收到通知訊息與 MSH15 欄位包含 AL、 SU 或 ER，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可能會傳送此訊息的 ACK 標頭和 TPM 設定剖析的結果為基礎的認可。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 擷取夥伴通知的設定，並傳回下列五個值之一：  
  
> [!NOTE]
>  HL7 規格會強制您使用 1 到 4，並填入您所產生的 ACK 訊息 MSH15 欄位的項目。 項目 5 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]-特定和代表不產生通知。  
  
1.  AL – 一律  
  
2.  NE – 永遠不會  
  
3.  SU-成功  
  
4.  ER-錯誤  
  
5.  否，不會產生通知  
  
## <a name="ack-configuration-inconsistency"></a>ACK 組態不一致  
 在通知組態使用者介面設定與訊息執行個體 MSH15 和 MSH16 欄位內的值之間不一致的情況下[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]其中兩個通知產生觸發程序需要它時，會傳送通知。 在其他的不一致的情況下執行個體中的資料會覆寫組態使用者介面中的設定。  
  
## <a name="see-also"></a>另請參閱  
 [設定訊息通知](../../adapters-and-accelerators/accelerator-hl7/configuring-message-acknowledgments.md)   
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)