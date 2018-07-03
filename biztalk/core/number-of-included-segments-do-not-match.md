---
title: 包括的區段數目不符合 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c868de02-fda7-4d84-be50-2c08cde0450c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0d2b91ba8ddecfe4926cbc21834b239eedc4547
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009383"
---
# <a name="number-of-included-segments-do-not-match"></a>包含的區段數目不相符
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                        X12TsIncludedSegCountMismatchDescription                        |
|  訊息文字   |                        包含的區段數目不相符                        |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 X12 交換的交易集的區段數目與交易集結尾 (SE01 欄位) 中的數目不相等。 會發生這種情況時保留交換，並發生錯誤時暫停交換。  
  
## <a name="user-action"></a>使用者動作  
 若要解決此錯誤，確定交換結尾的 SE01 欄位中的數目與交換集中的區段數目相同，然後重新傳送交換。