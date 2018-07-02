---
title: 中繼資料和 WCF 服務模型與 Siebel |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, metadata
- metadata, and the WCF service model
ms.assetid: 3aca1835-fb9e-4841-a920-078da0b3fe76
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73fdf3b57756bb2dfc007e63f803bf17c29285ab
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976647"
---
# <a name="metadata-and-the-wcf-service-model-with-siebel"></a><span data-ttu-id="1d95c-102">中繼資料和 Siebel 與 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="1d95c-102">Metadata and the WCF Service Model with Siebel</span></span>
<span data-ttu-id="1d95c-103">在 WCF 服務模型中，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutile.exe) 來產生 proxy 類別，WCF 用戶端類別，透過其程式碼可以叫用作業上[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1d95c-103">In the WCF service model, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutile.exe) to generate a proxy class—the WCF client class—through which your code can invoke operations on the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span>  
  
 <span data-ttu-id="1d95c-104">這些工具會使用配接器所公開的中繼資料來產生：</span><span class="sxs-lookup"><span data-stu-id="1d95c-104">These tools use the metadata exposed by the adapter to generate:</span></span>  
  
- <span data-ttu-id="1d95c-105">表示目標作業的服務合約的註解式的.NET 介面。</span><span class="sxs-lookup"><span data-stu-id="1d95c-105">An annotated .NET interface that represents the service contract for target operations.</span></span> <span data-ttu-id="1d95c-106">這個介面會呼叫 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="1d95c-106">This interface is called the WCF service contract.</span></span>  
  
- <span data-ttu-id="1d95c-107">表示支援的訊息合約、 作業合約和服務合約的資料合約的註解的類別。</span><span class="sxs-lookup"><span data-stu-id="1d95c-107">Annotated classes that represent the supporting message contracts, operation contracts, and data contracts for the service contract.</span></span>  
  
- <span data-ttu-id="1d95c-108">WCF 用戶端類別，其方法可以用來叫用 WCF 服務合約所公開的服務方法 （作業）。</span><span class="sxs-lookup"><span data-stu-id="1d95c-108">A WCF client class whose methods can be used to invoke the service methods (operations) exposed by the WCF service contract.</span></span>  
  
  <span data-ttu-id="1d95c-109">如需了解這個產生的結構的說明程式碼，請參閱 < 了解產生用戶端程式碼 >，網址[ http://go.microsoft.com/fwlink/?LinkId=98365 ](http://go.microsoft.com/fwlink/?LinkId=98365)。</span><span class="sxs-lookup"><span data-stu-id="1d95c-109">For help in understanding the structure of this generated code, see "Understanding Generated Client Code" at [http://go.microsoft.com/fwlink/?LinkId=98365](http://go.microsoft.com/fwlink/?LinkId=98365).</span></span> <span data-ttu-id="1d95c-110">本主題會具體描述，svcutil.exe 會產生，但其內容也會適用於程式碼的程式碼，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。</span><span class="sxs-lookup"><span data-stu-id="1d95c-110">This topic specifically describes code that svcutil.exe generates, but its content is also applicable to the code that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span>  
  
  <span data-ttu-id="1d95c-111">如需如何產生 WCF 用戶端類別為目標的作業，以及 svcutil.exe 之間差異的詳細資訊和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[產生 WCF 用戶端或 Siebel 方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)</span><span class="sxs-lookup"><span data-stu-id="1d95c-111">For information about how to generate a WCF client class for target operations and about the differences between svcutil.exe and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF Client or a WCF service contract for for Siebel solution Artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d95c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d95c-112">See Also</span></span>  
 [<span data-ttu-id="1d95c-113">開發使用 WCF 服務模型的 Siebel 應用程式</span><span class="sxs-lookup"><span data-stu-id="1d95c-113">Develop Siebel applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)