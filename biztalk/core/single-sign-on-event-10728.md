---
title: 單一登入： 事件 10728 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f579189c-c9a5-4d2c-a3d5-f0ba03c5a3ef
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5e37738d0bf566b2faf3b5b65c1152cd3ef6405
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995287"
---
# <a name="single-sign-on-event-10728"></a>單一登入： 事件 10728
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                     企業單一登入                                                                                                                     |
| 產品版本 |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                     |
|    事件識別碼     |                                                                                                                               10728                                                                                                                               |
|  事件來源   |                                                                                                                              ENTSSO                                                                                                                               |
|    元件    |                                                                                                                                N\A                                                                                                                                |
|  符號名稱  |                                                                                                                         SSO_ERROR_VERSION                                                                                                                         |
|  訊息文字   | 這個版本的 SSO 伺服器與不相容的 SSO 資料庫。 請升級您的主要祕密 server.%r<br /><br /> SQL Server 名稱: %1 %r<br /><br /> SSO 資料庫名稱: %2 %r<br /><br /> SSO 資料庫版本: %3 %r<br /><br /> 必要版本： %4 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示 SSO 伺服器版本是比 （原先建立的版本） 還新的 SSO 資料庫。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 升級 SSO 主要祕密伺服器，以符合此 SSO 伺服器目前的版本。 這會將目前的版本升級 SSO 資料庫。  

  如需詳細資訊，請參閱下列資源：  

- [管理主要密碼](../core/managing-the-master-secret.md)
