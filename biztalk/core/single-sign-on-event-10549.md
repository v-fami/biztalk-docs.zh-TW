---
title: 單一登入： 事件 10549 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a18eb63-700c-4f49-acc4-890abe2a00ff
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18a3b92192c7e7e4a0906bfd35e4069dd3481d45
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993439"
---
# <a name="single-sign-on-event-10549"></a>單一登入： 事件 10549
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                企業單一登入                                                                                 |
| 產品版本 |                                                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                |
|    事件識別碼     |                                                                                          10549                                                                                           |
|  事件來源   |                                                                                          ENTSSO                                                                                          |
|    元件    |                                                                                            CO                                                                                            |
|  符號名稱  |                                                                             SSO_ERROR_CREATE_DATABASE_FAILED                                                                             |
|  訊息文字   | 建立及初始化 SSO 資料庫失敗。%r<br /><br /> SQL Server 名稱: %1 %r<br /><br /> SSO 資料庫名稱: %2 %r<br /><br /> 用戶端使用者: %3 %r<br /><br /> 錯誤碼： %4 |

## <a name="explanation"></a>說明  
 此錯誤表示建立及初始化 SSO 資料庫失敗。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列：  

- 請檢查系統和應用程式事件記錄檔設定的相關聯的訊息。  

- 再次執行安裝程式。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [安裝 SSO](../core/installing-sso.md)
