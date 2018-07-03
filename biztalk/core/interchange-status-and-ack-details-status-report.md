---
title: 交換狀態和通知詳細資料狀態報告 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebba4af5-6dff-4bb8-9c63-739ef49bbbb8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3201bc969bc053e9a128cbb0e65a42a2714480c3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999023"
---
# <a name="interchange-status-and-ack-details-status-report"></a>交換狀態和通知詳細資料狀態報告
這份狀態報告會顯示交換的詳細資料，以及與其相關的交換 (技術) 通知和功能通知。 顯示此報表的交換內 [交換/通知狀態] 報告中，以滑鼠右鍵按一下，然後按一下**交換狀態和通知詳細資料**。  
  
 這份報告會提供下列針對交換和相關通知的個別檢視：  
  
## <a name="interchange-status"></a>交換狀態  
 這個檢視提供顯示下列欄位之值的表格：  
  
- 傳送者合作對象識別碼  
  
- 接收者合作對象識別碼  
  
- 控制項 ID  
  
- 接收者合作對象名稱  
  
- 傳送者合作對象名稱  
  
- 方向  
  
- 交換日期時間  
  
  > [!NOTE]
  >  接收文件，如果交換中所指定的日期是 YYMMDD 格式，而且 YY 是大於或等於 75，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將年份顯示為 19YY。 如果日期為少於 75 台，它會顯示為 20YY。  
  > 
  >  比方說，如果您收到包含值 991113 中 isa09-交換，交換日期將會列出在報表中為 11/13/1999年。  
  
- 群組計數  
  
- 連接埠識別碼  
  
- 交換狀態  
  
- EDI 編碼類型  
  
- 交易集合相互關聯識別碼  
  
  如果做為交換接收者的合作對象已經啟用技術通知 (在 [EDI 屬性] 對話方塊的 [通知處理和驗證設定] 頁面中)，BizTalk Server 便會期待收到可回應其傳送之交換而傳回的技術 (交換) 通知。 一開始在建立輸出交換的交換狀態項目時，BizTalk Server 會在 [交換狀態] 欄位中輸入「預期通知」。 當它收到技術通知，並使其與原始的交換相互關聯時，便會更新 [交換狀態] 欄位，以表示它已經收到通知。  
  
## <a name="interchange-ack-status"></a>交換通知狀態  
 這個檢視會顯示交換 (技術) 通知的狀態值。  
  
-   通知交換控制項 ID  
  
-   接收者合作對象  
  
-   傳送者合作對象  
  
-   方向  
  
-   通知交換日期  
  
-   通知交換時間  
  
-   通知狀態  
  
-   狀態碼  
  
-   通知說明碼 1  
  
-   通知說明碼 2  
  
## <a name="functional-acks"></a>功能通知  
 這個檢視會顯示功能通知的狀態值。  
  
-   群組控制編號  
  
-   接收者合作對象  
  
-   傳送者合作對象  
  
-   方向  
  
-   [狀態]  
  
-   狀態碼  
  
-   功能識別項程式碼  
  
-   TS 計數  
  
-   通知交換控制項 ID  
  
-   通知交換日期  
  
-   通知交換時間  
  
-   已傳遞 TS 計數  
  
-   已接受 TS 計數  
  
-   ErrorCode 1  
  
-   ErrorCode 2  
  
-   錯誤碼 3  
  
-   錯誤碼 4  
  
-   錯誤碼 5  
  
-   接收時間