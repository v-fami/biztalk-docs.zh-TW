---
title: 單一登入： 事件 10574 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f2a5aa-3a19-4d7c-9257-89f1567a3c2d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be3700f565dafb9003a3cc05d9e52c7559904f88
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976951"
---
# <a name="single-sign-on-event-10574"></a>單一登入： 事件 10574
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                        企業單一登入                                                                         |
| 產品版本 |                                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                        |
|    事件識別碼     |                                                                                  10574                                                                                   |
|  事件來源   |                                                                                  ENTSSO                                                                                  |
|    元件    |                                                                                   不適用                                                                                    |
|  符號名稱  |                                                                     SSO_WARN_INVALID_SSO_ADMIN_GROUP                                                                     |
|  訊息文字   | SSO 系統管理員帳戶對全域資訊 update.%r 無效<br /><br /> SSO 系統管理員: %1 %r<br /><br /> 無效的帳戶: %2 %r<br /><br /> 錯誤碼： %3 |
  
## <a name="explanation"></a>說明  
 SSO 系統管理員帳戶的全域資訊更新無效。  
  
## <a name="user-action"></a>使用者動作  
 警告訊息會包含 SSO 系統管理員帳戶 」 和 「 無效的帳戶的相關資訊。 檢閱這項資訊、 進行任何必要的修正，並再試一次更新。