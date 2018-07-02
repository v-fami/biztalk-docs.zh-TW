---
title: MLLP 配接器的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MLLP adapters, known issues
- known issues, MLLP adapters
ms.assetid: 66af8fcc-981a-4a77-80b7-84824bfae608
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb90c62baebb8fc73b939c0a3ea20eb85e9b0e28
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970831"
---
# <a name="mllp-adapter-known-issues"></a>MLLP 配接器的已知問題
本節包含可協助您避免最少的較低層通訊協定 (MLLP) 配接器錯誤的有用資訊。  
  
## <a name="two-way-mllp-adapter-might-not-detect-a-problem-with-an-ack"></a>雙向 MLLP 配接器可能無法偵測出問題與通知  
 當 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]) 接收通知 (ACK) 上的雙向的 MLLP 配接器，配接器會執行輕量型驗證上的認可，以判斷其有效性。 如果找到有效，擷取 MSA1 欄位時，並根據其值，配接器會重試、 暫止，或刪除原始訊息的 ACK 已回應。 不過，由於配接器所執行的驗證不是完整的驗證，就可以配接器不會偵測到問題的通知。 比方說，配接器無法判斷通知是有效的並刪除原始的訊息，而管線會判斷通知不是語式正確，並擱置的通知訊息。  
  
## <a name="mllp-performance-counters-do-not-count-acks"></a>MLLP 效能計數器不算 Ack  
 MLLP 效能計數器所示，效能的一個量值會是處理 MLLP 配接器的訊息數目。 這個計數會測量已接收或傳送的訊息的數目。 不過，計數不會衡量接收或傳送的通知數目。  
  
## <a name="mllp-adapter-connection-names-are-not-guaranteed-to-be-unique"></a>不保證是唯一的 MLLP 配接器連接名稱  
 [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] 不保證唯一性的 MLLP 配接器的屬性頁面中輸入的連接名稱。 確定該描述性及相關連接此必要欄位中輸入名稱。 使用代表特定業務應用程式的連接名稱可能會很有用，嘗試了解連接的行為時。 比方說，PerfMon 計數器使用的連接名稱。  
  
> [!NOTE]
>  BTAHL7 並確保唯一性的接收位置或傳送埠名稱。  
  
## <a name="two-way-mllp-adapters-do-not-send-commit-acks-for-all-messages-in-a-batch"></a>雙向 MLLP 配接器不會傳送認可的認可的批次中的所有訊息  
 當您設定每個訊息批次處理，以產生認可的通知，並在系統傳送的批次雙向 MLLP 接收配接器，配接器只會傳送對應至第一個訊息批次中認可的通知。  
  
> [!NOTE]
>  建議您，使用單向的 MLLP 配接器傳輸批次。  
  
## <a name="nak-generated-by-two-way-mllp-adapter"></a>雙向 MLLP 配接器所產生的 NAK  
 雙向的 MLLP 配接器會擱置任何訊息，當 MLLP 配接器就會產生 NAK （負值通知），並將它放在 MessageBox 資料庫。 這可能是未預期的行為。 您可能想要移除 NAK 從 MessageBox 資料庫，或將它對應到另一個訊息。  
  
## <a name="two-way-mllp-adapter-only-supports-the-2x-message-format"></a>雙向 MLLP 配接器只支援 2.X 訊息格式  
 雙向的 MLLP 配接器目前支援僅 2.X 訊息格式。  
  
## <a name="two-way-mllp-adapter-does-not-support-static-acknowledgments"></a>雙向 MLLP 配接器不支援靜態通知  
 雙向傳送配接器不支援處理靜態的通知。  
  
## <a name="see-also"></a>另請參閱  
 [已知問題](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)