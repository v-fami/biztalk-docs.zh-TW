---
title: 單一登入： 事件 10679 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 645f2b74-2cbe-4c6a-b0f5-7e31f93f88c6
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbeb91e58582fcd37fca4c791b35a9edfc558c96
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000351"
---
# <a name="single-sign-on-event-10679"></a>單一登入： 事件 10679
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                           企業單一登入                                                                                                            |
| 產品版本 |                                                                                           [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                           |
|    事件識別碼     |                                                                                                                     10679                                                                                                                      |
|  事件來源   |                                                                                                                     ENTSSO                                                                                                                     |
|    元件    |                                                                                                                      N\A                                                                                                                       |
|  符號名稱  |                                                                                                          SSO_WARN_PS_MAPPING_DISABLED                                                                                                          |
|  訊息文字   | 外部密碼變更。 因為對應 disabled.%r 密碼未變更外部帳戶<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 外部帳戶： %4 |

## <a name="explanation"></a>說明  
 這個警告事件表示，密碼未變更外部帳戶因為對應已停用。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列：  

-   若要啟用對應，此配接器使用 SSO 管理工具。  

## <a name="more-info"></a>其他資訊

- [密碼同步](../core/password-synchronization2.md)  

- **密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
