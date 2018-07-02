---
title: 單一登入： 事件 11012 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 252bedc8-8dc3-4962-b078-465f9b064ead
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28f78d834e57a85e05de143612d376b77ebed799
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988007"
---
# <a name="single-sign-on-event-11012"></a>單一登入： 事件 11012
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                               企業單一登入                                                                                                |
| 產品版本 |                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                               |
|    事件識別碼     |                                                                                                         11012                                                                                                          |
|  事件來源   |                                                                                                         ENTSSO                                                                                                         |
|    元件    |                                                                                                          不適用                                                                                                           |
|  符號名稱  |                                                                                           SSO_WARN_NOT_APP_ADMIN_ADMIN_SAME                                                                                            |
|  訊息文字   | 用戶端使用者不是應用程式系統管理員 account.%r 的成員<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 用戶端使用者： %2\\%3 %r<br /><br /> 應用程式名稱: %4 %r<br /><br /> 應用程式系統管理員： %5 |
  
## <a name="explanation"></a>說明  
 用戶端使用者不是應用程式系統管理員帳戶的成員。 稽核層級設定為高時，才會出現這個警告。  
  
## <a name="user-action"></a>使用者動作  
 若要補救這種情況，您必須進行用戶端使用者應用程式系統管理員帳戶的成員。 若要停止這項警告不會出現在未來，您可以降低稽核層級。