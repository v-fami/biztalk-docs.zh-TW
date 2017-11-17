---
title: "解析器和配接器提供者架構延伸 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4d5e6f2-b3bc-46e2-b8f7-d7e271d4a8c0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6ab5caf03d113e313e00a74c11641058e86b886
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="extending-the-resolver-and-adapter-provider-framework"></a><span data-ttu-id="dc6b5-102">擴充解析器和配接器提供者架構</span><span class="sxs-lookup"><span data-stu-id="dc6b5-102">Extending the Resolver and Adapter Provider Framework</span></span>
<span data-ttu-id="dc6b5-103">解析器和配接器提供者架構提供支援端點解析轉換和路由，而且它也可以針對服務提供自訂中繼資料。</span><span class="sxs-lookup"><span data-stu-id="dc6b5-103">The Resolver and Adapter Provider Framework provides support for endpoint and transformation resolution and routing, and it can also provide custom metadata for services.</span></span> <span data-ttu-id="dc6b5-104">架構可以動態地解決端點，並設定輸出配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="dc6b5-104">The framework can dynamically resolve endpoints and set outbound adapter properties.</span></span> <span data-ttu-id="dc6b5-105">之後的解析程式元件會解析端點 （例如，若要查閱輸出的 URL 使用通用描述、 探索與整合 [UDDI]），配接器提供者元件設定的已註冊的 Microsoft BizTalk Server 配接器特定屬性。</span><span class="sxs-lookup"><span data-stu-id="dc6b5-105">After a resolver component resolves an endpoint (for example, using Universal Description, Discovery, and Integration [UDDI] to look up an outbound URL), an adapter provider component sets specific properties of registered Microsoft BizTalk Server adapters.</span></span>  
  
 <span data-ttu-id="dc6b5-106">有三個主要區域，您可以在其中擴充解析器和配接器提供者架構：</span><span class="sxs-lookup"><span data-stu-id="dc6b5-106">There are three main areas where you can extend the Resolver and Adapter Provider Framework:</span></span>  
  
-   [<span data-ttu-id="dc6b5-107">建立自訂的解析程式</span><span class="sxs-lookup"><span data-stu-id="dc6b5-107">Creating a Custom Resolver</span></span>](../esb-toolkit/creating-a-custom-resolver.md)  
  
-   [<span data-ttu-id="dc6b5-108">使用 Unity 容器中建立自訂的解析程式</span><span class="sxs-lookup"><span data-stu-id="dc6b5-108">Creating a Custom Resolver with a Unity Container</span></span>](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md)  
  
-   [<span data-ttu-id="dc6b5-109">建立自訂配接器提供者</span><span class="sxs-lookup"><span data-stu-id="dc6b5-109">Creating a Custom Adapter Provider</span></span>](../esb-toolkit/creating-a-custom-adapter-provider.md)