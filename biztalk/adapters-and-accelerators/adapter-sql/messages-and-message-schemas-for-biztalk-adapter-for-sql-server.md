---
title: "訊息與 BizTalk adapter for SQL Server 的訊息結構描述 |Microsoft 文件"
description: "BizTalk Server 的 SQL Server 配接器使用的訊息和資料類型的 XML 結構"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e95c6342-5420-4fb8-9b41-7c87d27b5b68
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b1e45f0a20500253e2ca831138a21efa24df3c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-sql-server"></a>訊息與 BizTalk adapter for SQL Server 的訊息結構描述

## <a name="overview"></a>概觀
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 它會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。 這些作業會叫用透過通道傳送 SOAP 訊息。 如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。  
  
 做為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會公開其作業和資料類型的中繼資料，以使用標準[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]機制。 本主題中的各節描述 XML 訊息的結構和資料型別[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [基本的 SQL Server 資料類型](../../adapters-and-accelerators/adapter-sql/basic-sql-server-data-types.md)  
  
-   [訊息結構描述，插入、 更新、 刪除和選取資料表和檢視表上的作業](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)  
  
-   [訊息結構描述的程序和函式](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md)  
  
-   [輪詢和 TypedPolling 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md)  
  
-   [查詢通知的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-query-notification.md)  
  
-   [複合操作的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)  
  
-   [ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/executenonquery-executereader-and-executescalar-message-schemas-in-sql.md)  
  
