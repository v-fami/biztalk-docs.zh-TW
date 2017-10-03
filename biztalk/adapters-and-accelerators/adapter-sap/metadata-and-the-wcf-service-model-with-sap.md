---
title: "中繼資料和 WCF 服務與 SAP 模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1900cf66-a0d0-46f4-896b-7f6de3b51875
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f06cd33c0776df70e5ff2554d355915908012abb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-sap"></a><span data-ttu-id="35474-102">中繼資料和 WCF 服務模型，與 SAP</span><span class="sxs-lookup"><span data-stu-id="35474-102">Metadata and the WCF Service Model with SAP</span></span>
<span data-ttu-id="35474-103">在 WCF 服務模型中，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或者 ServiceModel Metadata Utility Tool (svcutile.exe) 來產生 proxy 類別，您的程式碼可以是：</span><span class="sxs-lookup"><span data-stu-id="35474-103">In the WCF service model, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].or the ServiceModel Metadata Utility Tool (svcutile.exe) to generate proxy classes through which your code can either:</span></span>  
  
-   <span data-ttu-id="35474-104">配接器 （WCF 用戶端類別） 上叫用作業</span><span class="sxs-lookup"><span data-stu-id="35474-104">Invoke operations on the adapter (a WCF client class)</span></span>  
  
-   <span data-ttu-id="35474-105">接收來自配接器 （WCF 服務合約） 的作業</span><span class="sxs-lookup"><span data-stu-id="35474-105">Receive operations from the adapter (a WCF service contract)</span></span>  
  
 <span data-ttu-id="35474-106">這些工具產生.NET 類別，代表目標作業 （以及支援訊息合約、 作業合約和資料合約） 的服務合約所公開的中繼資料從[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="35474-106">These tools generate .NET classes that represent a service contract for target operations (as well as the supporting message contracts, operation contracts, and data contracts) from the metadata exposed by the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span> <span data-ttu-id="35474-107">如需了解產生的程式碼的結構的說明，請參閱[了解產生的用戶端程式碼](https://msdn.microsoft.com/library/ms733881.aspx)。</span><span class="sxs-lookup"><span data-stu-id="35474-107">For help in understanding the structure of this generated code, see [Understanding Generated Client Code](https://msdn.microsoft.com/library/ms733881.aspx).</span></span> <span data-ttu-id="35474-108">本主題特別描述，svcutil.exe 會產生，但是其內容也適用於程式碼的程式碼，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。</span><span class="sxs-lookup"><span data-stu-id="35474-108">This topic specifically describes code that svcutil.exe generates, but its content is also applicable to the code that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span> <span data-ttu-id="35474-109">如需如何產生 WCF 用戶端類別或 WCF 服務合約 （介面） 的目標作業以及 svcutil.exe 之間差異的詳細資訊和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[適用於 SAP 產生 WCF 用戶端或 WCF 服務合約方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="35474-109">For information about how to generate a WCF client class or WCF service contract (interface) for target operations and about the differences between svcutil.exe and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35474-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35474-110">See Also</span></span>  
[<span data-ttu-id="35474-111">開發使用 WCF 服務模型的 SAP 應用程式</span><span class="sxs-lookup"><span data-stu-id="35474-111">Develop SAP applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)