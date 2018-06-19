---
title: TA1 交換中包含發生下列錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2d63fe9-63ef-44b3-8cb9-45a7abf8d0e4
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03bd7486d25e2c94fc809e6dc50c43359c152b70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278630"
---
# <a name="the-ta1-contained-in-interchange-had-the-following-errors"></a>TA1 交換中包含發生下列錯誤
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12TA1Error|  
|訊息文字|在識別碼為 '{1}'，寄件者 id '{2}' 交換中包含 {0} TA1、 接收者識別碼 '{3}' 發生下列錯誤：|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送的 TA1 通知發生指出的錯誤狀況。 這可能表示通知不符合 TA1Schema。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，讓傳送者的通知解決問題的通知，確保該通知符合 TA1Schema，然後再重新傳送通知。