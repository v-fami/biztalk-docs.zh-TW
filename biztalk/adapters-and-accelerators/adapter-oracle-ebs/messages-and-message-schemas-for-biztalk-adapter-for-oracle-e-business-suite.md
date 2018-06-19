---
title: 訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite |Microsoft 文件
description: BizTalk Server 的 Oracle EBS 配接器使用的訊息和資料類型的 XML 結構
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4434b4d4-fbe0-4692-81a5-9883c9a77cf6
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9069e5bf83f323726da7c8b08b9f5cc7ca6ccd85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216198"
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite"></a>訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite

## <a name="overview"></a>概觀
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 它會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。 這些作業會叫用透過通道傳送 SOAP 訊息。 如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。  
  
 做為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會公開其作業和資料類型的中繼資料，以使用標準[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]機制。 本主題中的各節描述 XML 訊息的結構和資料型別[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [基本的 Oracle 資料類型](../../adapters-and-accelerators/adapter-oracle-ebs/basic-oracle-data-types2.md)  
  
-   [訊息結構描述，插入、 更新、 刪除和選取作業](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md)  
  
-   [訊息結構描述的預存程序、 函數和 PL/SQL 應用程式開發介面](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-stored-procedures-functions-and-pl-sql-apis.md)  
  
-   [並行程式的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-concurrent-programs.md)  
  
-   [要求的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-request-sets.md)  
  
-   [特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md)  
  
-   [輪詢作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-polling-operations1.md)  
  
-   [通知作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-notification-operation2.md)  
  
-   [ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/executenonquery-executereader-and-executescalar-message-schemas.md)  
  
-   [複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-composite-operation1.md)  
  