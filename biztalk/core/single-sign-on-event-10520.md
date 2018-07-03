---
title: 單一登入： 事件 10520 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 91662072-d87c-4290-8afb-2143143ee858
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0721ae4d89ee05792f2189a0d6a6b2c5e4efdddb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011383"
---
# <a name="single-sign-on-event-10520"></a>單一登入： 事件 10520
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                       企業單一登入                                                        |
| 產品版本 |                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                       |
|    事件識別碼     |                                                                 10520                                                                  |
|  事件來源   |                                                                 ENTSSO                                                                 |
|    元件    |                                                                  N\A                                                                   |
|  符號名稱  |                                                          SSO_WARN_NO_SECRETS                                                           |
|  訊息文字   | 主要密碼伺服器的登錄中找不到任何祕密。 您可以使用 組態工具來產生或還原主要祕密。 |

## <a name="explanation"></a>說明  
 這個警告事件表示，任何祕密找不到主要密碼伺服器的登錄中。 SSO 主要祕密儲存在 SSO 主要祕密伺服器的登錄中加密。 兩個密碼通常都會保存在登錄中： 目前的主要祕密和先前的主要密碼。 密碼會識別使用 GUID （主要祕密識別碼）。 如果要求時的登錄中找不到指定的主要祕密，就會傳回此錯誤的程式碼。  

## <a name="user-action"></a>使用者動作  
 若要解決此 warnming，執行一或多個項目：  

- 確認主要密碼伺服器名稱正確且預期。  

- 如果正確，請檢查該主要密碼伺服器的登錄中的主要祕密。 主要祕密位於的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS （此金鑰是只能在 SSO 主要祕密伺服器上存在）。  

- 如果該索引鍵遺漏，則主要祕密不存在。 應該要有一或多個索引鍵下 SSOSS 命名為包含加密的金鑰的 Guid。 如果沒有這些然後主要祕密不存在。 主要祕密均具有 Guid （主要祕密識別碼） 讓這些 Guid （如果有的話） 應該符合所要求的祕密的主要祕密識別碼。 如果名為 Guid 的索引鍵，但它們不符合要求的主要祕密識別碼，則沒有 mixup 之間在登錄中的主要密碼和密碼是用來加密 SSO 資料庫 (SSODB) 中的資料。 可能需要在此情況下，還原不同的主要祕密或 SSODB 可能已從舊版的備份還原。 如果主要祕密根本不存在，然後可以使用 SSO 組態工具 （命令列或 MMC） 的表單已還原的備份，或可以產生新的祕密。 請注意，您通常只想来產生新的主要祕密，如果這是新的安裝，而且沒有任何現有的加密 SSO 資料庫中的資料。 第一次在初始設定期間通常會產生主要祕密。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [主要密碼伺服器](../core/master-secret-server.md)  

- [管理主要密碼](../core/managing-the-master-secret.md)  

- [設定 SSO](../core/configuring-sso.md)
