---
title: 單一登入： 事件 10615 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e5dd0041-2dfd-4fd1-97ec-f9fc719a6fcc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86b99f901ba60749386d055ce771beed225e4a18
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008463"
---
# <a name="single-sign-on-event-10615"></a>單一登入： 事件 10615
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                企業單一登入                                                                                                                |
| 產品版本 |                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                |
|    事件識別碼     |                                                                                                                          10615                                                                                                                          |
|  事件來源   |                                                                                                                         ENTSSO                                                                                                                          |
|    元件    |                                                                                                                           不適用                                                                                                                           |
|  符號名稱  |                                                                                                            SSO_WARN_NO_UPDATE_TICKET_TIMEOUT                                                                                                            |
|  訊息文字   | 用戶端使用者必須是 SSO 系統管理員帳戶的成員，才能變更 application.%r 的票證逾時<br /><br /> 用戶端使用者: %1 %r<br /><br /> SSO 系統管理員: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 錯誤碼： %4 |
  
## <a name="explanation"></a>說明  
 用戶端使用者必須是 SSO 系統管理員帳戶的成員，才能變更應用程式的票證逾時。  
  
## <a name="user-action"></a>使用者動作  
 有系統管理員協助您尋找的 SSO 系統管理員帳戶的成員，才能進行這項變更。