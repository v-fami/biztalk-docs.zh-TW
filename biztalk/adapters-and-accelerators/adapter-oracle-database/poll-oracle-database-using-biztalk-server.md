---
title: "使用 BizTalk Server 輪詢 Oracle 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c3aef30-956d-4585-b2de-7eebb919fab5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2578d00518a9f1632e690e84db04426575619109
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-database-using-biztalk-server"></a>使用 BizTalk Server 輪詢 Oracle 資料庫
您可以設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]從 Oracle 資料庫接收輪詢訊息。 配接器會提供兩種輪詢 Oracle 資料庫：  
  
-   **使用 SELECT 陳述式**。 您可以指定要輪詢的資料表和檢視 Oracle 資料庫中的簡單 SELECT 陳述式。 配接器執行 SELECT 陳述式，以指定的間隔，並將結果傳回至配接器用戶端。  
  
-   **使用預存程序、 函數或程序或函式，在封裝內**。 您可以指定預存程序、 函數或程序或函式，以輪詢 Oracle 資料庫在封裝內。 配接器指定的間隔執行的要求訊息，並將結果傳回至配接器用戶端。  
  
 兩種方法中的主要差異是方式配接器用戶端指定配接器輪詢 Oracle 資料庫所使用的輪詢陳述式。 輪詢陳述式的第一種方法是簡單的 SELECT 陳述式，而另一種方法的輪詢陳述式是執行預存程序、 函數或程序或函式，在封裝內的要求訊息。 配接器用戶端指定輪詢陳述式，兩種方法，在**PollingStatement**繫結屬性。 如需繫結屬性的詳細資訊，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  
  
 此章節的主題提供如何輪詢使用 SELECT 陳述式和預存程序、 函數或程序的指示，或在封裝內函式。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 SELECT 陳述式的輪詢 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-the-select-statement.md)  
  
-   [使用預存程序、 函數或封裝的程序和函式的輪詢 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-db-using-stored-procedures-functions-or-packaged-procedures.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)