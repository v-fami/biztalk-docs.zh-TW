---
title: "訊息結構描述的輪詢 Operations1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c572c4ec-0a3f-42b8-bebd-40eb584438ad
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee61aa47a7f991c140e0c0659b67da658a11a7ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-polling-operations"></a>輪詢作業的訊息結構描述
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]呈現輪詢根據 Oracle E-business Suite 中的目標物件與相關的各種輸入的作業。 介面資料表、 介面檢視、 資料表和檢視表，而您可以有多個自訂輪詢作業 PL/SQL 應用程式開發介面、 函數和預存程序，會顯示單一的輪詢作業。  
  
 設定繫結屬性設定輪詢作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需有關這些繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 您設定**PollingStatement**內容繫結至指定的 SQL 陳述式、 預存程序、 函式或在封裝中的輪詢查詢的程序。 此查詢的結果集傳回做為資料輪詢作業中的程式碼時。  
  
## <a name="message-structure-for-the-polling-operations"></a>輪詢作業的訊息結構  
 下表顯示各種輪詢作業的 XML 訊息結構。  
  
> [!NOTE]
>  在資料表之後，請參閱實體描述。  
  
|作業|目標物件|XML 訊息|Description|  
|---------------|-------------------|-----------------|-----------------|  
|輪詢|介面資料表<br /><br /> 介面檢視<br /><br /> -資料表<br /><br /> 對檢視|`<?xml version="1.0" encoding="utf-8" ?>  <Poll xmlns="[Version]/[TargetObject]/[Schema]/[TargetObject_Name]">    <DATA>      <SelectRecord>        <Column1>[Value]</Column1>        <Column2>[Value]</Column2>        …        </SelectRecord>    </DATA> </Poll>`|例如，輪詢作業介面資料表上的 XML 訊息會，如下所示：<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <Poll xmlns="[Version]/InterfaceTables/[Schema]/[InterfaceTable_Name]">    <DATA>      <SelectRecord>        <Column1>[Value]</Column1>        <Column2>[Value]</Column2>        …        </SelectRecord>    </DATA> </Poll>`|  
|[CustomPollingOperation]|-PL/SQL 應用程式開發介面<br /><br /> -預存程序<br /><br /> 函式|**PL/SQL 應用程式開發介面**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/PollingPackageAPis/[Schema]/[PL/SQL API]">    <[CustomPollingOperation]Result>[Value]</[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **函數**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?> <[CustomPollingOperation] xmlns="[Version]/PollingFunctions/[Schema]">    <[CustomPollingOperation]Result>      <COL1>[Value]</COL1]>      <COL2>[Value]</COL2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **預存程序**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/PollingFunctions/[Schema]">    <[CustomPollingOperation]Result>      <PRM1>[Value]</PRM1>      <PRM2>[Value]</PRM2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`|輪詢作業中的結果集的結構取決於目標物件中的項目中的資料類型。|  
  
 實體描述：  
  
 [版本] = http://schemas.microsoft.com/OracleEBS/2008/05。  
  
 [CustomPollingOperation] = 自訂輪詢作業的名稱。  
  
 [Schema] = Oracle 結構描述名稱。 例如，SCOTT。  
  
 [PL/SQL API] = 自訂輪詢作業執行所在的 PL/SQL api 的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)