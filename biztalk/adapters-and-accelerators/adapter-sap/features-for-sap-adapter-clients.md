---
title: SAP 配接器用戶端功能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic ports
- adapters, features
- XML data streaming
- performance counters
- adapters, support for dynamic ports in BizTalk Server
- adapters, support for message versioning
- adapters, support for XML data streaming
- adapters, support for performance counters
- adapters, support for configuring adapters using binding properties
ms.assetid: 9003c2c1-931d-405e-9a58-660032195af7
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6516ff99f599d02cdf27aa7c0c07752747749021
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217110"
---
# <a name="features-for-sap-adapter-clients"></a>SAP 配接器用戶端的功能
除了所有的主題所討論的功能[BizTalk adapter for mySAP Business Suite 的架構概觀](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)、[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也提供下列功能可用於配接器用戶端。  
  
-   **設定配接器使用的繫結屬性的支援**。 可以設定配接器用戶端[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]藉由指定特定繫結內容。 例如，用戶端可以設定配接器至配接器的連接集區中指定最大連接數目，藉由指定的值**MaxConnectionsPerSystem**繫結屬性。 如需詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
-   **支援 BizTalk Server 中的動態連接埠**。 透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]、[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。 如需詳細資訊，請參閱[設定動態連接埠](../../adapters-and-accelerators/adapter-sap/configure-dynamic-ports-in-the-sap-adapter.md)。
  
-   **訊息版本控制支援**。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]啟用不同的訊息結構描述的未來版本中支援的版本控制，從而支援訊息[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[訊息版本控制支援](../../adapters-and-accelerators/adapter-sap/message-versioning-support1.md)。  
  
    > [!NOTE]
    >  這項功能不提供與舊版配接器的回溯相容性。  
  
-   **對效能計數器支援**。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]以供配接器用戶端支援以 WCF 為基礎的效能計數器。 如需有關效能計數器的詳細資訊，請參閱[與 SAP 配接器使用效能計數器](../../adapters-and-accelerators/adapter-sap/use-performance-counters-with-the-sap-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk adapter for mySAP Business Suite 的架構概觀](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)