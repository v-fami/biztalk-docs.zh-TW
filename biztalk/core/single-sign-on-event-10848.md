---
title: 單一登入： 事件 10848 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61888420-29a6-4c64-a884-1b074b586f21
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59a324ff0a5de2ac6d2292692f2132c10aaabc5b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991031"
---
# <a name="single-sign-on-event-10848"></a>單一登入： 事件 10848
## <a name="details"></a>詳細資料  
  
|                 |                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------|
|  產品名稱   |                                 企業單一登入                                  |
| 產品版本 |                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                 |
|    事件識別碼     |                                           10848                                            |
|  事件來源   |                                           ENTSSO                                           |
|    元件    |                                            不適用                                             |
|  符號名稱  |                         ENTSSO_E_DIRECT_SYNC_NOT_ALLOWED_AMBIGUOUS                         |
|  訊息文字   | 因為欄位模稜兩可，所以不允許這個應用程式的直接密碼同步。 |
  
## <a name="explanation"></a>說明  
 如果有兩個以上的欄位，則只有唯一一個必須標示為密碼同步。  
  
## <a name="user-action"></a>使用者動作  
 若要修正這種情況，您必須刪除應用程式然後重新建立，讓應用程式遵循這些準則。