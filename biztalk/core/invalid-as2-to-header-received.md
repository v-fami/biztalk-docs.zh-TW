---
title: 無效的 AS2-To 標頭接收 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56cd16b3-511b-4716-8806-817f174f0b0e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0bc9fd8043205920f69aec2ca7efbfcc9478724
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010351"
---
# <a name="invalid-as2-to-header-received"></a>無效的 AS2-To 標頭接收
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                          InvalidAS2ToNameHeaderReceivedError                           |
|  訊息文字   |                      收到無效的 AS2-To 標頭。  值： {0}                       |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換，因為值的 AS2-To 標頭訊息中不符合 AS2 RFC 4130 中的規格。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定值，在 AS2-To 標頭的訊息符合 AS2 RFC 4130 第 6.2 節的規格。