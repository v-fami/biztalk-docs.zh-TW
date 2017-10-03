---
title: "疑難排解錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, troubleshooting
- troubleshooting, errors
ms.assetid: 08cc95a3-4be9-450f-a015-e031011158f7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae7ad99b699da29d4d8680375f88e4d4a74ff66a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-errors"></a>疑難排解錯誤
本節說明的相關問題[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]產生錯誤。  
  
## <a name="the-mllp-adapter-can-run-only-on-a-single-host-instance"></a>MLLP 配接器可以只在單一主控件執行個體上執行  
  
### <a name="symptom"></a>徵兆  
 您無法啟用與傳輸類型為 MLLP 的接收位置和不同的接收處理常式比另一個現有的接收位置。 此外，您無法登錄並啟動傳送埠使用不同的傳送處理常式，比另一個現有的傳送埠。  
  
**可能的原因**： 您只能使用一個 MLLP 接收 （或傳送） 在單一伺服器上的處理常式。 此外，URI 指定的接收位置 （或傳送埠） （MLLP 傳輸屬性中的主機名稱） 必須是"localhost"或伺服器名稱，其中的主控件執行個體就會接收 （或傳送） 配接器處理常式正在執行。  
  
**解析**： 單一伺服器上的所有 MLLP 的接收位置 （或傳送埠） 指定相同的接收 （或傳送） 處理常式。  
  
## <a name="msh-and-ack-schemas-must-be-added-to-only-one-project"></a>MSH 和通知結構描述必須加入至只有一個專案  
  
### <a name="symptom"></a>徵兆  
 當您嘗試建置專案時，會取得其中一種下列錯誤：  
  
`Error: Cannot locate document specification as multiple schemas match the message type "http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF"`
  
`Schema http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF not found`
  
**可能的原因**: MSH 和通知結構描述 （MSH_25_GLO_DEF.xsd 和 ACK_24_GLO_DEF.xsd） 已部署多個專案中。  
  
**解析**： 請確認 MSH_25_GLO_DEF.xsd 和 ACK_24_GLO_DEF.xsd 有已新增至只有一個專案。  
  
## <a name="exception-of-type-systemoutofmemoryexception-has-thrown-an-error-in-the-event-log"></a>型別 System.OutOfMemoryException 已擲回例外狀況錯誤事件記錄檔中  
  
### <a name="symptom"></a>徵兆  
 您可以取得下列或類似的錯誤事件記錄檔中：  
  
`Exception of type System.OutOfMemoryException has thrown an error.`
  
**可能的原因**： 處理大量訊息，有些時[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]引擎元件可能會出現記憶體流失。  
  
**解析**： 重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
## <a name="header-serialization-generates-an-error-in-the-event-viewer"></a>標頭序列化事件檢視器中會產生錯誤  
  
### <a name="symptom"></a>徵兆  
 即使 「 狀況與活動追蹤 (HAT) 工具中的訊息表示成功，您可以取得事件記錄檔中的下列或類似的錯誤：  
  
`An error happened in the header during serialization.`
  
**可能的原因**： 訊息標頭轉換值未正確設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。  
  
**解析**： 確認 MSH 對應中的值[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。  
  
## <a name="duplicate-event-id-4133-serializer-errors-are-logged"></a>重複的事件識別碼 4133 序列化程式錯誤記錄  
  
### <a name="symptom"></a>徵兆  
 事件識別碼 4133 – 」 錯誤是發生在標頭在序列化期間 」 就會發生兩次的訊息 MSH11 值不是有效的每個執行個體。  
  
**可能的原因**： 沒有事件記錄檔中的重複錯誤處理兩個通知 （認可和應用程式通知） 時發生錯誤。 相反地，您會收到一個事件識別碼 4133 每兩個認可。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]它會產生每個通知建立記錄項目。  
  
**解析**： 請確定您的郵件擁有正確格式化，並填入 MSH11 欄位。  
  
## <a name="send-pipeline-generates-an-error-when-using-the-2-way-mllp-adapter"></a>傳送管線會使用 2 方式 MLLP 配接器時，會產生錯誤  
  
### <a name="symptom"></a>徵兆  
 您可以取得下列或類似的錯誤事件記錄檔中：  
  
`There was a failure executing the send pipeline: "[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XPipelines.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XSendPipeline" Source: "[!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fAsm" Send Port: "<*host name: port number*>" Reason: Message does not contain a part with name MSHSegment.`
  
**可能的原因**： 接收的應用程式未使用通知來回應和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]預期從接收的應用程式的回應。  
  
**解析**： 這是根據設計，而且您可以忽略的錯誤訊息。  
  
## <a name="see-also"></a>另請參閱  
 [HL7 中的疑難排解和已知問題](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)