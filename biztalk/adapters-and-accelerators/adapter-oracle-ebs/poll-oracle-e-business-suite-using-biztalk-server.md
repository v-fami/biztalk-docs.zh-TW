---
title: "使用 BizTalk Server 輪詢 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a22b99a5-1715-4351-b0e0-6b8dcfacd9eb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9b5d0743d39dfcf6cbab7e1da20a8a3fb1382fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-e-business-suite-using-biztalk-server"></a>使用 BizTalk Server 輪詢 Oracle E-business Suite
您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]從 Oracle 資料庫接收輪詢訊息。 配接器會提供兩種輪詢 Oracle 資料庫：  
  
-   **使用 SELECT 陳述式**。 您可以指定簡單的 SELECT 陳述式，以輪詢 Oracle 資料庫。 配接器執行 SELECT 陳述式，以指定的間隔，並將結果傳回至配接器用戶端。  
  
-   **使用預存程序**。 您可以指定輪詢 Oracle 資料庫的預存程序。 配接器指定的間隔執行預存程序，並將結果傳回至配接器用戶端。  
  
 兩種方法中的主要差異是方式配接器用戶端指定配接器輪詢 Oracle 資料庫所使用的輪詢陳述式。 簡單的 SELECT 陳述式的第一個方法的輪詢陳述式時，預存程序方法的輪詢陳述式是執行預存程序的要求訊息。 配接器用戶端指定輪詢陳述式，兩種方法，如**PollingInput**繫結屬性。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
 此章節的主題提供如何輪詢使用 SELECT 陳述式和預存程序的指示。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [輪詢 Oracle E-business Suite 使用 SELECT 陳述式](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement.md)  
  
-   [輪詢 Oracle E-business Suite 使用預存程序](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-stored-procedures.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)