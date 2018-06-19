---
title: 使用此資料提供者與 SSIS siebel |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSIS
- SQL Server Integration Services
- Data Provider for Siebel, using with SSIS
ms.assetid: e72cecf2-6c05-4df7-8e6e-aff3a9df8b79
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0c46c1437d7eeedd56ee37b054f9f6eb6b72ada
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222206"
---
# <a name="use-the-data-provider-for-siebel-with-ssis"></a>Siebel 與 SSIS 中使用資料提供者
您可以使用[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) 以及 SQL Server Integration Services (SSIS) Siebel 系統的資料匯入至 SQL Server 資料庫資料表，一般檔案或其他相容的目的地類型。 具體來說，您可以建立的 SSIS 封裝，可以執行此資料匯入。  
  
 資料匯入到 SQL Server 資料庫，使用 SQL Server 匯入和匯出精靈，並提供 SELECT 查詢來指定要匯入資料。 查詢必須確認所支援的語意[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。 如需文法的 SELECT 查詢[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，請參閱[Siebel 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md)。  
  
> [!NOTE]
>  [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]不支援使用 SSIS 中使用 EXEC 陳述式。  
  
 您可以啟動 SQL Server 匯入和匯出精靈，從 SQL Server Management Studio 或 Visual Studio 中的整合服務專案。 本章節提供 SQL Server Management Studio 和 Visual Studio 介面從執行精靈的指示。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 SQL Server Management Studio 的 Siebel 資料匯入](../../adapters-and-accelerators/adapter-siebel/import-siebel-data-using-sql-server-management-studio.md)  
  
-   [使用 Visual Studio 的 Siebel 資料匯入](../../adapters-and-accelerators/adapter-siebel/import-siebel-data-using-visual-studio.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用.NET Framework Data Provider for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)