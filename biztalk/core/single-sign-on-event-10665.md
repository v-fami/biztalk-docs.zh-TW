---
title: 單一登入： 事件 10665 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d0de9d0-9b46-4f3a-b796-1ce3de01cf4c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e820b5d682a3ea5947d4811038d4a9bc5eaa38c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013919"
---
# <a name="single-sign-on-event-10665"></a>單一登入： 事件 10665
## <a name="details"></a>詳細資料  

|                 |                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                               企業單一登入                                                |
| 產品版本 |                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                               |
|    事件識別碼     |                                                         10665                                                          |
|  事件來源   |                                                         ENTSSO                                                         |
|    元件    |                                                          N\A                                                           |
|  符號名稱  |                                                 SSO_WARN_NO_PROPERTIES                                                 |
|  訊息文字   | 讀取密碼同步配接器屬性時發生錯誤。 使用 defaults.%r<br /><br /> 配接器: %1 %r<br /><br /> 錯誤碼： %2 |

## <a name="explanation"></a>說明  
 這個警告事件表示已讀取預設密碼同步配接器屬性時發生錯誤。 每個密碼同步配接器都有與其相關聯的組態屬性。 這些屬性會儲存在 SSO 組態存放區，並建立密碼同步配接器時，由 SSO 命令列工具或 SSO 管理 MMC 所建立。  可以會那里遺失屬性如果 「 密碼同步配接器建立任何其他方法，則可以發出此錯誤。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

-   確認密碼同步配接器屬性。  

-   重新建立密碼同步配接器  

## <a name="more-info"></a>其他資訊

- **密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]

- [密碼同步](../core/password-synchronization2.md)
