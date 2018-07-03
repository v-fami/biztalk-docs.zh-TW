---
title: 單一登入： 事件 10526 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f72d466-8b63-453c-b608-f9d64f635f65
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 433190146391c494ff3b890c8332cc15fb947753
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024452"
---
# <a name="single-sign-on-event-10526"></a>單一登入： 事件 10526
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                     企業單一登入                                                                     |
| 產品版本 |                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                     |
|    事件識別碼     |                                                                               10526                                                                               |
|  事件來源   |                                                                              ENTSSO                                                                               |
|    元件    |                                                                                N\A                                                                                |
|  符號名稱  |                                                                 SSO_ERROR_GENERATE_SECRET_FAILED                                                                  |
|  訊息文字   | 無法產生新的主要密碼。%r<br /><br /> 用戶端使用者: %1 %r<br /><br /> 用戶端電腦：%2%r<br /><br /> 追蹤識別碼: %3 %r<br /><br /> 錯誤碼： %4 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示使用者嘗試產生新的主要祕密失敗。 這可能是因為權限 （您必須是 SSO 系統管理員，以產生主要祕密） 的問題，或可能有寫入備份檔案中的主要密碼的問題。 在這些情況下應該有相關的郵件應用程式事件記錄檔中。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  

- 檢查應用程式事件記錄檔相關聯的事件或錯誤。  

- 檢查您具備適當的 SSO 系統管理員權限。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何產生主要密碼](../core/how-to-generate-the-master-secret.md)  

- [管理主要密碼](../core/managing-the-master-secret.md)
