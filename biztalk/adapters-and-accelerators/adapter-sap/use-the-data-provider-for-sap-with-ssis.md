---
title: 使用此資料提供者適用於 SAP 與 SSIS |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, using with SSIS
- SSIS, Data Provider for SAP
ms.assetid: e8c50cc1-ac25-4993-9aee-7fd88268d65d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8459453e153626b6a79a5dc5f57ce041ba67d1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217342"
---
# <a name="use-the-data-provider-for-sap-with-ssis"></a>適用於 SAP 使用 SSIS 中使用資料提供者
您可以使用[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]以及 SQL Server 整合服務 (SSIS) 從 SAP 系統的資料匯入到 SQL Server 資料庫資料表，一般檔案或其他相容的目的地類型。 您可以建立的 SSIS 封裝，可以執行的 SAP 系統從匯入資料。  
  
 您必須使用 SQL Server 匯入和匯出精靈將資料匯入 SQL Server 資料庫。 您必須提供查詢，以指定要匯入資料。 您可以指定使用 SELECT 陳述式或 EXECQUERY 陳述式的查詢。 查詢必須確認所支援的語意[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。 如需文法的 SELECT 查詢[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[SAP 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。 如需有關 EXECQUERY 陳述式的文法[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[sap EXECQUERY 陳述式語法](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md)。  
  
 從 SQL Server Management Studio 或 Visual Studio 中的整合服務專案，您可以啟動 [SQL Server 匯入匯出精靈]。 本節提供在 Management Studio 和 Visual Studio 介面從執行精靈的指示。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 SQL Server Management Studio 匯入 SAP 資料](../../adapters-and-accelerators/adapter-sap/import-sap-data-using-sql-server-management-studio.md)  
  
-   [使用 Visual Studio 的 SAP 資料匯入](../../adapters-and-accelerators/adapter-sap/import-sap-data-using-visual-studio.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用.NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)