---
title: Edifact 交換應該包含 TransactionSetGroup 或 FunctionalGroup Xml 標記 |Microsoft 文件
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
ms.openlocfilehash: adb93582daf235a7f1f0633231e536f3c5b14ab0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240102"
---
# <a name="edifact-interchange-should-have-contained-transactionsetgroup-or-functionalgroup-xml-tags"></a>Edifact 交換應該包含 TransactionSetGroup 或 FunctionalGroup Xml 標記
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|Edifact 交換應該包含 TransactionSetGroup 或 FunctionalGroup Xml 標記|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理已保留，因為 TransactionSetGroup 或 FunctionalGroup 標記未包含在交換 XML 檔案中的 EDIFACT 批次交換。  
  
 BizTalk 會處理批次的交換時，會保留，交易集的群組或一組群組的交換 XML 檔案中指定的 XML 標記。 交易集的群組會擁有 TransactionSetGroup 標記。 一組群組會指定 FunctionalGroup 標記。 如果您設定保留批次使用 接收管線和通道傳輸的傳送管線，就會發生這個錯誤狀況。 標記會設定由接收管線，並已移除的傳送管線。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認保留批次所產生的 XML 檔案有 TransactionSetGroup 標記 （適用於具有多個交易集的群組） 及/或 （適用於多個群組） 的 FunctionalGroup 標記語式正確的 XML 結構。