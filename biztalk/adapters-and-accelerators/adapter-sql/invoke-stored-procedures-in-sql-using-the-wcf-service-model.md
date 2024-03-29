---
title: 叫用預存程序，在 SQL 中使用 WCF 服務模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4edd2fac-0b54-4406-932e-e3044a66b2e6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05ce43db33101dfc3849743e8480e66a8fd76f53
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023292"
---
# <a name="invoke-stored-procedures-in-sql-using-the-wcf-service-model"></a>叫用預存程序，在 SQL 中使用 WCF 服務模型
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]探索預存程序做為配接器用戶端可以叫用 WCF 用戶端叫用預存程序上的作業。 根據預存程序傳回結果集的方式，配接器來分類為預存的程序：  
  
- **程序**。 叫用預存程序**程序**節點會傳回資料集的陣列。  
  
- **強型別程序**。 叫用預存程序**Strongly-Typed 程序**節點會傳回強型別結果集。  
  
  請注意，同一組連接到資料庫中的預存程序將會列在這兩**程序**並**Strongly-Typed 程序**節點。 根據您想要的結果集的類型，您必須叫用預存程序，從相關的節點。 如需有關如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援預存程序，請參閱[使用 BizTalk Server 的 SQL Server 中執行預存程序](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md)。  
  
  本節說明如何叫用預存程序，同時從**程序**並**Strongly-Typed 程序**使用 WCF 用戶端節點。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [Involk 弱型別中使用 WCF 服務模型的 SQL 預存程序](../../adapters-and-accelerators/adapter-sql/invoke-weakly-typed-stored-procedures-in-sql-using-the-wcf-service-model.md)  
  
-   [叫用強型別在 SQL 中使用 WCF 服務模型的預存程序](../../adapters-and-accelerators/adapter-sql/invoke-strongly-typed-stored-procedures-in-sql-using-wcf-service-model.md)  
  
## <a name="see-also"></a>另請參閱  
[使用 WCF 服務模型開發應用程式](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)