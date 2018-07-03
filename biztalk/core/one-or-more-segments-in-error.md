---
title: 一或多個區段發生錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ee86667-e72a-4f1b-8d5c-15ca710dbe5d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c364af2691767ac55a52afb52b77f09d39ef6d2d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005064"
---
# <a name="one-or-more-segments-in-error"></a>一或多個區段發生錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                        X12TsOneOrMoreSegmentsInErrorDescription                        |
|  訊息文字   |                             一或多個區段發生錯誤                              |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，來管理它們的結構描述不符合交換中的一個或多個區段。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，判斷哪一個區段中錯誤、 開啟結構描述來控管該區段中，以及判斷從該區段處於錯誤的結構描述。