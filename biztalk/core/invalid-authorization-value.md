---
title: 無效的授權值 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70d0dd75-b045-4b67-ba23-78551493f074
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 674585daa50f0adc0708a792b318bc0b736eca49
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974431"
---
# <a name="invalid-authorization-value"></a>無效的授權值
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                       X12Ta1InvalidAuthorizationValueDescription                       |
|  訊息文字   |                              無效的授權值                               |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，因為在 ISA02 授權資訊的值不符合結構描述 （如果是 X12_AN)，所指定的資料類型，或沒有結構描述 (10) 所需的數字數目。 結構描述是 X12ServiceSchema BaseArtifacts.dll 中。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定 ISA02 標頭中的值是否符合 X12： 資料型別和有 10 位數 （使用尾端空格），然後重新傳送交換。