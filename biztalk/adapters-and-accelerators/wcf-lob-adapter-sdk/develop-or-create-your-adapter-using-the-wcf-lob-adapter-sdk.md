---
title: 開發，或建立您的配接器使用 WCF LOB 配接器 SDK |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ca8c03a-1e4a-4077-b4cb-4e184b520bbb
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e7e4c76add25b53a8b3e32707c6a09b92636559
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224718"
---
# <a name="develop-or-create-your-adapter-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="46e6a-102">開發，或建立您的配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="46e6a-102">Develop or create your adapter using the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="46e6a-103">本章節包含資訊的開發人員要建立使用配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="46e6a-103">This section contains information for developers who are creating adapters using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="46e6a-104">一旦開發的配接器，它通常由.NET 或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]開發人員用來存取所要的目標特定業務系統中的作業和資料。</span><span class="sxs-lookup"><span data-stu-id="46e6a-104">Once the adapter has been developed, it is usually consumed by either .NET or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] developers as a way to access operations and data in a desired target line-of-business system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46e6a-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="46e6a-105">In This Section</span></span>  
  
-   [<span data-ttu-id="46e6a-106">使用 WCF LOB 配接器 SDK 開發最佳作法</span><span class="sxs-lookup"><span data-stu-id="46e6a-106">Development Best Practices using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="46e6a-107">使用 WCF LOB 配接器 SDK 中的 WSDL Proxy 命名空間</span><span class="sxs-lookup"><span data-stu-id="46e6a-107">Use namespaces with the WSDL-Proxy in the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/use-namespaces-with-the-wsdl-proxy-in-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="46e6a-108">描述與 WCF LOB 配接器 SDK 的 WSDL PortType 文件結構描述</span><span class="sxs-lookup"><span data-stu-id="46e6a-108">Describe the WSDL PortType Documentation Schema with the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/describe-the-wsdl-porttype-documentation-schema-with-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="46e6a-109">管理配接器使用 WCF LOB 配接器 SDK 進行版本控制</span><span class="sxs-lookup"><span data-stu-id="46e6a-109">Manage adapter versioning with the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/manage-adapter-versioning-with-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="46e6a-110">使用服務行為來輸入認證，與 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="46e6a-110">Use a Service Behavior to enter credentials with the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/use-a-service-behavior-to-enter-credentials-with-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="46e6a-111">公開介面卡設定為使用 WCF LOB Adapter SDK 的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="46e6a-111">Expose adapter settings as binding property using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="46e6a-112">瀏覽和搜尋的中繼資料使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="46e6a-112">Browse and Search Metadata using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/browse-and-search-metadata-using-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="46e6a-113">交易支援</span><span class="sxs-lookup"><span data-stu-id="46e6a-113">Transaction Support</span></span>](../../core/transaction-support.md)  
  
-   [<span data-ttu-id="46e6a-114">使用 WCF LOB Adapter SDK 的 IIS 中的配接器主機</span><span class="sxs-lookup"><span data-stu-id="46e6a-114">Host an adapter in IIS using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/host-an-adapter-in-iis-using-the-wcf-lob-adapter-sdk.md) 
  
-   [<span data-ttu-id="46e6a-115">使用建立使用 WCF LOB Adapter SDK 的配接器</span><span class="sxs-lookup"><span data-stu-id="46e6a-115">Consume an Adapter created using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)  
  
## <a name="see-also"></a><span data-ttu-id="46e6a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46e6a-116">See Also</span></span>  
 <span data-ttu-id="46e6a-117">[開始使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/get-started-with-the-with-the-wcf-lob-adapter-sdk.md) </span><span class="sxs-lookup"><span data-stu-id="46e6a-117">[Get started with the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/get-started-with-the-with-the-wcf-lob-adapter-sdk.md) </span></span>  
 [<span data-ttu-id="46e6a-118">WCF 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="46e6a-118">Troubleshooting the WCF Adapters</span></span>](../../core/troubleshooting-the-wcf-adapters.md)