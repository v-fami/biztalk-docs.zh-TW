---
title: Edifact 交換應該包含 TransactionSetGroup 或 FunctionalGroup Xml 標記 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 34318133-211f-422d-acdf-b841ece5d2b0
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5736a9146a88dd9c9dac6747e381fccc88f18d9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979327"
---
# <a name="edifact-interchange-should-have-contained-transactionsetgroup-or-functionalgroup-xml-tags"></a>Edifact 交換應該包含 TransactionSetGroup 或 FunctionalGroup Xml 標記
## <a name="details"></a>詳細資料  
  
|                 |                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------|
|  產品名稱   |    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]     |
| 產品版本 |                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                 |
|    事件識別碼     |                                             -                                             |
|  事件來源   |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI   |
|    元件    |                                        將 EDI 引擎                                         |
|  符號名稱  |                                             -                                             |
|  訊息文字   | Edifact 交換應該包含 TransactionSetGroup 或 FunctionalGroup Xml 標記 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理批次的 EDIFACT 交換因為交換 XML 檔案中未包含 TransactionSetGroup 或 FunctionalGroup 的標記時保留。  
  
 BizTalk 可處理的批次的交換時，會保留，交易集的群組或交換的 XML 檔案中的群組一組指定的 XML 標記。 交易集群組的指定 TransactionSetGroup 標記。 群組一組指定的 FunctionalGroup 標記。 如果您設定保留批次使用 接收管線，並通過傳輸的傳送管線，就會發生這個錯誤狀況。 標記會由接收管線設定，並移除的傳送管線。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定保留批次產生的 XML 檔案有 TransactionSetGroup 標記 （適用於具有多個交易集的群組） 及/或 （適用於多個群組） 的 FunctionalGroup 標記語式正確的 XML 結構。