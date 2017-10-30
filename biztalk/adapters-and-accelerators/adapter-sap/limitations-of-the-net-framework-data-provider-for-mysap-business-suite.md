---
title: "限制的.NET Framework Data Provider for mySAP Business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, limitations of
- .NET Framework Data Provider for mySAP Business Suite, limitations of
ms.assetid: 462e627d-41da-4456-bc62-e8cf7296f5b4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fd4ad3a57e2b762a53582ceb77eb65f23a535fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-the-net-framework-data-provider-for-mysap-business-suite"></a>.NET Framework Data Provider for mySAP Business Suite 的限制
下列已知的限制[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]):  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援連接到 SAP 系統，使用安全網路連線 (SNC)。 如需 SNC 的詳細資訊，請參閱[SAP 系統與配接器之間的安全性](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md)。
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援`DbType`或`Size`屬性`SAPParameter`。 相反地，當使用者指定的值時，才`SAPParameter`，值會在內部轉換成根據.NET 和 SAP 資料類型之間建立對應的.NET 資料類型。  
  
-   允許的 SAP 資料類型的欄位值的最大長度`CURR`， `DEC`，和`QUAN`是 29 個位數。 雖然 SAP，這些資料型別值提供 31 位置的原生，但是.NET decimal 資料類型轉換成會施加 29 位數限制。  
  
-   .NET 資料類型之間的對應限制`Double`和 SAP`FLTP`資料型別可能會造成溢位錯誤，當從 SAP 系統的資料讀入的.NET 類型。 雖然.NET 類型可以表示成雙精度 64 位元數字值範圍是從負 1.79769313486232 e 308 到正 1.79769313486232 e 308，SAP`FLTP`類型剖析[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不能超過 1.8446744073709552E + 19;有效限制`FLTP`型別是負數 1.8446744073709552E + 到正數 1.8446744073709552E + 19 19 的範圍。  
  
-   由於處理基礎的用戶端程式庫，逾時問題[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援命令，並連接逾時。  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援非同步命令的行為。  
  
-   使用 SQL Server Integration Services (SSIS) 專案，使用時[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]無法擷取資料行包含的值超過 8000 個字元的資料。 這是因為，據此 SSIS 限制：  
  
    -   不支援大於 4000 個字元，SSIS 變數中的值。  
  
    -   不支援大於 4000 個寬字元的值。  
  
    -   不支援大於 8000 個單一位元組字元的值。  
  
## <a name="see-also"></a>另請參閱  
 [關於.NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)