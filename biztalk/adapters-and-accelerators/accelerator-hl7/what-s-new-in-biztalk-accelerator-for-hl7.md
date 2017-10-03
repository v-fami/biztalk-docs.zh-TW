---
title: "什麼 &#39; s 的新 BizTalk Accelerator for HL7 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new
- BizTalk Accelerator for HL7, what's new
- getting started, what's new
ms.assetid: e98595a1-2d1e-488e-8a97-7cd561948b3b
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c350ef616acf61cab7910c5381cca02d68c919f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what39s-new-in-biztalk-accelerator-for-hl7"></a>什麼 &#39; s 的新 BizTalk Accelerator for HL7
變更與更新與[!INCLUDE[HL7_CurrentVersion_FirstRef_md](../../includes/hl7-currentversion-firstref-md.md)]。 

## <a name="biztalk-server-2016"></a>BizTalk Server 2016

|功能|Description|  
|---|---| 
| **啟動連線到 LOB** | 使用 MLLP 配接器，[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]可以啟動或起始遠端的企業營運 (LOB) 的伺服器系統的連線。 LOB 等候連接，然後再將傳送訊息至[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]使用 MLLP 配接器。 有一些 MLLP 中的新屬性的接收位置設定此選項。 請參閱： <br/><ul><li>[端對端教學課程中的步驟 4](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md)</li><li>[步驟 4 中 interrogative 教學課程](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md)</li><li>[Interrogative 教學課程中的步驟 5](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)</li><li>[在批次的教學課程步驟 4](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md)</li></ul>在[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]較舊版本中，HL7 MLLP 的接收配接器等候遠端 LOB 伺服器連線到 MLLP 配接器和 LOB 然後傳送訊息。 <br/><br/>請參閱[BTAHL7 將訊息路由](../../adapters-and-accelerators/accelerator-hl7/how-btahl7-routes-messages.md)如需詳細資訊。|

## <a name="biztalk-server-2013-r2"></a>BizTalk Server 2013 R2  
  
|功能|Description|  
|-------------|-----------------|  
|**64 位元支援**|MLLP 配接器與 HL7 管線可以在執行這兩個 32 位元和 64 位元的主控件執行個體。<br /><br /> [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]安裝包括 32 位元安裝封裝和 64 位元安裝封裝。 在 32 位元的電腦上，請只安裝 32 位元封裝。 在 64 位元電腦上安裝 32 位元**或**64 位元封裝。 <br/><br/>**重要事項：**若要使用 64 位元支援，請僅安裝 64 位元封裝。 64 位元封裝可讓配接器和管線在 32 位元和 64 位元模式中都能執行。|  
|**v2.6 結構描述支援**|支援包括：<br /><br /> -   **BTAHL7V26Common**專案： v2.6 結構描述。<br />-   **BTAHL7Common**專案： 包含 v2.6 結構描述和 ACK_26_GLO_DEF 通知結構描述則會產生 v2.6 訊息通知。<br />-   **MSH_25_GLO_DEF**結構描述： 處理新訊息標頭欄位，隨附於 v2.6 結構描述，並且會繼續支援所有 v2。*x*結構描述。|  
|**動態 MLLP 配接器支援**|屬性可以設定在執行階段使用單向或雙向 （要求-回應） 的配接器傳送埠。 請參閱[動態 MLLP 配接器](../../adapters-and-accelerators/accelerator-hl7/dynamic-mllp-adapter.md)。|  
|**「 FreeText 」 支援**|如果欄位或區段定義為 「 FreeText"，無法剖析欄位/區段中的字元資料。 請參閱[編碼的字元，使用任意文字](../../adapters-and-accelerators/accelerator-hl7/encoding-characters-using-free-text.md)。|  
|**具有無效的 MSH 郵件會傳送 ACK 或 NACK**|使用**ReturnErrorForInvalidMSH3**登錄機碼，負認可 (NACK) 會傳送至合作對象如果發生下列情況：<br /><br /> -無效的 MSH3 （合作對象中未定義 HL7 組態總管） <br />    **AND**<br />-MSH15 和 MSH16 訊息中的值是 null 或空白<br /><br /> 若要傳送 NACK，下列的登錄機碼設為 1，然後重新啟動主控件執行個體：<br /><br /> 32 位元主控件：`HKLM\SOFTWARE\Microsoft\BizTalk Accelerator for HL7`<br /><br /> 64 位元主控件：`HKLM\ SOFTWARE\Wow6432Node\Microsoft\BizTalk Accelerator for HL7` <br/><br/>**提示：**連接埠可以訂閱失敗訊息： <ul><li>使用**BTAHL7Schemas.ParseError = True**篩選條件。</li><li>使用**Pass Through**管線。</li></ul>|  
|**ACK 訊息執行個體保持作用中**|如果沒有連接到上游系統失敗，傳送到上游系統通知 (ACK) 會維持在作用中狀態。<br /><br /> 新的行為： 如果沒有連接到上游系統失敗，則通知會擱置訊息。|  
|**不要傳送\<SB >**|這個屬性會新增至接收配接器連接埠組態屬性。 若要啟用此屬性，設定**UseMLLPTransACK**值：<br /><br /> -當設定為**False** （預設值），配接器傳送訊息如果資料是以開頭\<SB >。 例如，會傳送下列訊息：<br /> `<SB\>DataData<CR\>DataData<CR\>…`<br/><br />-當設定為**True**，配接器傳送訊息，如果資料遺漏\<SB > 一開始。 例如，會傳送下列訊息：<br /> `DataData<CR\>DataData<CR\>…` <br/><br/>**重要事項：**如果兩個方式傳送連接埠有**不要傳送\<SB >**設為 True，則不會傳送 SB 訊息至下游系統。 同時它可以與 SB 遺漏下游系統接收通知。|  
|**接受遺漏\<SB >**|這個屬性會加入至傳送配接器連接埠組態屬性。 若要啟用此屬性，設定**UseMLLPTransACK**值：<br /><br /> -當設定為**False** （預設值），配接器時傳回錯誤的資料已遺失\<SB > 一開始。 例如，下列訊息會傳回錯誤：<br /> `DataData<CR\>DataData<CR\>…`<br/><br />-當設定為**True**，配接器可以接收訊息，如果資料遺漏\<SB > 一開始。 例如，收到下列訊息：<br /> `<SB\>DataData<CR\>DataData<CR\>…` <br />`DataData<CR\>DataData<CR\>…` <br/><br/>**重要事項：**雙向接收埠是否**接受遺漏\<SB >**設為 True，則它會接受來自上游系統訊息中的遺失 SB。 同時它不會傳送 SB 上游的系統。|  
  
## <a name="biztalk-server-2013"></a>BizTalk Server 2013  
  
 之前的版本中包含下列增強功能：  
  
-   可復原交換支援 HL7 管線中批次中的批次出實例。  
  
 在舊版中，已移除下列功能：  
  
-   健全狀況的活動追蹤功能會從 BizTalk Server 移除因此從 BTAHL7 移除稽核功能，但記錄會維持不變。  
  
 在先前的版本修改下列功能：  
  
-   「 稽核和記錄服務 」 已重新命名為 「 HL7 記錄服務 」。  

## <a name="see-also"></a>另請參閱

[什麼是 BizTalk Server 2016 的新功能](../../install-and-config-guides/what-s-new-in-biztalk-server-2016.md)  
[BizTalk Server 2013 R2 和 2013年中最新消息](../../install-and-config-guides/what-s-new-in-biztalk-server-2013-and-2013-r2.md)