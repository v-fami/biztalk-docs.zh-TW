---
title: 使用 BizTalk Server 輪詢 Oracle 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c3aef30-956d-4585-b2de-7eebb919fab5
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d819abc957eb46dc430befb01cbcae0b8b55ca48
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996095"
---
# <a name="poll-oracle-database-using-biztalk-server"></a>使用 BizTalk Server 輪詢 Oracle 資料庫
您可以設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]從 Oracle 資料庫接收以輪詢為基礎的訊息。 配接器會提供兩種輪詢 Oracle 資料庫：  
  
- **使用 SELECT 陳述式**。 您可以指定要輪詢的資料表和檢視 Oracle 資料庫中的簡單 SELECT 陳述式。 配接器執行 SELECT 陳述式，以指定的間隔，並將結果傳回至配接器用戶端。  
  
- **使用預存程序、 函數或程序或函式，在封裝內**。 您可以指定預存程序、 函數或程序或輪詢 Oracle 資料庫在封裝內的函式。 配接器會在指定的時間間隔執行的要求訊息，並將結果傳回至配接器用戶端。  
  
  中的兩種方法的主要差異是方式配接器用戶端指定用來輪詢 Oracle 資料庫的配接器輪詢陳述式。 輪詢陳述式的第一種方法是簡單的 SELECT 陳述式，而另一種方法的輪詢陳述式就會是執行預存程序、 函數或程序或函式，在封裝內的要求訊息。 配接器用戶端指定輪詢陳述式，針對任一方法，在**PollingStatement**繫結屬性。 如需有關繫結屬性的詳細資訊，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  
  
  在本節中的主題提供有關如何使用 SELECT 陳述式和預存程序、 函數或程序進行輪詢的指示，或在封裝內函式。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 SELECT 陳述式的輪詢 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-the-select-statement.md)  
  
-   [使用預存程序、 函數或封裝的程序和函式的輪詢 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-db-using-stored-procedures-functions-or-packaged-procedures.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)