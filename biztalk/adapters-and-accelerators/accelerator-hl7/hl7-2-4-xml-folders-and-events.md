---
title: "HL7 2.4 XML 資料夾和事件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events, HL7 2.XML versions
- HL7, default sub-folders
- HL7, events
ms.assetid: bc6c5d75-66c7-4269-bfb9-59cab5999a73
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10c9445a1d5c7978b526fd0347dc6defa3214640
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-24-xml-folders-and-events"></a>HL7 2.4 XML 資料夾和事件
下表列出安裝精靈的 XML 編碼訊息的 HL7 2.4 版資料夾內所建立的子資料夾。 這些子資料夾包含使用的結構描述[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 來驗證、 剖析和序列化此資料表的事件資料行中列出的事件。 子資料夾名稱會描述這些結構描述支援的事件類型。  
  
|子資料夾|事件|  
|----------------|------------|  
|病患的系統管理|A01 A62、 K21、 K22、 K23、 K24、 Q21 Q24|  
|訂單項目|O01 O22、 Q06、 Q26 Q30、 RAR、 RDR、 RER、 RGR、 ROR、 V01 V04、 Z73、 Z74|  
|查詢|J01、 J02、 K11、 K13、 K15、 Q01 Q05、 Q07 Q09、 Q11、 Q13、 Q15 Q17、 R07 R09、 Z75 Z99|  
|財務管理|P01 ~ P06、 P10|  
|觀察報告|C01 C12、 P07、 P08、 P09、 R01、 R02、 R04、 R21、 W01、 W02|  
|主版檔案|M01 M12 MFA|  
|醫療的記錄資訊管理|T01 T12|  
|排程|S01 S26|  
|病患的轉介|I01 I15|  
|病患照護|PC1-PCJ，PCK，PCL PCH|  
|臨床實驗室自動化|U01 U13|  
|應用程式管理|N01 N02|  
|人員管理|B01 B06，K25，Q25|  
  
## <a name="see-also"></a>另請參閱  
 [使用 HL7 2.XML 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)