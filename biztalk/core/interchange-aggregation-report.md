---
title: 交換彙總報告 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4619e8d0-9e9e-4d19-a67a-ac1058a0579b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ac86a43bc74d862aa856a18f1564b03bc7f4e89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257878"
---
# <a name="interchange-aggregation-report"></a>交換彙總報告
此報告可提供一份記錄，指出共用相同 EDI 編碼類型、傳送者合作對象、接收者合作對象以及方向的 EDI 交換數目。 此報告不提供個別交換的詳細資料。  
  
 此狀態報告中的 [群組中樞] 頁面底部的 [交換彙總報告] 連結，即可顯示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="fields-in-the-status-report"></a>狀態報告中的欄位  
 交換彙總報告會顯示每份記錄的下列資訊：  
  
-   有多少交換共用相同 EDI 編碼類型、傳送者合作對象、接收者合作對象以及方向的統計數目  
  
-   記錄中每個交換的傳送者合作對象  
  
-   記錄中每個交換的接收者合作對象  
  
-   記錄中每個交換的方向 (接收或傳送)  
  
-   在傳送或接收的時間範圍內，最早交換的日期和時間 (最早開始日期/時間)  
  
    > [!NOTE]
    >  接收文件，如果交換中所指定的日期是 YYMMDD 格式和 YY 是大於或等於 75，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將年份顯示 19YY。 如果日期為少於 75 台，它會顯示為 20YY。  
    >   
    >  比方說，如果您收到的交換包含值 991113 中 ISA09，最早啟動日期/時間會列出為 11/13/1999年報表中。  
  
-   在傳送或接收的時間範圍內，最晚交換的日期和時間 (最新結束日期/時間)  
  
-   記錄中每個交換的 EDI 編碼類型  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a>狀態報告之查詢運算式中的欄位  
 您可以自訂 [交換彙總報告]，只要變更會決定所顯示資料之查詢運算式中的欄位即可。 可用的欄位如下：  
  
|||||  
|-|-|-|-|  
|查詢運算式欄位|可能的運算子|可能的值|預設已包含？|  
|搜尋|等於|交換彙總報告|是 (必要)|  
|交換日期時間|小於或等於<br /><br /> 大於或等於|特定日期時間<br /><br /> 今天<br /><br /> 今日 - 1|是<br /><br /> 附註： 可以包含在查詢運算式中，一次使用小於兩次-運算子，另一次加入大於位運算子，以便提供範圍。|  
|相符記錄上限|等於|整數 (預設為 50)|是|  
|方向|等於|全部 (預設)<br /><br /> Receive<br /><br /> Send|否|  
|接收者合作對象名稱|等於|全部 (預設)<br /><br /> 特定合作對象名稱 (AN 字串)|否|  
|傳送者合作對象名稱|等於|全部 (預設)<br /><br /> 特定合作對象名稱 (AN 字串)|否|  
|狀態|等於<br /><br /> 不等於|已接受<br /><br /> 已接受，發生錯誤<br /><br /> 已傳送<br /><br /> 全部<br /><br /> 預期通知<br /><br /> 未預期通知<br /><br /> 已拒絕|否|