---
title: Edifact 交易集在 UNT01 中有不相符的計數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2859274-78e8-4e16-92b7-c143da6da421
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717260f8e45298c19756707ed042b97ab6e207fb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016045"
---
# <a name="the-edifact-transaction-set-had-a-mismatched-count-in-unt01"></a>Edifact 交易集在 UNT01 中有不相符的計數
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                          |
| 產品版本 |                                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                      |
|    事件識別碼     |                                                                  -                                                                  |
|  事件來源   |                       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                        |
|    元件    |                                                             將 EDI 引擎                                                              |
|  符號名稱  |                                                      EfactUnhUntCountMismatch                                                       |
|  訊息文字   | Edifact 交易集在 UNT01 中有不相符的計數。 UNT01 已{0}，但它應該是{1}。 已更正。 |
  
## <a name="explanation"></a>說明  
 這則警告表示 UNT01 欄位，也就是區段計數，不符的交易集的區段數目。 UNT01 值已變更或損毀，或是加入或刪除之後決定計數區段。 傳送管線重 UNT01 欄位設為正確的區段數目，然後傳送交換。  
  
## <a name="user-action"></a>使用者動作  
 使用者不必採取任何動作。