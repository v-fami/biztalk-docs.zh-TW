---
title: 區段和欄位 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, segments
- messages, fields
- segments, messages
ms.assetid: e68864e6-590c-47f3-8c9e-81831aec2642
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca948748bc30f8c8a56f7c257b775b37a990625
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206478"
---
# <a name="segment-and-field"></a>區段和欄位
區段資料表定義 HL7 區段。 每個區段定義遵循如下所示的模式。  
  
|SEQ|LEN|DT|選擇加入|RP / #|TBL #|項目 #|項目名稱|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|1|4|SI|O|||00104|設定識別碼-PID|  
|2|20|/CX|B|||00105|病患識別碼|  
|3|250|/CX|R|Y||00106|病患識別碼清單|  
|4|20|/CX|B|Y||00107|替代病患識別碼-PID|  
|5|250|XPN|R|Y||00108|病患的名稱|  
|..||||||||  
|..||||||||  
|37|80|ST|O|||01541|疲勞|  
|38|250|CE|O|2|0429|01542|生產類別程式碼|  
  
 HL7 也包含每個欄位的文字定義。 三個字元區段標記與序號可唯一識別每個區段內的欄位。 比方說，如果病患識別區段中，標記 PID 和序號"5"唯一識別病患名稱欄位。 XML 編碼方式和介面文件的同時會使用此慣例來識別區段中的欄位。 區段定義也包含每個欄位，以及適用於自動程式碼項目資料表數目的資料型別宣告。  
  
 在新的版本中，您只可以加入欄位結尾的區段，而且您無法移除欄位。 如果加入的欄位來取代現有欄位的功能，則回溯相容性資料會保留第一個欄位。 (這可以看到"B"中 （選擇性） 和資料行上方 PID.2 PID.3。)  
  
 下列函式的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]支援標準 HL7 版本從 V2.1 區段上。  
  
-   當您建構介面規格，並實作介面時，您可以標籤是選擇性的標準為強制性或不受支援，根據功能需求的欄位。  
  
-   您可以建立 Z 區段在需要時進行當地語系化。  
  
-   您可以重新定義欄位的語意，或將欄位加入至片段所需進行當地語系化。 請注意這個落在不合法的當地語系化標題之下。 不過，在某些情況下您需要這項功能以支援舊版的介面或舊版系統的介面。  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)