---
title: 區段有尾端分隔符號，在元件或子元件層級 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 517f1cfc-66c1-47e6-be94-2c76c1f89230
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94b95e45cc4c6676bdbd2e787661a73547f45148
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024237"
---
# <a name="segment-has-trailing-delimiters-at-component-or-sub-component-level"></a>區段有尾端分隔符號，在元件或子元件層級
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                      X12SeSegmentHasTrailingDelimiterDescription                       |
|  訊息文字   |         區段有尾端分隔符號，在元件或子元件層級          |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換包含尾端分隔符號，但未啟用做為交換傳送者合作對象的尾端分隔符號。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，啟用 尾端分隔符號，如下所示：  
  
1.  開啟 BizTalk Server 管理主控台，移至 [合作對象] 資料夾中，然後開啟 EDI 屬性的合作對象。  
  
2.  移至 驗證和通知產生頁面為 X12 或 EDIFACT，視需要。  
  
3.  按一下 [允許尾端分隔符號]。