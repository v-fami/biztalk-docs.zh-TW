---
title: 單一登入： 事件 10745 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed630e40-d876-4e90-937e-4d2d54fe9f1a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bb3afa69e4a959b189347ac20b71acfc58208f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984751"
---
# <a name="single-sign-on-event-10745"></a>單一登入： 事件 10745
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                          企業單一登入                                                           |
| 產品版本 |                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                          |
|    事件識別碼     |                                                                    10745                                                                     |
|  事件來源   |                                                                    ENTSSO                                                                    |
|    元件    |                                                                     N\A                                                                      |
|  符號名稱  |                                                          SSO_ERROR_ADAPTER_OFFLINE                                                           |
|  訊息文字   | 配接器已 offline.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 錯誤訊息: %3 %r<br /><br /> 錯誤碼： %4 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示指定的配接器已離線。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  

- 請檢查系統和應用程式事件日誌中的相關錯誤。  

- 請檢查有錯誤的外部介面卡。  

  如需詳細資訊，請參閱下列資源：  

- [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)
