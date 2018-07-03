---
title: 單一登入： 事件 10511 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98371982-0db5-4ae0-9f92-f05a58e23b83
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 828dab394e773f99b31ca23f19b2816ab8558a10
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992087"
---
# <a name="single-sign-on-event-10511"></a>單一登入： 事件 10511
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                   |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                     企業單一登入                                                     |
| 產品版本 |                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                     |
|    事件識別碼     |                                                               10511                                                               |
|  事件來源   |                                                              ENTSSO                                                               |
|    元件    |                                                                N\A                                                                |
|  符號名稱  |                                                         SSO_ERROR_NO_DSN                                                          |
|  訊息文字   | 在登錄中找不到 SQL Server 與 SSO 資料庫名稱。 您可以使用 SSO 管理工具來設定這些值。 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示 SQL Server 與 SSO 資料庫名稱不登錄中找到。 SSO 服務會需要這項資訊，讓它可以連線到 SSO 資料庫。 在設定期間在登錄中設定這項資訊。 這可能表示並未正確完成組態，或已完成設定後，已刪除的登錄項目。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  

- 如果您懷疑更多的設定失敗時，取消設定產品，然後再重新設定使用 「 組態 」 程式。  

- 或者您可以使用 SSO 命令列工具位於 SSO 安裝目錄，通常是 C:\Program Files\Common Files\Enterprise Single Sign-on ssoconfig.exe 來設定這些特定遺漏的登錄項目。 您的 SSO 安裝目錄可能會不同。 使用 **-setDB**選項可用來設定必要的 SQL Server 與 SSO 資料庫名稱。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)
