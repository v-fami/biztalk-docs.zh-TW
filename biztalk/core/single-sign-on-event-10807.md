---
title: 單一登入： 事件 10807 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 882c01c6-70db-4986-9f4b-f08335424250
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9e23aefbb950160f29b6145e64bfaa1784dc3f1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985407"
---
# <a name="single-sign-on-event-10807"></a>單一登入： 事件 10807
## <a name="details"></a>詳細資料  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  產品名稱   |                 企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    事件識別碼     |                           10807                            |
|  事件來源   |                           ENTSSO                           |
|    元件    |                            不適用                             |
|  符號名稱  |        ENTSSO_E_TOO_MANY_UNCONFIRMED_NOTIFICATIONS         |
|  訊息文字   |            太多未確認的通知。             |
  
## <a name="explanation"></a>說明  
 傳送密碼變更通知每次，但在收到確認訊息。 在此情況下，已超過此限制，而不需要確認的通知。  
  
## <a name="user-action"></a>使用者動作  
 檢查 「 密碼同步配接器。