---
title: 通知的已知的問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- known issues, acknowledgements
- acknowledgements, known issues
ms.assetid: cb45f80e-ba89-4b3f-a770-4b1cf9b8e220
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f585c9f0b147f50bd915bb757a3ed3c09a56ee8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966151"
---
# <a name="acknowledgments-known-issues"></a>通知的已知的問題
本節包含可協助您避免通知 (ACK) 錯誤的有用資訊。  
  
## <a name="hl7-v21-acknowledgment-message-accepted-even-if-it-contains-msa6-field"></a>HL7 V2.1 通知訊息，即使它包含 MSA6 欄位接受  
 Microsoft [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會接受 HL7 V2.1 通知訊息，即使包含 MSA6 欄位。  
  
## <a name="msa-01-value-not-generated-for-commit-acknowledgment-errors"></a>不產生認可通知錯誤的 MSA-01 值  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 不會產生認可通知錯誤 (CE) 的 MSA-01 通知程式碼。  
  
## <a name="two-way-mllp-adapter-might-not-detect-a-problem-with-an-ack"></a>雙向 MLLP 配接器可能無法偵測出問題與通知  
 當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]收到 ACK 在雙向的 MLLP 配接器，配接器會執行輕量型驗證上的認可，以判斷其有效性。 如果找到有效，擷取 MSA1 欄位時，並根據其值，配接器會重試、 暫止，或刪除原始訊息的 ACK 已回應。 不過，由於配接器所執行的驗證不是完整的驗證，就可以配接器不會偵測到問題的通知。 比方說，配接器無法判斷通知是有效的並刪除原始的訊息，而管線會判斷通知不是語式正確，並擱置的通知訊息。  
  
## <a name="v2xml-acks-with-multiple-errors-will-fail-validation"></a>V2。有多個錯誤的 XML 通知將無法通過驗證  
 如果內送的 V2。XML 訊息包含多個錯誤，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析器可能會產生 V2。在 [錯誤] 欄位中的多個錯誤的 XML 通知。 V2。XML 通知將無法通過驗證，因為 HL7 標準可讓您指定剖析器可以報告在 V2 中的一個錯誤。XML 通知錯誤的欄位。  
  
## <a name="mllp-performance-counters-do-not-count-acks"></a>MLLP 效能計數器不算 Ack  
 一種測量[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]MLLP 效能計數器所示，效能是 MLLP 配接器所處理的訊息數目。 這個計數會測量已接收或傳送的訊息的數目。 不過，計數不會衡量接收或傳送的通知數目。  
  
## <a name="nak-generated-by-two-way-mllp-adapter"></a>雙向 MLLP 配接器所產生的 NAK  
 雙向的 MLLP 配接器會擱置訊息，當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]產生 NAK （負值通知），並將它放置在 MessageBox 資料庫。 這可能是未預期的行為。 您可能想要移除 NAK 從 MessageBox 資料庫，或將它對應到另一個訊息。  
  
## <a name="data-type-of-an-ack-to-a-batch-message"></a>資料類型的通知設定為批次訊息  
 在產生回應的批次訊息的 ACK 訊息，GUID，而不是根據批次訊息中的 [MSH10] 欄位的資料類型，將會 MSH10 欄位 (訊息控制項 ID)。  
  
## <a name="generated-acknowledgments-doc-type"></a>產生的通知文件類型  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 產生使用文件類型的通知 http://Microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF 或 http://Microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF 。 如果您的目的合作對象使用不同的命名空間，您必須套用本文中對應的傳送埠;否則，您可能會發生序列化錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [已知問題](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)