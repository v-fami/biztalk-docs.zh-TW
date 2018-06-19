---
title: 執行 JMS MQRFH2 標頭保留範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65982dca-77e1-4267-9528-26c59237e9b1
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab840ed1d319f8fd50d3a386e0ffc9b349f61b9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295126"
---
# <a name="running-the-jms-mqrfh2-header-preservation-sample"></a>執行 JMS MQRFH2 標頭保留範例
此範例的這個部分會將訊息插入 WebSphere 佇列。 ESB 拾取此訊息，並將輸出的 WebSphere 佇列。 這示範了 ESB 和 Microsoft BizTalk 保留失真 RFH2 標頭如下的訊息是透過 BizTalk Server。  
  
 **若要執行保留標頭範例**  
  
1.  如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  
  
2.  執行 IBM RfhUtil 公用程式，然後選取 佇列管理員名稱為 ESB。JMS。第一個下拉式清單來連線到此佇列管理員 Sample.QueueManager。  
  
3.  在第二個下拉式清單中，選取名為 ESB 目標輸出佇列。JMS。範例。SENDTOBIZTALK，如圖 1 所示。  
  
     ![佇列管理員](../esb-toolkit/media/ch6-queuemanager.gif "第 6 章第 QueueManager")  
  
     **圖 1**  
  
     **連接到 「 佇列管理員和 RfhUtil 將傳出佇列**  
  
4.  如果下拉式清單不包含任何佇列，請確定佇列管理員正在執行檢查 WebSphere MQ 服務項目，如圖 2 所示。  
  
     ![Web 球體](../esb-toolkit/media/ch6-websphere.gif "第 6 章第 WebSphere")  
  
     **圖 2**  
  
     **檢查佇列管理員正在執行中的 WebSphere 服務項目**  
  
5.  按一下**ReadFile** RfhUtil 公用程式中的按鈕，巡覽至名為測試 000128 測試訊息檔案。JMS 位於子資料夾名為 \Source\Samples\JMS\Test\Data\Load\\。 此檔案包含 128 測試訊息批次，但是此公用程式載入只有第一個。  
  
6.  按一下**RFH**索引標籤，然後確定只有**JMS**選取核取方塊。  
  
7.  按一下**jms**索引標籤，並請確定所選**回覆**佇列是 ESB。JMS。範例。DYNAMICQ1，所選**目的地佇列**是 ESB。JMS。範例。DYNAMICQ2。  
  
8.  按一下**Main**索引標籤，然後再按一下**寫入 Q**  按鈕，將訊息寫入佇列。  
  
9. 在延遲之後應用程式執行，而 ESB 輸出訊息會出現在 ESB。JMS。範例。DYNAMICQ1 和 ESB。JMS。範例。DYNAMICQ1 佇列。 開啟 WebSphere 佇列總管並瀏覽佇列，確認這個項目。  
  
10. 返回 RfhUtil 公用程式，並連接到看到的訊息佇列。 按一下**MQMD、 RFH，** 和**jms**驗證輸入和輸出值會變更該目的地佇列中的訊息，而且回覆佇列中的訊息是相同的索引標籤除外，而不是標準的 JMS 訊息，訊息會標示為 「 其他 」。