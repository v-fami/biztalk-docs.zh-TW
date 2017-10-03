---
title: "訊息與 BizTalk adapter for Oracle 資料庫的訊息結構描述 |Microsoft 文件"
description: "BizTalk Server 的 Oracle 資料庫配接器使用的訊息和資料類型的 XML 結構"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fee0a531-b1e6-4b99-bb79-45368c401395
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bda5ed06470e051dc1f0bdf4595a1539aab6e6bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-oracle-database"></a>訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫

## <a name="overview"></a>概觀
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 它會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。 這些作業會叫用透過通道傳送 SOAP 訊息。 如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。  
  
 做為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會公開其作業和資料類型的中繼資料，以使用標準[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]機制。 本主題中的各節描述 XML 訊息的結構和資料型別[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [基本的 Oracle 資料類型](../../adapters-and-accelerators/adapter-oracle-database/basic-oracle-data-types1.md)  
  
-   [訊息結構描述基本的插入、 更新、 刪除和選取資料表和檢視表上的作業](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)  
  
-   [特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md)  
  
-   [函數和程序的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)  
  
-   [REF CURSOR 的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md)  
  
-   [記錄類型的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md)  
  
-   [SQLEXECUTE 操作的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)  
  
-   [輪詢作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md)  
  
-   [複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)  
  
-   [通知作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-notification-operation1.md)  
  
