---
title: ResolverDictionary 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46deb8a0-0523-4a5c-ac6b-45c506de7a72
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2dfe0082ffc7f7b68c5c56811a28d5ccd20e93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294998"
---
# <a name="the-resolverdictionary-class"></a><span data-ttu-id="24aac-102">ResolverDictionary 類別</span><span class="sxs-lookup"><span data-stu-id="24aac-102">The ResolverDictionary Class</span></span>
<span data-ttu-id="24aac-103">**ResolverDictionary**類別是**字典**-基礎類別，可以儲存的執行個體**解析程式**類別做為**字串**名稱 /值組。</span><span class="sxs-lookup"><span data-stu-id="24aac-103">The **ResolverDictionary** class is a **Dictionary**-based class that can store instances of the **Resolver** class as **String** name/value pairs.</span></span> <span data-ttu-id="24aac-104">建立的執行個體時**ResolverDictionary**類別，您必須提供現有參考**字典**執行個體。</span><span class="sxs-lookup"><span data-stu-id="24aac-104">When creating instances of the **ResolverDictionary** class, you must provide a reference to an existing **Dictionary** instance.</span></span> <span data-ttu-id="24aac-105">**ResolverDictionary**類別提供資料的**解析程式**類別會使用執行執行階段解析時。</span><span class="sxs-lookup"><span data-stu-id="24aac-105">The **ResolverDictionary** class provides the data that the **Resolver** class uses when it performs run-time resolution.</span></span>  
  
 <span data-ttu-id="24aac-106">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]安裝程式安裝並註冊**Microsoft.Practices.ESB.Resolver.dll**具有組件**ResolverDictionary**在全域組件快取中的類別。</span><span class="sxs-lookup"><span data-stu-id="24aac-106">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] installer installs and registers the **Microsoft.Practices.ESB.Resolver.dll** assembly with the **ResolverDictionary** class in the global assembly cache.</span></span>  
  
 <span data-ttu-id="24aac-107">**ResolverDictionary**類別會公開其中一種方法和一個屬性：</span><span class="sxs-lookup"><span data-stu-id="24aac-107">The **ResolverDictionary** class exposes one method and one property:</span></span>  
  
-   <span data-ttu-id="24aac-108">**項目 (** 金鑰 **)**。</span><span class="sxs-lookup"><span data-stu-id="24aac-108">**Item(** key **)**.</span></span> <span data-ttu-id="24aac-109">這個方法會採用包含索引鍵名稱的字串值。</span><span class="sxs-lookup"><span data-stu-id="24aac-109">This method takes a string value that contains a key name.</span></span> <span data-ttu-id="24aac-110">如果，則傳回對應的字串值或空字串項目不存在於基礎**字典**執行個體。</span><span class="sxs-lookup"><span data-stu-id="24aac-110">It returns the corresponding string value or an empty string if the item does not exist in the underlying **Dictionary** instance.</span></span>  
  
-   <span data-ttu-id="24aac-111">**BaseDictionary**。</span><span class="sxs-lookup"><span data-stu-id="24aac-111">**BaseDictionary**.</span></span> <span data-ttu-id="24aac-112">這個屬性會傳回參考基礎**字典**執行個體。</span><span class="sxs-lookup"><span data-stu-id="24aac-112">This property returns a reference to the underlying **Dictionary** instance.</span></span>