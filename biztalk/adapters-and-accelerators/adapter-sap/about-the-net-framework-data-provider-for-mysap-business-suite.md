---
title: "關於.NET Framework Data Provider for mySAP Business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSIS
- EXEC query
- SELECT query
- SAPDiscoveredObjects.xml
- SQL Server Integration Services
- .NET Framework Data Provider for mySAP Business Suite
- Data Provider for SAP
- custom RFC
- Visual Studio DDEX plug-in
ms.assetid: 4832f789-c1d8-4c5d-a49d-b1da6b7d4bd4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf6b8a1657f0731fc09c4ebc1ef1fa99e0e6ae4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-net-framework-data-provider-for-mysap-business-suite"></a>關於.NET Framework Data Provider for mySAP Business Suite
本節提供有關資訊[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) 和它的功能。 如需有關如何使用指示[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[使用.NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)。  
  
> [!NOTE]
>  即使您選擇要安裝[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]一部分[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝中，您[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]為仍然不完整，直到您安裝的自訂 RFC，SAP 系統中。 如需有關如何安裝自訂 RFC 的指示，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。  
  
 您可以使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]如下：  
  
-   要寫入的 ADO.NET 用戶端連接至 SAP 系統。 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]會公開特定類別，可讓您與提供者介面。  
  
-   SAP 系統上執行 SELECT 查詢。 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]這項功能會使用自訂的 RFC。  
  
-   執行 SAP 系統上的執行作業。 您可以使用這項作業，在 SAP 系統上執行查詢。  
  
-   執行 SAP 系統上的 EXECQUERY 作業。 若要執行 SAP 系統中已定義的查詢，您可以使用這項作業。  
  
-   若要亦使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]DDEX 外掛程式介面資料表和函式模組從 SAP 系統。 從 SAP 系統探索到的物件名稱會寫入至組態檔，SAPDiscoveredObjects.xml。  
  
-   若要使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]與 SQL Server Integration Services (SSIS)。  
  
-   若要使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]與 SQL Server Reporting Services (SSRS)。  
  
 如需有關如何執行這些工作的詳細資訊，請參閱[使用.NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)。 如需有關自訂 RFC、 SAPDiscoveredObjects.xml 組態檔和相關聯的限制[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱下列連結。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SAP 中的提供者所使用的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/custom-rfcs-used-by-the-provider-in-sap.md)  
  
-   [關於 sap SAPDiscoveredObjects.xml 檔案](../../adapters-and-accelerators/adapter-sap/about-the-sapdiscoveredobjects-xml-file-in-sap.md)  
  
-   [.NET Framework Data Provider for mySAP Business Suite 的限制](../../adapters-and-accelerators/adapter-sap/limitations-of-the-net-framework-data-provider-for-mysap-business-suite.md)