---
title: "單一登入： 事件 10520 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91662072-d87c-4290-8afb-2143143ee858
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9349452d99518f210237c5e8dd0f945d1f92aa46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10520"></a>單一登入： 事件 10520
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10520|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_NO_SECRETS|  
|訊息文字|主要密碼伺服器的登錄中找不到任何密碼。 使用組態工具產生或還原主要密碼。|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示密碼找到主要密碼伺服器的登錄中。 SSO 主要密碼儲存在 SSO 主要密碼伺服器的登錄中加密。 兩個密碼通常都會保存在登錄中： 目前的主要密碼和先前的主要密碼。 密碼會識別使用的 GUID (主要密碼的 id)。 如果在要求時的登錄中找不到指定的主要密碼，就會傳回此錯誤碼。  
  
## <a name="user-action"></a>使用者動作  
 若要解決此 warnming，執行下列一或多個項目：  
  
-   檢查主要密碼伺服器名稱正確，且如預期。  
  
-   如果正確，請檢查確認主要密碼中已有該主要密碼伺服器的登錄。 主要密碼位於的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS （此索引鍵存在於只在 SSO 主要密碼伺服器）。  
  
-   如果該索引鍵遺漏，則主要密碼不存在。 應該要有一個或多個索引鍵下 SSOSS 命名為包含加密的金鑰的 Guid。 如果沒有這些然後主要密碼不存在。 主要密碼以 Guid (主要密碼的 id) 來識別讓這些 Guid （如果有的話） 應符合所要求之密碼的主要密碼識別碼。 如果有命名為 Guid 的索引鍵，但它們不符合要求的主要密碼識別碼，就 mixup 之間在登錄中的主要密碼和密碼是用來加密 SSO 資料庫 (SSODB) 中的資料。 可能需要在此情況下，還原不同的主要密碼或 SSODB 可能已從舊版的備份還原。 如果主要密碼根本不存在，然後可以使用 SSO 組態工具 （命令列或 MMC） 的表單還原的備份，或可以產生新的密碼。 請注意您平常只想来產生新的主要密碼，如果這是新的安裝，而且沒有任何現有的加密 SSO 資料庫中的資料。 第一次初始設定期間通常會產生主要密碼。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [主要密碼伺服器](../core/master-secret-server.md)  
  
-   [管理主要密碼](../core/managing-the-master-secret.md)  
  
-   [設定 SSO](../core/configuring-sso.md)