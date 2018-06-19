---
title: 疑難排解通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, troubleshooting
- troubleshooting, acknowledgements
ms.assetid: faed356e-f5fc-4920-a9f9-82eca0ad7d67
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecbbb22498cfd3d451c0b8c75c8e6f4502c2364d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207030"
---
# <a name="troubleshooting-acknowledgments"></a>疑難排解通知
解決相關問題[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通知。  
  
## <a name="acknowledgments-are-not-generated"></a>不會產生通知  
 有幾個可能的原因，通知 (Ack) 未產生或接收。 檢閱以下清單中的潛在問題。  
  
### <a name="symptom"></a>徵兆  
 當您更新中的合作對象資訊時，不會產生通知[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管來產生通知。  
  
**可能的原因**:[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會快取和重新整理合作對象組態資訊每隔 15 分鐘。  
  
**解析**： 等待至少 15 分鐘的時間讓快取重新整理或重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]變更立即生效。  
  
### <a name="symptom"></a>徵兆  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]未產生通知，而且事件錯誤會出現在事件記錄檔。  
  
**可能的原因**： 無法產生通知，當批次中 / 出訊息的批次包含空白 FHS11 欄位。  
  
**解析**： 請確定您的郵件擁有正確格式化，並填入 FHS11 欄位。  
  
### <a name="symptom"></a>徵兆  
 您的應用程式無法產生或收到通知。  
  
**可能的原因**: MSH3 欄位中的訊息不正確的資訊可避免[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]從傳送訊息的通知。  
  
**解析**： 請確定您的郵件擁有正確格式化，並填入 MSH3 欄位。  
  
## <a name="acknowledgments-are-suspended-or-not-routed-to-the-send-party"></a>通知會暫停，或者不會路由至傳送合作對象  
  
### <a name="symptom"></a>徵兆  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將訊息傳送至雙向配接器中，而不會產生通知。  
  
**可能的原因**： 訊息訂用帳戶未正確設定。  
  
**解析**： 確定訊息訂閱已存在且設定正確。  
  
## <a name="suspended-acknowledgments"></a>暫止的通知  
  
### <a name="symptom"></a>徵兆  
 通知會出現錯誤訊息"欄位中找到的 Delimiter"暫停時，您已設定合作對象具有編碼字元，例如其中包含分隔符號字元@-！ $。  
  
**可能的原因**： 訊息包含例如句點 （.） 或連字號 （-） 字元。 產生 Ack 時[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]包含"。"和"-"時間戳記值。  
  
**解析**： 停用驗證，若要避免這些錯誤的傳送管線中。  
  
## <a name="biztalk-server-generates-an-error-about-missing-ack-when-using-2-way-mllp-adapter"></a>BizTalk Server 會產生有關遺漏 ACK，使用 2 方式 MLLP 配接器時錯誤  
  
### <a name="symptom"></a>徵兆  
 您可以取得下列或類似的錯誤事件記錄檔中：  
  
 「 無法從網路，因為發生錯誤接收通知 」 來自 HRESULT 的例外狀況： 0xC0C01662""  
  
**可能的原因**： 您正在使用 1 方式接收和 2 單向傳送埠，因此 BizTalk 沒有對應的接收埠，以傳回 2 單向傳送埠從接收的訊息。  
  
**解析**： 這是根據設計，而且您可以忽略的錯誤訊息。  
  
## <a name="see-also"></a>另請參閱  
[HL7 中的疑難排解和已知問題](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)