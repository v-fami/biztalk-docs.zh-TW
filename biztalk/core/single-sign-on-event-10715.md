---
title: 單一登入： 事件 10715 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f63c98d2-988e-466f-be40-171b13a34732
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9bc461aa812c2c61844c11d54743335ac89321a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994855"
---
# <a name="single-sign-on-event-10715"></a>單一登入： 事件 10715
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                            企業單一登入                                                                                             |
| 產品版本 |                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                            |
|    事件識別碼     |                                                                                                      10715                                                                                                       |
|  事件來源   |                                                                                                      ENTSSO                                                                                                      |
|    元件    |                                                                                                       N\A                                                                                                        |
|  符號名稱  |                                                                                            SSO_WARN_NO_CREATE_ADAPTER                                                                                            |
|  訊息文字   | 用戶端使用者必須是 SSO 系統管理員帳戶的成員，才能建立配接器。%r<br /><br /> 用戶端使用者: %1 %r<br /><br /> SSO 系統管理員: %2 %r<br /><br /> 配接器: %3 %r<br /><br /> 錯誤碼： %4 |

## <a name="explanation"></a>說明  
 這個警告事件表示用戶端使用者必須是 SSO 系統管理員帳戶的成員，才能建立配接器。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

- 使用屬於 SSO 系統管理員群組的帳戶登入。  

  如需詳細資訊，請參閱下列資源：  

- [SSO 使用者群組](../core/sso-user-groups.md)
