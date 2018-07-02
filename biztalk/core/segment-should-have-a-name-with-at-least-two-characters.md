---
title: 區段應該有至少兩個字元的名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f80bbc4a-151a-4094-8640-1944e8812730
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: def67be8b1c146bd6da37b669a71f2be15e22e2d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985959"
---
# <a name="segment-should-have-a-name-with-at-least-two-characters"></a>區段應該有至少兩個字元的名稱
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                             SchemaCode103EInvalidTagLength                             |
|  訊息文字   |                 區段應該有至少 2 個字元的名稱                  |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，因為交換中的區段名稱沒有至少 2 個字元。  
  
## <a name="user-action"></a>使用者動作  
 若要解決此錯誤，請指示交換的傳送者確定交換的每個區段名稱都有至少 2 個字元，然後重新傳送交換。