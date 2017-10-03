---
title: "HIPAA 文件結構描述版本 5010 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62e50964-66e1-4ed9-a1a1-68556b13b024
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24d1528d5c35c15e777ce1540d42ea4b7066cea2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hipaa-document-schema-version-5010"></a>HIPAA 文件結構描述版本 5010
U.S.部門的健全狀況及公共服務部 (HHS) 宣布於 2009 年 1 月 16 日的最終規則目前的 HIPAA 4010A1 版取代為 5010 版。 版本 5010 HIPAA 標準包括增強結構最上層主題、 技術、 功能和資料內容。 這些改進將減少，並消除資料中的模稜兩可，也處理一些先前業的商務需求時。 [!INCLUDE[prague](../includes/prague-md.md)]提供支援 HIPAA 5010 版。  
  
> [!NOTE]
>  [!INCLUDE[prague](../includes/prague-md.md)] 仍支援 HIPAA 4010A1 版。  
  
## <a name="hipaa-5010-version-support"></a>HIPAA 5010 版支援  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 引進下列變更以支援 HIPAA 5010：  
  
-   **新的取代結構描述**: HIPAA 5010 透過舊版 4010A1 版引進下列新的取代結構描述的版本。 EDI 結構描述已壓縮，並在可執行檔，傳遞[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\MicrosoftEdiXSDTemplates.exe。 在執行時，MicrosoftEdiXSDTemplates.exe 會將 HIPAA 5010 結構描述存入[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\HIPAA\5010 資料夾。  
  
    |GS08/ST03|交易集識別碼 (ST01)|Description|  
    |----------------|----------------------|-----------------|  
    |005010X279|270|資格、涵蓋範圍或利益查詢 - 要求|  
    |005010X279|271|投保資格、保險範圍或或保險金資訊 - 要求|  
    |005010X212|276|健康照護主張狀態 - 要求|  
    |005010X212|277|健康照護主張狀態 - 回應|  
    |005010X217|278|醫療保健服務檢視 – 要求與回應|  
    |005010X218|820|薪資扣除額|  
    |005010X220|834|醫療保健給付的登記與管理|  
    |005010X221|835|健康照護理賠金|  
    |005010X222|837|健康照護理賠 - 專業化|  
    |005010X223A1|837|健康照護理賠 - 制度化|  
    |005010X224A1|837|健康照護理賠 - 牙科|  
  
-   **支援 ST03 欄位**: 5010 版會強制所有交易的 ST03 存在設定而不是 835 (醫療保健宣告強制使用 st03。 ST03 是用來識別交易集版本。 ST03 允許在單一群組中使用不同的交易集版本。 ST03 在識別交易集版本方面的優先性高於 GS08。 您可以在 EDI 屬性結構描述命名空間以內容屬性的形式撰寫和升級 ST03，並依據 ST03 路由訊息。  
  
-   **群組內的類似交易集的支援**: X12 標準提供交易集和群組，稱為 st01-gs01 對應之間的對應。 此對應是用來驗證可合併於單一群組 (GS-GE) 中的類似交易集。 對於 HIPAA，這表示「職業」、「機構」與「牙科」的 837 索賠現在可以合併於單一群組中。  
  
-   **支援 icd-10**： 電子交易代碼集用來傳輸醫療保健資料。 5010 版支援使用舊版 4010A1 未支援的國際疾病分類 (ICD-10) 代碼集。 ICD-10 是用來識別索賠申請的各種診斷與程序、相關交易與臨床報告。 使用 ICD-10 的好處是可擁有更正確的病患服務、診斷與治療資訊資料，以及更全面的檢測數據報告。  
  
-   **5010 997 中的新欄位**: 997 功能通知結構描述所提供的--預設由[!INCLUDE[prague](../includes/prague-md.md)]導入三個新的選擇性欄位也就是 AK103、 AK203 與 AK41.3。 將 EDI 引擎都可以處理的內送 5010 997 訊息，包含這些欄位，但不是會產生外寄 997 通知根據新的結構描述。  
  
 HIPAA 4010A1 結構描述有一個已知問題，就是不會檢查 X12_R 資料類型元素的長度上限與下限。 [!INCLUDE[prague](../includes/prague-md.md)] 已修正此問題，HIPAA 5010 結構描述會驗證 X12_R 資料類型元素的長度上限與下限。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 中的 HIPAA 支援](../core/hipaa-support-in-biztalk-server.md)   
 [分割 HIPAA 子文件](../core/splitting-hipaa-subdocuments.md)