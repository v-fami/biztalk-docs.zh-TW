---
title: "MLLP 接收和傳送元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send components
- Minimal Lower Layer Protocol (MLLP)
- MLLP adapters
- MLLP adapters, wrappers
- wrappers [MLLP adapters]
- receive components
ms.assetid: 2f1c4099-8f52-437a-bdc1-efe707fbf347
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e135b98c04531aa6200f3b79c5b6d5153bf299a7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="mllp-receive-and-send-components"></a>MLLP 接收和傳送元件
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援所有[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]原生配接器類型，包括 File、 HTTP、 SQL、 與 FTP。 HL7 編碼的訊息接收和傳送，不過，您通常使用 MLLP 配接器。 此配接器是使用最低限度的較低層通訊協定 (MLLP) 的 TCP/IP 通訊端介面卡。 此通訊協定提供雙向的訊息支援與端對端醫療保健應用程式整合。  
  
 您可以設定 MLLP 為雙向配接器或單向配接器接收配接器。 您可以設定 MLLP 傳送配接器，為雙向請求-回應傳送配接器、 單向傳送配接器設定為接收通知 (Ack) 上相同的通訊端連線，或單向傳送配接器不會傳回任何訊息。 當您使用雙向請求-回應傳送 MLLP 配接器時，您可以設定要傳回 Ack 或回應訊息的接收埠。 如需為 MLLP 的範例傳送和接收配接器，請參閱[Interrogative 教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)。  
  
 訊息[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接收或傳送的 MLLP 配接器上需要下列的包裝函式：  
  
-   \<SB\>啟動區塊字元  
  
-   \<EB\> End 區塊的字元  
  
-   \<CR\> （選擇性） 歸位字元傳回位元組  
  
 MLLP 配接器會提供錯誤處理遺漏\<SB\>或\<EB\>包裝函式、 卸除的連接或逾時。 與 MLLP 配接器，您可以設定限制的連線數目。 您可以使用 MLLP 配接器的通知分類。  
  
## <a name="see-also"></a>請參閱  
 [處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [BizTalk Accelerator for HL7 元件](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)