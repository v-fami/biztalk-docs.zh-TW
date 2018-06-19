---
title: 連接至 SAP 系統使用配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection URI
- adapters, connecting to an SAP system
- connection string
ms.assetid: d506a948-5f4a-420b-a404-508824683099
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75f8c4b8650b2c81b3b82bf520958646e20da380
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216894"
---
# <a name="connect-to-an-sap-system-using-the-adapter"></a>連接至 SAP 系統使用配接器
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]需要配接器用戶端提供的連接字串，稱為連接來連接到 SAP 系統的統一資源識別元 (URI)。 使用 連線 URI，配接器用戶端可以指定連線參數，以連接到外部系統。如需連線 URI 的詳細資訊，請參閱[建立連接至 SAP 系統](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md)。  
  
 請確定您遵循安全性指導方針建立與 SAP 系統的連線時。 如需安全性指導方針的詳細資訊，請參閱[保護您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)。
  
## <a name="how-many-connections-can-the-adapter-open-to-the-sap-system"></a>連線數目可以配接器開啟至 SAP 系統？  
 根據預設，SAP 系統可讓用戶端開啟 100 個連接至 SAP 系統。 不過，您可以設定環境變數執行 SAP 系統，以增加連線數目上限的電腦上。 如需詳細資訊，請參閱[疑難排解操作問題 SAP 配接器](../../adapters-and-accelerators/adapter-sap/troubleshoot-operational-issues-with-the-sap-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for mySAP Business Suite 的架構概觀](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)