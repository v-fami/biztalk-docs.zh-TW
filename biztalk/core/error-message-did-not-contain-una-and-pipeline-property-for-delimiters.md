---
title: 訊息不包含 UNA，而且分隔符號的管線屬性的格式不正確 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b761d820-e09d-4949-bb41-da9e66054c60
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717626c6ba38d8e278ad173739c28d502c3d6e0d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967775"
---
# <a name="message-did-not-contain-una-and-pipeline-property-for-delimiters-was-incorrect-format"></a>訊息不包含 UNA，而且分隔符號的管線屬性的格式不正確
## <a name="details"></a>詳細資料  
  
|                 |                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------|
|  產品名稱   |     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]      |
| 產品版本 |                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                  |
|    事件識別碼     |                                              -                                              |
|  事件來源   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI    |
|    元件    |                                         將 EDI 引擎                                          |
|  符號名稱  |                                EfactDelimiterIncorrectFormat                                |
|  訊息文字   | 訊息不包含 UNA，而且分隔符號的管線屬性的格式不正確 '{0}' |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送 EDIFACT 交換因為無法判定處理交換時所需的分隔符號。 如果交換沒有 UNA 區段，而且 EfactDelimiters 管線屬性並未充分定義的分隔符號，這可能會發生。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
1.  請確定交換已定義的交換中，分隔符號的 UNA 區段，然後再重新傳送交換。  
  
2.  EfactDelimiters 管線藉由開啟 BizTalk Server 管理主控台，以滑鼠右鍵按一下接收位置，可以接收的交換，內容，按一下省略符號，將管線的傳送管線 屬性的集合和然後輸入字串，包含分隔符號的值。