---
title: 單一登入： 事件 10603 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 139d1eb5-af88-4216-9604-c052f3db13c9
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5416ae8a2dcfdf5a3da6d8c1d00eb5a556fc3599
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970063"
---
# <a name="single-sign-on-event-10603"></a>單一登入： 事件 10603
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                             企業單一登入                                                              |
| 產品版本 |                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                             |
|    事件識別碼     |                                                                       10603                                                                        |
|  事件來源   |                                                                       ENTSSO                                                                       |
|    元件    |                                                                        不適用                                                                         |
|  符號名稱  |                                                                 SSO_WARN_DB_ACCESS                                                                 |
|  訊息文字   | 無法存取 SSO 資料庫。 如果此狀況持續發生，SSO 服務將會移 offline.%r<br /><br /> %1.%r<br /><br /> SQL 錯誤碼： %2 |
  
## <a name="explanation"></a>說明  
 無法使用 SSO 資料庫。  
  
## <a name="user-action"></a>使用者動作  
 請檢查警告中所包含的 SQL 錯誤碼。 這可能會提供一些指引。 如果沒有，請連絡 Microsoft 產品支援服務。