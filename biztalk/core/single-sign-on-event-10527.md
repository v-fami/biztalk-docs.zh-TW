---
title: 單一登入： 事件 10527 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 40995ad8-9f74-4e96-863d-427e23025ba1
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac787d375e8ccc4c578c2450b7cc6128dd427483
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972991"
---
# <a name="single-sign-on-event-10527"></a>單一登入： 事件 10527
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                     |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                      企業單一登入                                                                                      |
| 產品版本 |                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                      |
|    事件識別碼     |                                                                                                10527                                                                                                |
|  事件來源   |                                                                                               ENTSSO                                                                                                |
|    元件    |                                                                                                  0                                                                                                  |
|  符號名稱  |                                                                                     SSO_ERROR_GET_SECRET_FAILED                                                                                     |
|  訊息文字   | 取得主要祕密 failed.%r 的要求<br /><br /> 祕密號碼: %1 %r<br /><br /> 用戶端使用者: %2 %r<br /><br /> 用戶端電腦: %3 %r<br /><br /> 追蹤識別碼: %4 %r<br /><br /> 錯誤碼： %5 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示取得主要祕密的要求已失敗。 在這些情況下應該有相關的郵件應用程式事件記錄檔中。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 檢查應用程式事件記錄檔相關聯的事件或錯誤。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何產生主要密碼](../core/how-to-generate-the-master-secret.md)  

- [管理主要密碼](../core/managing-the-master-secret.md)
