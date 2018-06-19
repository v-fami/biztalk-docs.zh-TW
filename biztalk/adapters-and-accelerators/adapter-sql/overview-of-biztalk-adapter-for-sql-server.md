---
title: BizTalk Adapter for SQL Server 的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e46690e-d5c4-4d6b-b7a0-9a5adf4431cd
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40d0c1fd3ce3a9f07367b7cc75ffeeb98f84b119
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222742"
---
# <a name="overview-of-biztalk-adapter-for-sql-server"></a>BizTalk Adapter for SQL Server 的概觀
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開為 WCF 服務的 SQL Server 資料庫。 配接器用戶端可以交換 SOAP 訊息的配接器，以執行 SQL Server 資料庫上的作業。 配接器會使用 SOAP 訊息，並會適當 ADO.NET 呼叫，以執行此作業。 配接器會傳回回應從 SQL Server 資料庫中的 SOAP 訊息形式的用戶端。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]表面的成品 （例如資料表、 檢視和程序） 的 SQL Server 資料庫中的中繼資料。  此中繼資料描述之表單的 Web 服務描述語言 (WSDL) 中的 SOAP 訊息的結構。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]讓配接器用戶端擷取作業的中繼資料。 配接器也會產生可使用的程式設計成品程式設計方案中。 如需有關[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，請參閱[連接到使用 SQL 配接器的 Visual Studio 中的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md)。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 ADO.NET，與 SQL Server 資料庫通訊。 您可以使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以下列方式與 SQL Server 資料庫通訊：  
  
-   開發 BizTalk 應用程式。 如需詳細資訊，請參閱[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)。  
  
-   使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型。 如需詳細資訊，請參閱[開發應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)。  
  
-   使用 WCF 通道模型。 如需詳細資訊，請參閱[開發應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [配接器如何連接到 SQL Server？](https://msdn.microsoft.com/library/dd788114.aspx) 
  
-   [配接器介面的 SQL Server 中繼資料的運作方式](https://msdn.microsoft.com/library/dd787941.aspx)  
  
-  [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)  
  
-   [SQL 配接器支援哪些作業](../../adapters-and-accelerators/adapter-sql/what-operations-are-supported-by-the-sql-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
 [瞭解 BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)