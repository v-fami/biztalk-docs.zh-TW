---
title: BizTalk Adapter for SQL Server 概觀 |Microsoft Docs
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
ms.openlocfilehash: 12c9393504332da636de8b09cca0e76f4dfe0da6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983455"
---
# <a name="overview-of-biztalk-adapter-for-sql-server"></a>BizTalk Adapter for SQL Server 概觀
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開為 WCF 服務的 SQL Server 資料庫。 配接器用戶端可以交換使用配接器的 SOAP 訊息來執行 SQL Server 資料庫上的作業。 配接器會使用 SOAP 訊息，並使適當的 ADO.NET 呼叫，以執行此作業。 配接器會傳回至用戶端的 SOAP 訊息的形式從 SQL Server 資料庫的回應。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]表面的成品 （例如資料表、 檢視和程序） 的 SQL Server 資料庫中的中繼資料。  此中繼資料描述 Web 服務描述語言 (WSDL) 格式之 SOAP 訊息的結構。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]讓配接器用戶端擷取作業的中繼資料。 配接器也會產生程式設計方案程式設計可用的成品。 如需詳細資訊[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，並[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，請參閱[連接到使用 SQL 配接器的 Visual Studio 中的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md)。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 ADO.NET 與 SQL Server 資料庫進行通訊。 您可以使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以下列方式與 SQL Server 資料庫通訊：  
  
- 開發 BizTalk 應用程式。 如需詳細資訊，請參閱 <<c0> [ 開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)。  
  
- 使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型。 如需詳細資訊，請參閱 <<c0> [ 開發應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)。  
  
- 使用 WCF 通道模型。 如需詳細資訊，請參閱 <<c0> [ 使用 WCF 通道模型開發應用程式](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [配接器如何連接到 SQL Server？](https://msdn.microsoft.com/library/dd788114.aspx) 
  
-   [配接器介面的 SQL Server 中繼資料如何？](https://msdn.microsoft.com/library/dd787941.aspx)  
  
-  [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)  
  
-   [SQL 配接器支援哪些作業](../../adapters-and-accelerators/adapter-sql/what-operations-are-supported-by-the-sql-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)