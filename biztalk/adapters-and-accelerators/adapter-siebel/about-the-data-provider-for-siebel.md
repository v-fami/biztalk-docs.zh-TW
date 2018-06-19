---
title: Siebel 的資料提供者相關 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, overview
ms.assetid: 461fe4d8-75f2-49d5-9fc2-3baab4ccf13f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81cac425bf1671166b4f40cecae3e1a3aca1c8e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217758"
---
# <a name="about-the-data-provider-for-siebel"></a>有關 Siebel 的資料提供者
## <a name="overview"></a>概觀
[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]建置最上層的[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。 您可以使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]至：  
  
-   撰寫 ADO.NET 用戶端連接至 Siebel 系統。 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]會公開特定類別，可讓您與提供者介面。  
  
-   Siebel 商務元件上執行 SELECT 查詢
  
-   Siebel 商務服務上執行 EXEC 查詢
  
-   使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]搭配 SQL Server Integration Services (SSIS)
  
[使用.NET Framework Data Provider for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)位於資訊的絕佳資源：  
  
-   藉由擴充的 ADO.NET 介面[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]  
  
-   要連接至 Siebel 系統的連接字串  
  
-   SELECT 和 EXEC 陳述式語法  
  
-   使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]與 SSIS  
  
## <a name="limitations"></a>限制
下列已知的限制[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]:  
  
-   [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援別名的資料表名稱在 SELECT 子句中，但不是在 WHERE 子句。  
  
-   [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]無法建立資料表的資料行名稱中有特殊字元，"]"。 您可以藉由另一個右方括弧逸出特殊字元。 因此，您應該包括 「]]"而不是"]"。  
  
-   因為具有基礎 Siebel 用戶端應用程式開發介面，逾時處理的問題而[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]不支援命令，並連接逾時。  
  
-   [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]不支援非同步命令的行為。  
  
-   使用 SQL Server Integration Services (SSIS) 專案，使用時[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]無法擷取資料行包含的值超過 8000 個字元的資料。 這是因為，據此 SSIS 限制：  
  
    -   不支援大於 4000 個字元，SSIS 變數中的值。  
  
    -   不支援大於 4000 個寬字元的值。  
  
    -   不支援大於 8000 個單一位元組字元的值。  
  
-   EXEC 作業將無法正常運作時使用[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]與 SQL Server Integration Services (SSIS)。 因此，比方說，配接器用戶端將無法執行 Siebel 商務服務 (使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) 時使用 SSIS 中使用的資料提供者。 

## <a name="see-also"></a>另請參閱
[Siebel 配接器的限制](../../adapters-and-accelerators/adapter-siebel/limitations-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
[Siebel 配接器進行疑難排解](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)