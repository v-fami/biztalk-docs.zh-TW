---
title: 單一登入： 事件 10673 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa1d572a-1e9f-496e-a219-852e7d9228d5
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fb923d1e137a00eed4ba87e65df71b226287aa2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975135"
---
# <a name="single-sign-on-event-10673"></a>單一登入： 事件 10673
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                                                                                                                          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                                                        企業單一登入                                                                                                                                                                         |
| 產品版本 |                                                                                                                                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                        |
|    事件識別碼     |                                                                                                                                                                                  10673                                                                                                                                                                                   |
|  事件來源   |                                                                                                                                                                                  ENTSSO                                                                                                                                                                                  |
|    元件    |                                                                                                                                                                                   N\A                                                                                                                                                                                    |
|  符號名稱  |                                                                                                                                                                SSO_INFO_WINDOWS_MAPPING_CONFLICT_ALLOWED                                                                                                                                                                 |
|  訊息文字   | 外部密碼變更將造成一個以上的 Windows account.%r 變更<br /><br /> 這被允許的因為這個外部系統的配接器已設定為允許對應 conflicts.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 外部帳戶: %3 %r<br /><br /> Windows 帳戶 1: %4 %r<br /><br /> Windows 帳戶 2: %5 |

## <a name="explanation"></a>說明  
 這個資訊事件表示外部密碼變更會導致多個 Windows 帳戶的變更。  

## <a name="user-action"></a>使用者動作  

-   使用者不必採取任何動作。  

## <a name="more-info"></a>其他資訊

- [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)  

- **密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]

- [密碼同步](../core/password-synchronization2.md)
