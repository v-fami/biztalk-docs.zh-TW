---
title: 交易集彙總報告 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6e1417e-e0c6-4d30-aab5-d9bfe14cd4b8
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 960fe64eb61504cb07b71be3e1870007b46c5fa9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279678"
---
# <a name="transaction-set-aggregation-report"></a>交易集彙總報告
此報告可提供一份記錄，顯示共用相同交易集識別碼、EDI 編碼類型、傳送者合作對象、接收者合作對象以及方向的 EDI 交易集數目。 此報告不提供個別交易集的詳細資料。  
  
 在 BizTalk Server 管理主控台的 [群組中樞] 頁面底部的 [交易集彙總報告] 連結，即可顯示此狀態報告。  
  
## <a name="fields-in-the-status-report"></a>狀態報告中的欄位  
 [交易集彙總報告] 會顯示下列已接收或已傳送之交換的資訊：  
  
-   有多少交易集共用相同的交易集識別碼、EDI 編碼類型、傳送者合作對象、接收者合作對象以及方向的計數  
  
-   記錄中每個交易集的傳送者合作對象  
  
-   記錄中每個交易集的接收者合作對象  
  
-   記錄中每個交易集的方向 (接收或傳送)  
  
-   在時間範圍內，最早傳送或接收之交易集的日期和時間 (最早開始日期/時間)  
  
    > [!NOTE]
    >  接收文件，如果交換中所指定的日期是 YYMMDD 格式和 YY 是大於或等於 75，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將年份顯示 19YY。 如果日期為少於 75 台，它會顯示為 20YY。  
    >   
    >  例如，如果您收到包含值 991113 中 isa09-交換時，最早開始日期/時間會列入報表中為 11/13/1999年。  
  
-   在時間範圍內，最晚傳送或接收之交易集的日期和時間 (最新結束日期/時間)  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a>狀態報告之查詢運算式中的欄位  
 您可以自訂 [交換彙總報告]，只要變更會決定所顯示資料之查詢運算式中的欄位即可。 可用的欄位如下：  
  
|||||  
|-|-|-|-|  
|查詢運算式欄位|可能的運算子|可能的值|預設已包含？|  
|搜尋|等於|交易集彙總報告|是 (必要)|  
|交換日期時間|小於或等於<br /><br /> 大於或等於|特定日期時間<br /><br /> 今天<br /><br /> 今日 - 1|是<br /><br /> 附註： 可以包含在查詢運算式中，一次使用小於兩次-運算子，另一次加入大於位運算子，以便提供範圍|  
|相符記錄上限|等於|整數 (預設為 50)|是|  
|方向|等於|全部 (預設)<br /><br /> Receive<br /><br /> Send|否|  
|接收者合作對象名稱|等於|全部 (預設)<br /><br /> 特定合作對象名稱 (AN 字串)|否|  
|傳送者合作對象名稱|等於|全部 (預設)<br /><br /> 特定合作對象名稱 (AN 字串)|否|  
|狀態|等於<br /><br /> 不等於|已接受<br /><br /> 已接受，發生錯誤<br /><br /> 已傳送<br /><br /> 全部<br /><br /> 預期通知<br /><br /> 未預期通知<br /><br /> 已拒絕|否|  
|交易集識別碼|等於|全部 (預設)<br /><br /> 特定交易集識別碼|否|  
  
