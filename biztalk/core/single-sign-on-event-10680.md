---
title: 單一登入： 事件 10680 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 88ea12ff-d181-423f-9054-b0c656cc4558
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1ce2871618722af1fce4175be715c8ac1fa55a9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974895"
---
# <a name="single-sign-on-event-10680"></a>單一登入： 事件 10680
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                        企業單一登入                                                                                                                                        |
| 產品版本 |                                                                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                        |
|    事件識別碼     |                                                                                                                                                  10680                                                                                                                                                  |
|  事件來源   |                                                                                                                                                 ENTSSO                                                                                                                                                  |
|    元件    |                                                                                                                                                   N\A                                                                                                                                                   |
|  符號名稱  |                                                                                                                                      SSO_WARN_PS_GET_CREDS_FAILED                                                                                                                                       |
|  訊息文字   | 外部帳戶的密碼未變更，因為無法從 SSO 資料庫取得現有外部認證。%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 外部帳戶: %4 %r<br /><br /> 錯誤碼： %5 |

## <a name="explanation"></a>說明  
 這個警告事件表示，密碼未變更外部帳戶因為無法從 SSO 資料庫取得現有外部認證。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

-   驗證外部認證。  

-   外部認證不正確，請使用 SSO 管理工具設定此外部帳戶的外部認證。 您必須在所有相關聯的應用程式中設定 （適用於指定的帳戶） 的外部密碼。  

## <a name="more-info"></a>其他資訊

- [密碼同步](../core/password-synchronization2.md)  

- **密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
