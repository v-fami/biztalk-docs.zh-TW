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
# <a name="connect-to-an-sap-system-using-the-adapter"></a><span data-ttu-id="e2f59-102">連接至 SAP 系統使用配接器</span><span class="sxs-lookup"><span data-stu-id="e2f59-102">Connect to an SAP system using the adapter</span></span>
<span data-ttu-id="e2f59-103">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]需要配接器用戶端提供的連接字串，稱為連接來連接到 SAP 系統的統一資源識別元 (URI)。</span><span class="sxs-lookup"><span data-stu-id="e2f59-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] requires adapter clients to provide a connection string, called the connection Uniform Resource Identifier (URI) to connect to the SAP system.</span></span> <span data-ttu-id="e2f59-104">使用 連線 URI，配接器用戶端可以指定連線參數，以連接到外部系統。如需連線 URI 的詳細資訊，請參閱[建立連接至 SAP 系統](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="e2f59-104">With a connection URI, adapter clients can specify connection parameters to connect to an external system.For more information about the connection URI, see [Create a connection to the SAP system](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md).</span></span>  
  
 <span data-ttu-id="e2f59-105">請確定您遵循安全性指導方針建立與 SAP 系統的連線時。</span><span class="sxs-lookup"><span data-stu-id="e2f59-105">Make sure you comply with the security guidelines when establishing a connection with an SAP system.</span></span> <span data-ttu-id="e2f59-106">如需安全性指導方針的詳細資訊，請參閱[保護您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="e2f59-106">For more information about security guidelines, see [Secure your SAP applications](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md).</span></span>
  
## <a name="how-many-connections-can-the-adapter-open-to-the-sap-system"></a><span data-ttu-id="e2f59-107">連線數目可以配接器開啟至 SAP 系統？</span><span class="sxs-lookup"><span data-stu-id="e2f59-107">How Many Connections Can the Adapter Open to the SAP System?</span></span>  
 <span data-ttu-id="e2f59-108">根據預設，SAP 系統可讓用戶端開啟 100 個連接至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="e2f59-108">By default, the SAP system enables clients to open 100 connections to the SAP system.</span></span> <span data-ttu-id="e2f59-109">不過，您可以設定環境變數執行 SAP 系統，以增加連線數目上限的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e2f59-109">However, you can set an environment variable on the computer running the SAP system to increase the limit on the number of connections.</span></span> <span data-ttu-id="e2f59-110">如需詳細資訊，請參閱[疑難排解操作問題 SAP 配接器](../../adapters-and-accelerators/adapter-sap/troubleshoot-operational-issues-with-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e2f59-110">For more information, see [Troubleshoot Operational Issues with the SAP adapter](../../adapters-and-accelerators/adapter-sap/troubleshoot-operational-issues-with-the-sap-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f59-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2f59-111">See Also</span></span>  
 [<span data-ttu-id="e2f59-112">BizTalk Adapter for mySAP Business Suite 的架構概觀</span><span class="sxs-lookup"><span data-stu-id="e2f59-112">Architecture overview of the BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)