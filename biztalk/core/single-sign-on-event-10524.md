---
title: 單一登入： 事件 10524 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55e26da3-f67f-4f87-92e5-2f8765b19989
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f873dab5d4d5f00897e498e2bb88b6ae9a2f040
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009503"
---
# <a name="single-sign-on-event-10524"></a>單一登入： 事件 10524
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                  企業單一登入                                                                                  |
| 產品版本 |                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                  |
|    事件識別碼     |                                                                                            10524                                                                                            |
|  事件來源   |                                                                                           ENTSSO                                                                                            |
|    元件    |                                                                                             N\A                                                                                             |
|  符號名稱  |                                                                               SSO_ERROR_RESTORE_SECRET_FAILED                                                                               |
|  訊息文字   | 還原主要密碼失敗。%r<br /><br /> 檔案名稱: %1 %r<br /><br /> 目前的 MSID: %2 %r<br /><br /> 先前的 MSID: %3 %r<br /><br /> 用戶端使用者: %4 %r<br /><br /> 錯誤碼： %5 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示使用者嘗試從備份檔案還原主要祕密失敗。 這可能是因為權限 （您必須是 SSO 系統管理員還原主要祕密） 的問題或可能是因為檔案損毀的備份檔案。 在這些情況下應該有相關的郵件應用程式事件記錄檔中。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  

- 檢查應用程式事件記錄檔相關聯的事件或錯誤。  

- 檢查您具備適當的 SSO 系統管理員權限。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何還原主要密碼](../core/how-to-restore-the-master-secret.md)  

- [如何備份主要密碼](../core/how-to-back-up-the-master-secret.md)  

- [如何產生主要密碼](../core/how-to-generate-the-master-secret.md)
