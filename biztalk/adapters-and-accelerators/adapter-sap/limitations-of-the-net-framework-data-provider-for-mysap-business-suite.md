---
title: .NET Framework Data Provider for mySAP Business Suite 的限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, limitations of
- .NET Framework Data Provider for mySAP Business Suite, limitations of
ms.assetid: 462e627d-41da-4456-bc62-e8cf7296f5b4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9efcf7fb18471c92c504e08df43482fbc64064d2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999815"
---
# <a name="limitations-of-the-net-framework-data-provider-for-mysap-business-suite"></a>.NET Framework Data Provider for mySAP Business Suite 的限制
下列已知的限制[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]):  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援連接到 SAP 系統，請使用安全網路連線 (SNC)。 如需 SNC 的詳細資訊，請參閱[SAP 系統與配接器之間的安全性](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md)。
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] Nepodporuje`DbType`或是`Size`的屬性`SAPParameter`。 相反地，當使用者指定的值時，才`SAPParameter`，值會在內部根據.NET 和 SAP 資料類型之間建立對應的.NET 資料類型轉換。  
  
- SAP 資料類型的欄位值允許的最大長度`CURR`， `DEC`，和`QUAN`是 29 位數。 雖然 SAP，這些資料型別值提供 31 上的芳鄰的原生，轉換成.NET decimal 資料類型會 29 位數限制的大小。  
  
- .NET 資料類型之間的對應限制`Double`並將 SAP`FLTP`資料型別可能會導致溢位錯誤，當從 SAP 系統的資料讀入的.NET 類型。 雖然.NET 型別可以代表雙精確度 64 位元數字值範圍從負 1.79769313486232e308 到正 1.79769313486232 e 308，SAP`FLTP`型別剖析[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不能超過 1.8446744073709552E + 19;有效限制`FLTP`型別是負的 1.8446744073709552E + 19 到正數 1.8446744073709552E + 19 的範圍。  
  
- 因為處理基礎的用戶端程式庫，逾時問題而[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援命令，並連接逾時。  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援非同步命令的行為。  
  
- SQL Server Integration Services (SSIS) 專案中，搭配使用時[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]無法擷取資料行包含值超過 8000 個字元的資料。 這是因為，據此 SSIS 限制：  
  
  -   不支援大於 4000 個字元，SSIS 變數中的值。  
  
  -   不支援大於 4000 個寬字元的值。  
  
  -   不支援大於 8000 個單一位元組字元的值。  
  
## <a name="see-also"></a>另請參閱  
 [關於 .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)