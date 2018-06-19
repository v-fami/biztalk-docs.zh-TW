---
title: EDI 和 AS2 狀態報告 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9e58b29-9be0-41d6-ad35-1aae28e1a784
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31b08fd8222cee0cb0f04750eedcb32d06c28820
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241382"
---
# <a name="edi-and-as2-status-reporting"></a>EDI 和 AS2 狀態報告
EDI 狀態報告可以讓作業人員追蹤 EDI 和 AS2 傳輸的狀態。 如果啟用，狀態報告會提供文件交換交易的完整狀態，包括交換以及與交換相互關聯的任何通知。 這些報告提供 EDI 和 AS2 訊息處理的接收、驗證、批次處理和通知相關資料。  
  
 您可以使用這些報告取得擱置中和未通知的交換、完整交換、錯誤實例或商務實例等項目的狀態。 使用這些報告，您可以執行下列動作：  
  
-   確認接收交換  
  
-   列出等待通知的外寄交換  
  
-   列出所有已拒絕的已接收交換  
  
-   列出報告為已拒絕或已部分接受的外寄交換。  
  
 狀態報告中所包含的資料取自交換控制區段，例如 ISA、TA1、GS、UNB 和 UNG (功能通知狀態除外)。  
  
 **狀態報告 UI**  
  
 EDI 和 AS2 狀態報告可從 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 取得。 從**群組中樞**頁面**BizTalk 群組** 節點，您已連結至 EDI 交換和相互關聯的通知狀態、 批次狀態，以及 AS2 訊息和相互關聯的 MDN 狀態。 這些報告會提供您可以從查詢運算式包含或排除的狀態參數範圍，讓您建置所需的狀態報告。  
  
 除了能看到 EDI 交換的狀態，還可以檢視交換中的交易集。 只要啟用追蹤 (BizTalkDTADb) 資料庫 EDI 資料表中的訊息內容儲存區，就能達到此目的。 使用狀態報告 UI 中的檢視詳細資料命令，即可檢視交易集。  
  
 您也可以將輸入或輸出 AS2 訊息或 MDN 儲存在不可否認性的資料庫中。 以滑鼠右鍵按一下狀態報告中的訊息並選取適當的命令，即可檢視交易集或 AS2 訊息。  
  
 **狀態報告元件**  
  
 狀態報告的相關 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件如下：  
  
-   EDI 接收管線中的 EDI 解譯器，會在內送交換的資料存放區中建立並更新狀態項目  
  
-   EDI 傳送管線中的 EDI 組合器，會在外送交換的資料存放區中建立並更新狀態項目  
  
-   存放狀態報告項目的資料存放區。 包括用來追蹤資料的 BAM 主要匯入資料庫，以及 EDI 交易集和 (或) AS2 訊息內容專用之 BizTalk 追蹤資料庫 (BizTalkDTADb) 的 EDI Message Content 資料表  
  
-   狀態報告 UI 上**群組中樞**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，用來顯示狀態報告資料  
  
-   [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 中的協議屬性和後援協議屬性選項，可用來啟用及設定狀態報告  
  
-   運用 BAM 基礎結構的 DTA 和 SQL 分析伺服器。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定 EDI 和 AS2 狀態報告](../core/configuration-of-edi-and-as2-status-reporting.md)  
  
-   [類型的 EDI 和 AS2 狀態報告](../core/types-of-edi-and-as2-status-reports.md)  
  
-   [EDI 和 AS2 狀態報告的儲存資料](../core/data-stored-for-edi-and-as2-status-reports.md)  
  
-   [資料如何儲存 EDI 和 AS2 狀態報告](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)