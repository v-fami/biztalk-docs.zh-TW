---
title: 遺失必要的區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e459a22-8de5-426a-a46a-1d0ab72b532d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2bc9775da2fcbef756774c576074b471e808484
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977087"
---
# <a name="mandatory-segment-missing"></a>遺失必要的區段
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                         X12MandatorySegmentMissingDescription                          |
|  訊息文字   |                               遺失必要的區段                                |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換，因為交換未包含所需的訊息結構描述 （minoccurs 大於 0） 的區段。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定此交換包含的訊息結構描述中，所需的所有區段，然後必須將訊息重新傳送。