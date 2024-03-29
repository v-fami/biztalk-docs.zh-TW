---
title: 什麼是量值和維度？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e6b12a4c-9be5-4cac-b5b9-ece376d28cb1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb494246741699dfdbdab704c8fca0a3c9d55301
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994343"
---
# <a name="what-are-measures-and-dimensions"></a>什麼是量值和維度？
維度和量值是資料彙總的實體層面。 本主題使用 BAM 實例提供環境以說明量值和維度的意義。  
  
## <a name="measures"></a>量值  
 假設您以極其簡單的方式，為訂單管理程序定義了包含三個項目的 BAM 活動：  
  
1. 程序開始時間 (現實世界的事件)  
  
2. 程序結束時間 (也是現實世界的事件)  
  
3. 程序持續時間 (#2 - #1 的計算)  
  
   在此例中將資料彙總是很容易的；只需將彙總函式 (例如，平均值、最小值、最大值等) 套用到一系列個別的持續時間值 (亦即，每張訂單的持續處理期間)。  
  
   「平均持續時間」的概念是量值，並且為單一值。 這個量值會自行產生與程序管理相關的資訊，藉以指示程序的整體表現 (就適時性/處理能力而言) 是否如預期一般。 不過，由於缺少其他的資料 (因為「平均持續時間」是單一值)，要瞭解量值實際值的意義會比較困難；例如，本週的平均持續時間為什麼會突增？ 是否因為特定的夥伴、計劃或產品而引起？  
  
## <a name="dimensions"></a>維度  
 維度是協助量值取用者瞭解這些量值意義的內涵。  
  
 續上例，假設您為訂單管理程序另外新增三個項目到 BAM 活動中：  
  
1. 交易夥伴名稱 (傳送訂單者)  
  
2. 業務經理名稱 (銷售連絡人)  
  
3. 銷售地區  
  
   因為活動現在包含三個可能的資料樞紐 (夥伴、業務經理、地區)，彙總這項資料的實際結果將會在執行階段建立三維度的 Cube。  
  
   彙總仍然從工作的第一個項目開始進行，結果會建立單一的「平均持續時間」量值。 當工作的下一個項目 (因另一張訂單的到來而起始) 完成時，如果此項目的交易夥伴、業務經理和地區都和工作第一個項目的完全相同，那麼目前所要進行的，就只是根據兩個項目 (例如，兩個持續時間的平均值) 重新計算「平均持續時間」量值，以取得單一「平均持續時間」量值的值。  
  
   但是只要有不同於此前所遇交易夥伴、業務經理或地區的一組項目出現，就會建立「平均持續時間」量值的新值，並與第一個項目分開維護。  
  
   例如，如果工作第三個項目的交易夥伴和前兩個項目的不同，結果將會在交易夥伴維度上產生第二個「平均持續時間」量值的值。 您現在可以沿著交易夥伴維度檢視「平均持續時間」值，並且會看到像是「處理 TradingPartnerX 的訂單所花費的平均時間幾乎是處理 TradingPartnerY 的訂單所需時間的兩倍」等的情況。 此外，維度可以摺疊以方便檢視，這樣您就仍然能看見與任何交易夥伴或其他維度無關之程序的整體「平均持續時間」。  
  
   最後，如果交易夥伴、業務經理和地區各自都有恰好三個不同的值，一旦出現所有的排列組合，產生的結果將會一個 Rubik's® Cube 的資料；使用者可以在產生的 27 個獨立維護的「平均持續時間」值中擇一進行檢視，而其中的維度即是 Cube 三邊上的一邊。  
  
   如需有關維度和量值的其他資訊，請參閱「Excel 說明」中的＜關於樞紐分析表和樞紐分析圖的 OLAP 資料來源＞。