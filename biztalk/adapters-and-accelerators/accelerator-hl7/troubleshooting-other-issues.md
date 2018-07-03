---
title: 針對其他問題進行疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting
ms.assetid: 1f115f64-45ce-445d-ab18-092f4a6a232c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2753d85050506d5b8ca05ca3b3438bb767a26322
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009495"
---
# <a name="troubleshooting-other-issues"></a>針對其他問題進行疑難排解
解決 Microsoft 的相關其他問題[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]。  
  
## <a name="message-rejected-by-the-btahl7-engine"></a>BTAHL7 引擎所拒絕的訊息  
  
### <a name="symptom"></a>徵兆  
 傳訊引擎會隨機拒絕訊息。  
  
**可能的原因**： 根據 HL7 標準，列舉值資料表 0338年包含 「 L （& I） 」 值。 欄位 6 PRA 區段可能包含此值。 因為[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會將"&"字元作為分隔符號，將會拒絕訊息。  
  
**解析**： 有三個可能的解決方案，此問題：  
  
1.  在訊息執行個體，會處理透過逸出序列，例如使用字元組合 L\T\I"&"字元。  
  
2.  在 PRA 6 新增 「 LI 」 列舉值，在結構描述和訊息執行個體中，改為使用此值。  
  
3.  在 MSH2; 中使用完全不同的子元件分隔符號不過，這個特定的解決方案可能無法實際取決於您的環境而定。  
  
## <a name="cannot-edit-the-hl7-schema-using-visual-studio"></a>無法編輯 HL7 結構描述使用 Visual Studio  
  
### <a name="symptom"></a>徵兆  
 無法編輯 HL7 結構描述使用 Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
**可能的原因**:[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]不支援某些 HL7 結構描述。  
  
**解析**： 使用 Microsoft 記事本之類的其他編輯器編輯 HL7 結構描述。  
  
## <a name="message-handling-fails-with-no-errors-logged"></a>訊息處理失敗，並記錄任何錯誤  
  
### <a name="symptom"></a>徵兆  
 系統會處理訊息，但不記錄錯誤訊息，或將訊息放入擱置的訊息佇列。  
  
**可能的原因**: **HeaderSpecType**並**DocumentSpecType**屬性值會區分大小寫。 當您部署您的管線時，在這些名稱中的印刷錯誤可能會導致 mishandled 和卸除與記錄任何錯誤訊息。  
  
**解析度**： 使用時，觀察是否區分大小寫**HeaderSpecType**並**DocumentSpecType**屬性值的名稱。  
  
## <a name="message-header-fields-are-not-validated-correctly"></a>訊息標頭欄位未正確驗證  
  
### <a name="symptom"></a>徵兆  
 標頭欄位的驗證失敗。  
  
 原因：[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式會驗證升級的屬性，而不實際的標頭欄位內容屬性。  
  
**可能的原因**： 對應至透過協調流程或對應的標頭升級屬性發生變更。  
  
**解析度**： 內容屬性的訊息標頭 MSH1、 MSH2 和 MSH5{1-3}需要更新，使其在同步處理的資料。  
  
## <a name="the-mllp-adapter-is-not-removed-during-uninstall"></a>解除安裝期間將不會移除 MLLP 配接器  
  
### <a name="symptom"></a>徵兆  
 在解除安裝 BTAHL7 期間，BTAHL7 安裝程式並未移除 MLLP 配接器。  
  
**可能的原因**： 時發生傳輸類型為 MLLP 的接收位置或傳送埠。 如果任何 BizTalk Server 專案正在參考它，BTAHL7 安裝程式無法移除 MLLP 配接器。  
  
**解析**： 解除安裝 BTAHL7 完成之後，執行下列動作：  
  
1.  在 BizTalk Server 管理主控台中，移除所有接收位置和傳送埠傳輸類型為 MLLP，或變更傳輸類型的接收位置或傳送埠新增至另一個型別。  
  
2.  在 [管理主控台] 中，刪除 MLLP 配接器。  
  
3.  重新啟動主控件執行個體。  
  
## <a name="btahl7-cannot-be-uninstalled-if-biztalk-server-has-already-been-uninstalled"></a>無法解除安裝 BTAHL7，如果已解除安裝 BizTalk Server  
  
### <a name="symptom"></a>徵兆  
 解除安裝[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]會導致下列錯誤：  
  
`A network error while attempting to read from file C:\Windows\Installer\Microsoft BizTalk <version\> Accelerator for HL7.msi`
  
**可能的原因**:[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]已解除安裝之前解除安裝[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]嘗試。 您必須先解除安裝[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]解除安裝之前[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。  
  
**解析度**： 重新安裝[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]，然後解除安裝[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]，然後再解除安裝[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。  
  
## <a name="messages-are-still-sent-after-the-applicable-mllp-send-port-has-been-stopped"></a>適用的 MLLP 傳送連接埠已停止後，仍會傳送訊息  
  
### <a name="symptom"></a>徵兆  
 之後您停止 MLLP 傳送連接埠、 傳送埠會透過傳送的訊息不會停止，但繼續傳送。  
  
**可能的原因**： 當您停止傳送埠時，連接會維持已建立藉由停止 BizTalk 主控件移除之前。 如此一來，訊息仍在之後停止傳送埠傳送。 這是因為 Biztalk Server 不會呼叫 MLLP 配接器在啟動或停止傳送埠的期間。 BizTalk Server 呼叫 MLLP 配接器只在開始和停止主機服務。  
  
**解析**： 您可以藉由停止您停止傳送埠的傳送處理常式的主控件執行個體中移除連線並停止傳輸的訊息。 不過，停止該主控件執行個體可能會影響其他不想停止的訊息。 如果您知道這是一種情況下，您應該設定傳送埠以不同的方式建立。 您應該建立另一個做為 只有這個 MLLP 傳送連接埠 （或傳送埠的子集） 的傳送處理常式的主控件執行個體。 您可以停止此主控件執行個體，然後停止來自此傳送埠的訊息傳輸。 這則不會影響其他使用其他的傳送處理常式的傳送埠上的其他訊息的傳輸。  
  
## <a name="see-also"></a>另請參閱  
 [HL7 的疑難排解和已知問題](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)