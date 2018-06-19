---
title: BTAHL72XML 處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2.XML messages, processing
- acknowledgements, 2.XML messages
- 2.XML messages, message modes
- message modes, 2.XML message
- 2.XML messages
- validating, 2.XML messages
- 2.XML messages, acknowledgements
- 2.XML messages, validating
ms.assetid: 2f12cb44-816c-4773-9db0-9cbc3d1b1aee
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e86697884c28d71fa9fb91c8b276293f7d36a588
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204678"
---
# <a name="btahl72xml-processing"></a>BTAHL72XML 處理
中的下列元件[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 處理 HL7 2.XML （XML 編碼） 訊息：  
  
-   管線與核心程式庫： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。PipelineCommon.dll 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。PipelineMessageCore.dll  
  
-   組合器和解譯器程式庫： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL72XmlAsm.dll 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL72XmlDAsm.dll  
  
-   通知 (ACK) 的驗證程式庫用於雙向 MLLP 傳送配接器： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL7ACKHelper.dll  
  
## <a name="xml-message-modes"></a>XML 訊息模式  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2.XML 訊息支援下列的訊息模式：  
  
-   發行者訂閱 (pub sub) 模式  
  
     「 發行者 」 端廣播給合作對象的 「 訂閱者 」 為宣告式或未經同意的更新。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可提供彈性，此模式中，因為您可以在設計階段之後管理訂用帳戶和合作對象。  
  
-   要求-回應模式  
  
     來自特定實體的特定要求回應訊息中產生 interrogative 或查詢訊息交換。  
  
## <a name="xml-validation"></a>XML 驗證  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]XML 訊息會提供 2.下列驗證：  
  
-   XML 讀取器  
  
-   圖解  
  
     您可以啟用或停用圖解驗證合作對象。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]由 MSH9.3 訊息結構標頭欄位和 MSH12 版本識別碼欄位 （2.3.1、 2.4，2.5） 會使用這項處理，直接對 HL7 2.XML 結構描述。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]使用標準的 XML 處理功能，在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
-   Z 區段  
  
     [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會驗證沒有宣告的區段會包含未宣告的 Z 區段中。  
  
## <a name="ack-generation"></a>通知的產生  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2.XML 訊息支援下列類型的通知 (Ack)。 HL7 錯誤類型和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可用 （替代） 的錯誤類型：  
  
-   HL7 原始 Ack  
  
-   HL7 增強 Ack  
  
     認可接受和應用程式接受  
  
## <a name="see-also"></a>另請參閱  
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.XML 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)