---
title: 中繼資料和 WCF 服務模型與 Oracle 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service model, metadata
- WCF client class
- WCF service contract
ms.assetid: b55cf4ed-c41a-4986-bbaf-88e80c32b01f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3b1c3eed2ab71282a50ccbb6709601aa69ca733
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973295"
---
# <a name="metadata-and-the-wcf-service-model-with-oracle-database"></a><span data-ttu-id="bae1f-102">中繼資料和 WCF 服務模型與 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="bae1f-102">Metadata and the WCF Service Model with Oracle Database</span></span>
<span data-ttu-id="bae1f-103">在 WCF 服務模型中，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutile.exe) 來產生 proxy 類別讓您的程式碼可以：</span><span class="sxs-lookup"><span data-stu-id="bae1f-103">In the WCF service model, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].or the ServiceModel Metadata Utility Tool (svcutile.exe) to generate proxy classes through which your code can either:</span></span>  
  
- <span data-ttu-id="bae1f-104">配接器 （WCF 用戶端類別） 上叫用作業</span><span class="sxs-lookup"><span data-stu-id="bae1f-104">Invoke operations on the adapter (a WCF client class)</span></span>  
  
- <span data-ttu-id="bae1f-105">接收配接器 （WCF 服務合約） 中的作業</span><span class="sxs-lookup"><span data-stu-id="bae1f-105">Receive operations from the adapter (a WCF service contract)</span></span>  
  
  <span data-ttu-id="bae1f-106">這些工具會產生代表服務合約為目標的作業 （以及支援的訊息合約、 作業合約和資料合約） 的.NET 類別所公開的中繼資料從[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bae1f-106">These tools generate .NET classes that represent a service contract for target operations (as well as the supporting message contracts, operation contracts, and data contracts) from the metadata exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="bae1f-107">如需了解這個產生的結構的說明程式碼，請參閱 < 了解產生用戶端程式碼 >，網址[ http://go.microsoft.com/fwlink/?LinkId=98365 ](http://go.microsoft.com/fwlink/?LinkId=98365)。</span><span class="sxs-lookup"><span data-stu-id="bae1f-107">For help in understanding the structure of this generated code, see "Understanding Generated Client Code" at [http://go.microsoft.com/fwlink/?LinkId=98365](http://go.microsoft.com/fwlink/?LinkId=98365).</span></span> <span data-ttu-id="bae1f-108">本主題會具體描述，svcutil.exe 會產生，但其內容也會適用於程式碼的程式碼，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。</span><span class="sxs-lookup"><span data-stu-id="bae1f-108">This topic specifically describes code that svcutil.exe generates, but its content is also applicable to the code that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span> <span data-ttu-id="bae1f-109">如需 svcutil.exe 之間的差異以及如何產生 WCF 用戶端類別或目標作業的 WCF 服務合約的相關資訊和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[Oracle 資料庫產生 WCF 用戶端或 WCF 服務合約方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="bae1f-109">For information about how to generate a WCF client class or WCF service contract for target operations and about the differences between svcutil.exe and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF Client or a WCF Service Contract for Oracle Database Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bae1f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bae1f-110">See Also</span></span>  
 [<span data-ttu-id="bae1f-111">使用 WCF 服務模型開發 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="bae1f-111">Develop Oracle Database Applications by Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)