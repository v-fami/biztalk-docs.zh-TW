---
title: 單一登入： 事件 10597 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c57db8f-f7e4-4745-89b6-3112a3b2e1be
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d0c0f1959580dfb9bc9327021c179f616f98d71
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970559"
---
# <a name="single-sign-on-event-10597"></a>單一登入： 事件 10597
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                  企業單一登入                                                                                   |
| 產品版本 |                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                  |
|    事件識別碼     |                                                                                            10597                                                                                             |
|  事件來源   |                                                                                            ENTSSO                                                                                            |
|    元件    |                                                                                             不適用                                                                                              |
|  符號名稱  |                                                                             SSO_WARN_CALLER_NOT_IN_NEW_SSO_ADMIN                                                                             |
|  訊息文字   | 用戶端使用者必須是新 SSO 系統管理員帳戶的成員，才能變更 SSO 系統管理員帳戶 name.%r<br /><br /> 用戶端使用者: %1 %r<br /><br /> 新的 SSO 系統管理員： %2 |
  
## <a name="explanation"></a>說明  
 用戶端使用者必須是新 SSO 系統管理員帳戶的成員，才能變更 SSO 系統管理員帳戶名稱。  
  
## <a name="user-action"></a>使用者動作  
 您必須是新 SSO 系統管理員帳戶的成員，才能變更 SSO 系統管理員帳戶名稱。