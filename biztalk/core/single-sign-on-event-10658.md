---
title: 單一登入： 事件 10658 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5bee12d-502b-4fee-bc84-25807eb0e48e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd6ea4cb33e6df4fe8a59fc1041861bdb530aaa4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982247"
---
# <a name="single-sign-on-event-10658"></a>單一登入： 事件 10658
## <a name="details"></a>詳細資料  

|                 |                                                                                   |
|-----------------|-----------------------------------------------------------------------------------|
|  產品名稱   |                             企業單一登入                             |
| 產品版本 |            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]             |
|    事件識別碼     |                                       10658                                       |
|  事件來源   |                                      ENTSSO                                       |
|    元件    |                                        N\A                                        |
|  符號名稱  |                   SSO_ERROR_PASSWORD_SYNC_ADAPTERS_START_FAILED                   |
|  訊息文字   | 外部配接器的密碼同步無法啟動。%r<br /><br /> 錯誤碼： %1 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示外部配接器的密碼同步無法啟動。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  

-   檢查應用程式和系統事件記錄檔相關聯的事件。  

-   確認配接器組態屬性。  

## <a name="more-info"></a>其他資訊  

- [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)  

- **企業單一登入 UI 說明** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
