---
title: 區段未依照正確順序排列 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f0c0fdc-10d9-4b77-a80d-b2b8571e7665
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2e90f42fdc3226827dae670daecb0e856eba156
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980359"
---
# <a name="segment-not-in-proper-sequence"></a>區段未依照正確順序排列
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                        X12SegmentNotInProperSequenceDescription                        |
|  訊息文字   |                             區段未依照正確順序排列                             |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於內送 X12 交換中的區段未依照文件結構描述指定的順序排列，因此接收管線無法處理該交換。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，交換的傳送者必須重新排列交換中的區段，使這些區段依照文件結構描述指定的順序排列，然後再重新傳送交換。