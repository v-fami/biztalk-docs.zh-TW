---
title: 在 SMTP 標頭使用巨集的限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], restrictions
- macros, SMTP headers [SMTP adapters]
- SMTP adapters, macros
- SMTP adapters, restrictions
- configuring [SMTP adapters], SMTP headers
- SMTP adapters, SMTP headers
- configuring [SMTP adapters], macros
- SMTP headers
ms.assetid: ceab0917-cb3c-423b-a15f-63747ab1d8da
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5162de289f9c9e7798e5a24aa75fa9305763b401
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977975"
---
# <a name="restrictions-on-using-macros-in-smtp-headers"></a>在 SMTP 標頭使用巨集的限制
您可以使用預先定義的一組巨集，在 SMTP 訊息標頭上動態形成 **主旨**、 **收件者**、 **寄件者**及 **副本** 屬性。 傳送訊息前，SMTP 傳送處理常式會將標頭中的所有巨集以巨集的值取代。 您可以使用數個不同的巨集來形成一個標頭。  
  
 若發生下列任何一種情況，SMTP 傳送處理常式便不會取代 **收件者**、 **寄件者**或 **副本** 標頭中的巨集：  
  
- 未設定對應的系統屬性。  
  
- 巨集拼錯。  
  
- 巨集的值包含 SMTP 標頭無效的符號。  
  
  如果符合下列任一條件，SMTP 傳送處理常式會保留巨集原樣，比方說， <strong>%sourceparty%@somedomain.com</strong> 或是**Message from %sourceparty%**。  
  
  下表列出您可用來建置 **收件者**、 **副本**及 **主旨** 等標頭的巨集。  
  
|巨集|描述|用於 [寄件者]|用於 [副本]|用於 [主旨]|  
|-----------|-----------------|---------------------|---------------------|--------------------------|  
|%MessageID%|BizTalk Server 中訊息的全域唯一識別碼 (GUID)。 這個值來自訊息內容屬性 **BTS.MessageID**。|否|否|是|  
|%datetime_bts2000%|UTC 日期時間的格式為 YYYYMMDDhhmmsss，其中 sss 表示秒與毫秒 (例如，199707121035234 表示 1997/07/12，10:35:23 與 400 毫秒)。|否|否|是|  
|%datetime%|UTC 日期時間格式為 YYYY-MM-DDThhmmss (例如，1997-07-12T103508)。|否|否|是|  
|%datetime.tz%|本地日期時間加上 GMT 的時區，格式為 YYYY-MM-DDThhmmssTZD (例如，1997-07-12T103508+800)。|否|否|是|  
|%time%|UTC 時間的格式為 hhmmss。|否|否|是|  
|%time.tz%|本地時間加上 GMT 的時區，格式為 hhmmssTZD (例如，124525+530)。|否|否|是|  
|%SourceParty%|FILE 配接器從中接收訊息的來源合作對象名稱。|否|否|是|  
|%SourcePartyQualifier%|FILE 配接器從中接收訊息的來源合作對象辨識符號。|否|否|是|  
|%DestinationParty%|目的地合作對象的名稱。 這個值來自訊息內容屬性 **BTS.DestinationParty**。|是|是|是|  
|%DestinationPartyQualifier%|目的地合作對象的辨識符號。 這個值來自訊息內容屬性 **BTS.DestinationPartyQualifier**。|否|否|是|  
  
## <a name="see-also"></a>另請參閱  
 [設定 SMTP 配接器的限制](../core/restrictions-when-configuring-the-smtp-adapter.md)