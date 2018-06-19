---
title: 訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite |Microsoft 文件
description: MySAP 配接器的 BizTalk Server 使用的訊息和資料類型的 XML 結構
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75ea5c27-8297-47bf-bcfd-503870349189
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9db6ec6b0fbea7ce5c8f90158126d52cbc7530ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216342"
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite"></a>訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite

## <a name="overview"></a>概觀
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 它會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。 這些作業會叫用透過通道傳送 SOAP 訊息。 如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。  
  
 做為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會公開其作業和資料類型的中繼資料，以使用標準[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]機制。 本主題中的各節描述 XML 訊息的結構和資料型別[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [基本的 SAP 資料類型](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md)  
  
-   [自訂 Rfc 的資料類型對應](../../adapters-and-accelerators/adapter-sap/data-type-mapping-for-custom-rfcs.md)  
  
-   [IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)  
  
-   [訊息內容屬性，用於接收 Idoc](../../adapters-and-accelerators/adapter-sap/message-context-properties-for-receiving-idocs.md)  
  
-   [RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)  
  
-   [TRFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)  
  
-   [BAPI 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-bapi-operations.md)  
  
-   [特殊作業](../../adapters-and-accelerators/adapter-sap/special-operations.md)  
  
-   [訊息版本控制支援](../../adapters-and-accelerators/adapter-sap/message-versioning-support1.md)  
  
