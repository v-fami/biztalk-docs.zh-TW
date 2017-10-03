---
title: "了解的架構和 WCF LOB Adapter SDK 的不同元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 293189be-61d7-44f4-8ba6-e5550516d9b4
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: feea57176512bb42306feb8b60a10a887a020145
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="understand-the-architecture-and-different-components-of-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="e5a84-102">了解 WCF LOB Adapter SDK 的不同元件與架構</span><span class="sxs-lookup"><span data-stu-id="e5a84-102">Understand the architecture and different components of the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="e5a84-103">閱讀有關[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]有助於了解不同的元件，與 WCF 的角色。</span><span class="sxs-lookup"><span data-stu-id="e5a84-103">Read about the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] to help understand the different components, and the role of WCF.</span></span>  

<span data-ttu-id="e5a84-104">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]工具和元件，提供一致的架構開發可重複使用、 豐富的中繼資料的特定業務系統的配接器的集合。</span><span class="sxs-lookup"><span data-stu-id="e5a84-104">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is a collection of tools and components that provide a consistent framework for developing reusable, metadata-rich adapters for line-of-business systems.</span></span> <span data-ttu-id="e5a84-105">配接器使用撰寫[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]當成自訂 WCF 繫結，且可以由 WCF 支援的用戶端。</span><span class="sxs-lookup"><span data-stu-id="e5a84-105">Adapters written using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] are surfaced as custom WCF bindings and can be consumed by a WCF-capable client.</span></span>  
  
## <a name="features-and-components-overview"></a><span data-ttu-id="e5a84-106">功能和元件概觀</span><span class="sxs-lookup"><span data-stu-id="e5a84-106">Features and components overview</span></span>
<span data-ttu-id="e5a84-107">[何謂 Windows Communication Foundation 線條的商務配接器 SDK](what-is-the-windows-communication-foundation-line-of-business-adapter-sdk.md)提供的 SDK，構成元件的功能概觀和描述的中繼資料、 連線管理，並且描述常見的 WCF 詞彙。</span><span class="sxs-lookup"><span data-stu-id="e5a84-107">[What Is the Windows Communication Foundation Line of Business Adapter SDK](what-is-the-windows-communication-foundation-line-of-business-adapter-sdk.md) provides an overview of the features and components that make up the SDK, and describes the metadata, connection management, and describes the common WCF terms.</span></span>

## <a name="role-of-wcf"></a><span data-ttu-id="e5a84-108">WCF 的角色</span><span class="sxs-lookup"><span data-stu-id="e5a84-108">Role of WCF</span></span>  
<span data-ttu-id="e5a84-109">[讀取 WCF LOB 配接器 SDK 如何使用 WCF](read-how-wcf-is-used-by-the-wcf-lob-adapter-sdk.md)說明 SDK 與 WCF 關聯性。</span><span class="sxs-lookup"><span data-stu-id="e5a84-109">[Read how WCF is used by the WCF LOB Adapter SDK](read-how-wcf-is-used-by-the-wcf-lob-adapter-sdk.md) explains the relationship with the SDK and WCF.</span></span>

## <a name="architecture-overview"></a><span data-ttu-id="e5a84-110">架構概觀</span><span class="sxs-lookup"><span data-stu-id="e5a84-110">Architecture Overview</span></span>  
<span data-ttu-id="e5a84-111">[架構概觀](architecture-overview-of-the-wcf-lob-adapter-sdk.md)descrbied 內部架構和 WCF LOB Adapter SDK 的主要元件。</span><span class="sxs-lookup"><span data-stu-id="e5a84-111">[Architecture overview ](architecture-overview-of-the-wcf-lob-adapter-sdk.md) descrbied the internal architecture and the main components of WCF LOB Adapter SDK.</span></span>
 
## <a name="connection-handler-metadata-custom-and-core-components"></a><span data-ttu-id="e5a84-112">連接、 處理常式、 中繼資料、 自訂和核心元件</span><span class="sxs-lookup"><span data-stu-id="e5a84-112">Connection, handler, metadata, custom, and core components</span></span>
<span data-ttu-id="e5a84-113">[WCF LOB Adapter SDK 的索引鍵元件](key-components-of-the-wcf-lob-adapter-sdk.md)說明這些不同元件。</span><span class="sxs-lookup"><span data-stu-id="e5a84-113">[Key Components of the WCF LOB Adapter SDK](key-components-of-the-wcf-lob-adapter-sdk.md) describes these different components.</span></span>

## <a name="biztalk-server-and-the-sdk"></a><span data-ttu-id="e5a84-114">BizTalk Server 和 SDK</span><span class="sxs-lookup"><span data-stu-id="e5a84-114">BizTalk Server and the SDK</span></span>  
[<span data-ttu-id="e5a84-115">BizTalk Adapter for Oracle 資料庫與 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="e5a84-115">BizTalk Adapter for Oracle Database and the WCF LOB Adapter SDK</span></span>](../adapter-oracle-database/architecture-overview-of-the-biztalk-adapter-for-oracle-database.md)   
  
## <a name="see-also"></a><span data-ttu-id="e5a84-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5a84-116">See Also</span></span>  
 [<span data-ttu-id="e5a84-117">BizTalk Server 使用者入門</span><span class="sxs-lookup"><span data-stu-id="e5a84-117">Getting started with BizTalk Server</span></span>](../../core/getting-started-with-biztalk-server.md)