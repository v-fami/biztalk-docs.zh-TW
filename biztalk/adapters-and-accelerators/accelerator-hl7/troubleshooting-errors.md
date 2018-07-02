---
title: 針對錯誤進行疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors, troubleshooting
- troubleshooting, errors
ms.assetid: 08cc95a3-4be9-450f-a015-e031011158f7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f5af933f83f292bfae3f92f70d2c247274c159c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976855"
---
# <a name="troubleshooting-errors"></a>針對錯誤進行疑難排解
本節說明的相關問題[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]產生錯誤。  
  
## <a name="the-mllp-adapter-can-run-only-on-a-single-host-instance"></a>MLLP 配接器可以只在單一主機執行個體上執行  
  
### <a name="symptom"></a>徵兆  
 您無法啟用傳輸類型為 MLLP 的接收位置和不同的接收處理常式比另一個現有的接收位置。 此外，您不能登錄並啟動傳送埠使用不同的傳送處理常式，比另一個現有的傳送埠。  
  
**可能的原因**： 您只能使用一個 MLLP 接收 （或傳送） 在單一伺服器上的處理常式。 此外，URI 指定的接收位置 （或傳送埠） （MLLP 傳輸屬性中的主機名稱） 必須是"localhost"，或執行所在的主控件執行個體接收 （或傳送） 配接器處理常式的伺服器名稱。  
  
**解析**： 指定在單一伺服器上相同的接收 （或傳送） 處理常式的所有 MLLP 接收位置 （或傳送埠）。  
  
## <a name="msh-and-ack-schemas-must-be-added-to-only-one-project"></a>MSH 和通知結構描述必須新增至只有一個專案  
  
### <a name="symptom"></a>徵兆  
 當您嘗試建置專案時，您會收到下列錯誤其中一項：  
  
`Error: Cannot locate document specification as multiple schemas match the message type "http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF"`
  
`Schema http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF not found`
  
**可能的原因**: MSH 和通知結構描述 （MSH_25_GLO_DEF.xsd 和 ACK_24_GLO_DEF.xsd） 已部署在多個專案。  
  
**解析**： 確定 MSH_25_GLO_DEF.xsd 和 ACK_24_GLO_DEF.xsd 有已新增至只有一個專案。  
  
## <a name="exception-of-type-systemoutofmemoryexception-has-thrown-an-error-in-the-event-log"></a>型別的 System.OutOfMemoryException 已擲回例外狀況錯誤事件記錄檔中  
  
### <a name="symptom"></a>徵兆  
 事件記錄檔中，您就會收到下列或類似的錯誤：  
  
`Exception of type System.OutOfMemoryException has thrown an error.`
  
**可能的原因**： 一些處理大量訊息時[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]引擎元件可能會出現記憶體流失。  
  
**解析度**： 重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
## <a name="header-serialization-generates-an-error-in-the-event-viewer"></a>標頭序列化會產生事件檢視器中的錯誤  
  
### <a name="symptom"></a>徵兆  
 即使 「 狀況與活動追蹤 (HAT) 工具中的訊息表示成功，您可以取得事件記錄檔中的下列或類似的錯誤：  
  
`An error happened in the header during serialization.`
  
**可能的原因**： 訊息標頭轉換值未正確設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。  
  
**解析度**： 確認 MSH 對應中的值[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。  
  
## <a name="duplicate-event-id-4133-serializer-errors-are-logged"></a>重複的事件識別碼 4133 序列化程式錯誤記錄  
  
### <a name="symptom"></a>徵兆  
 事件識別碼 4133 – 「 錯誤發生在序列化期間標頭中 」 就會發生兩次的每個 MSH11 值不是有效的訊息執行個體。  
  
**可能的原因**： 沒有事件記錄檔中的重複錯誤處理 （認可和應用程式通知） 的兩個通知時發生錯誤。 相反地，您會收到一個事件識別碼 4133 的兩個通知的每個。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 它會產生每個通知建立記錄項目。  
  
**解析**： 請確定您的訊息已正確格式化，並填入 MSH11 欄位。  
  
## <a name="send-pipeline-generates-an-error-when-using-the-2-way-mllp-adapter"></a>傳送管線會使用 2 向處理 MLLP 配接器時，會產生錯誤  
  
### <a name="symptom"></a>徵兆  
 事件記錄檔中，您就會收到下列或類似的錯誤：  
  
`There was a failure executing the send pipeline: "[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XPipelines.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XSendPipeline" Source: "Microsoft.Solutions.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fAsm" Send Port: "<*host name: port number*>" Reason: Message does not contain a part with name MSHSegment.`
  
**可能的原因**： 接收的應用程式不回應通知並[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]預期從接收的應用程式的回應。  
  
**解析**： 這是根據設計，因此您可以忽略的錯誤訊息。  
  
## <a name="see-also"></a>另請參閱  
 [HL7 的疑難排解和已知問題](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)