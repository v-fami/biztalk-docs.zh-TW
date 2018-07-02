---
title: 從 ISA 資料中讀取分隔符號時發生錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8cb60abd-53c8-45e1-a840-d27dc974aad7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3cb0dac30c18cb2c6da9c5a57818ce301fe95ec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015735"
---
# <a name="error-encountered-in-reading-delimiters-from-isa-data"></a>從 ISA 資料中讀取分隔符號時發生錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                     InvalidIsaData                                     |
|  訊息文字   |                 從 ISA 資料中讀取分隔符號時發生錯誤                  |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線發生錯誤時正在處理內送 X12 交換因為無法剖析從 ISA 區段的分隔符號。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認內送交換的 ISA 區段中的分隔符號是唯一且有效。 如果沒有，則已交換傳送者在每個分隔符號欄位 （做為重複分隔符號的 ISA11 區段和元件分隔符號 ISA16 區段），輸入唯一且有效的值，然後再重新傳送交換。