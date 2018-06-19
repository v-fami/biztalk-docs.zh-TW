---
title: EDIFACT CONTRL 訊息為技術通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f2a7564-dbd3-48d0-b0a6-a77a0560459f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8376e3249a102486c1bef4d92a7512c8aa29636c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242510"
---
# <a name="edifact-contrl-message-as-technical-acknowledgment"></a>EDIFACT CONTRL 訊息為技術通知
如果您選取要產生技術通知，在商務設定檔的設定或交易夥伴協議 （或後援協議，如果未定義協議是兩個商務設定檔之間），或如果設定為"2"，CONTRL 訊息中的 UNB9 欄位訊息將會產生為技術通知。 這個通知 (ACK) 會報告接收交換時的結果。  
  
 CONTRL 技術通知 (ACK) 包括下列區段：  
  
-   UNH 訊息標頭 (必要項)  
  
-   UCI 交換回應，可確認主旨交換並表示交換接收的性質 (必要項)。 UCI 區段的最多出現次數為 1；因此，它會針對其中控制區段中所遇到的第一個錯誤進行報告。  
  
-   UNT 訊息結尾 (必要項)。  
  
 系統會以資料元素 UCI5 的「語法錯誤代碼」來報告錯誤。 EDIFACT 編碼交換不會出現像 X12 編碼交換所出現的「已接受，發生錯誤」狀況。  
  
> [!NOTE]
>  CONTRL 回條 (EDIFACT 技術通知) 只會在內送 EDIFACT 訊息發生重複或是信封中發生錯誤 (例如，字元集發生問題) 時報告「已拒絕」狀態。 不同於 X12 在 TA1 通知中 TA104 欄位，EDIFACT 不會在 CONTRL 技術通知中報告「交換已接受，發生錯誤」狀態。 若已接受部分 EDIFACT 訊息，CONTRL 技術通知將會報告「已接受」。 在一些情況下，部分訊息雖然將遭到拒絕，但是 CONTRL 通知仍會報告「已接受」狀態。 在這種情況下，UCI5 元素可能會報告此等錯誤。  
  
 CONTRL 技術通知 (ACK) 包括下列資料元素：  
  
|Data 元素|名稱|使用方式|  
|------------------|----------|-----------|  
|UNH1|訊息參考編號|-|  
|UNH2|訊息識別碼子元件|這些子元件包括：<br /><br /> -1 = CONTRL<br /><br /> - 2 = 4<br /><br /> - 3 = 1<br /><br /> -4 = 取消|  
|UCI1|交換控制編號|自所接收訊息的 UNB5 欄位進行對應。|  
|UCI2|交換傳送者|自所接收訊息的 UNB2 欄位進行對應。 第一個子元件 (識別) 為必要項。 第二個子元件 (辨識符號) 和第三個元件 (反向路由位址) 為選擇性項目。|  
|UCI3|交換收件者|自所接收訊息的 UNB3 欄位進行對應。 第一個子元件 (識別) 為必要項。 第二個子元件 (辨識符號) 為選擇性項目。|  
|UCI4|動作代碼|這些動作代碼包括：<br /><br /> -8 如果交換已接受<br /><br /> -7，當交換已接受，但某些交易集將會拒絕<br /><br /> -4，當交換因 UNA 或 UNB 區段錯誤而拒絕<br /><br /> 這是必要的資料元素。|  
|UCI5|語法錯誤代碼|確認錯誤狀況 (如果有的話)。 如需詳細資訊，請參閱[EDIFACT CONTRL 通知錯誤碼](../core/edifact-contrl-acknowledgment-error-codes.md)。<br /><br /> 這個資料元素具有條件式選用性。|  
|UCI6|服務區段標記|識別具有 UCI5 資料元素中已指出之錯誤狀況的區段。<br /><br /> 這個資料元素具有條件式選用性。|  
|UCI7|資料元素識別碼|識別具有 UCI5 資料元素中已指出之錯誤狀況的資料元素。 UCI7 的子元件包括：<br /><br /> -錯誤資料元素區段中的位置 （必要項）<br /><br /> -錯誤元件資料元素區段中的位置 （條件式選用性）<br /><br /> -錯誤資料元素區段 （條件式選用性） 中的項目|  
|UCI8|-|-|  
|UNT1|區段計數|-|  
|UNT2|訊息參考編號|-|