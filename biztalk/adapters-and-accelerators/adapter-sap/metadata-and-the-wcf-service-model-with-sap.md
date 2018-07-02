---
title: 中繼資料和 WCF 服務模型，使用 SAP |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1900cf66-a0d0-46f4-896b-7f6de3b51875
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e4a3ca75470192f2237cf67c6ac0312b150b46a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972831"
---
# <a name="metadata-and-the-wcf-service-model-with-sap"></a><span data-ttu-id="05040-102">中繼資料和 WCF 服務模型，使用 SAP</span><span class="sxs-lookup"><span data-stu-id="05040-102">Metadata and the WCF Service Model with SAP</span></span>
<span data-ttu-id="05040-103">在 WCF 服務模型中，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutile.exe) 來產生 proxy 類別讓您的程式碼可以：</span><span class="sxs-lookup"><span data-stu-id="05040-103">In the WCF service model, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].or the ServiceModel Metadata Utility Tool (svcutile.exe) to generate proxy classes through which your code can either:</span></span>  
  
- <span data-ttu-id="05040-104">配接器 （WCF 用戶端類別） 上叫用作業</span><span class="sxs-lookup"><span data-stu-id="05040-104">Invoke operations on the adapter (a WCF client class)</span></span>  
  
- <span data-ttu-id="05040-105">接收配接器 （WCF 服務合約） 中的作業</span><span class="sxs-lookup"><span data-stu-id="05040-105">Receive operations from the adapter (a WCF service contract)</span></span>  
  
  <span data-ttu-id="05040-106">這些工具會產生代表服務合約為目標的作業 （以及支援的訊息合約、 作業合約和資料合約） 的.NET 類別所公開的中繼資料從[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="05040-106">These tools generate .NET classes that represent a service contract for target operations (as well as the supporting message contracts, operation contracts, and data contracts) from the metadata exposed by the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span> <span data-ttu-id="05040-107">如需了解產生的程式碼結構的說明，請參閱 <<c0> [ 了解產生的用戶端程式碼](https://msdn.microsoft.com/library/ms733881.aspx)。</span><span class="sxs-lookup"><span data-stu-id="05040-107">For help in understanding the structure of this generated code, see [Understanding Generated Client Code](https://msdn.microsoft.com/library/ms733881.aspx).</span></span> <span data-ttu-id="05040-108">本主題會具體描述，svcutil.exe 會產生，但其內容也會適用於程式碼的程式碼，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。</span><span class="sxs-lookup"><span data-stu-id="05040-108">This topic specifically describes code that svcutil.exe generates, but its content is also applicable to the code that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span> <span data-ttu-id="05040-109">如需如何產生 WCF 用戶端類別或 WCF 服務合約 （介面） 為目標的作業，以及 svcutil.exe 之間差異的詳細資訊和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[產生適用於 SAP 的 WCF 用戶端或 WCF 服務合約方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="05040-109">For information about how to generate a WCF client class or WCF service contract (interface) for target operations and about the differences between svcutil.exe and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05040-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05040-110">See Also</span></span>  
[<span data-ttu-id="05040-111">開發使用 WCF 服務模型的 SAP 應用程式</span><span class="sxs-lookup"><span data-stu-id="05040-111">Develop SAP applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)