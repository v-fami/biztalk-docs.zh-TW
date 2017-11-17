---
title: "解析程式類別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9ebd6c2-fd86-471a-bc50-b1b89f701fab
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1359bcbb9c6c918fc0ee6d5e67bacb8e3559c84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolver-class"></a><span data-ttu-id="59ebb-102">解析程式類別</span><span class="sxs-lookup"><span data-stu-id="59ebb-102">The Resolver Class</span></span>
<span data-ttu-id="59ebb-103">**解析程式**類別會公開 （expose） 的名稱/值組的簡單結構。</span><span class="sxs-lookup"><span data-stu-id="59ebb-103">The **Resolver** class is a simple structure that exposes a name/value pair.</span></span> <span data-ttu-id="59ebb-104">解析程式的 Web 服務會傳回這個類別的執行個體的泛型集合，從它的方法。</span><span class="sxs-lookup"><span data-stu-id="59ebb-104">The Resolver Web service returns a generic collection of instances of this class from its methods.</span></span>  
  
 <span data-ttu-id="59ebb-105">ESB 核心安裝程式安裝並註冊**Microsoft.Practices.ESB.Resolver.dll**與全域組件快取中的解析程式類別的組件。</span><span class="sxs-lookup"><span data-stu-id="59ebb-105">The ESB Core installer installs and registers the **Microsoft.Practices.ESB.Resolver.dll** assembly with Resolver class in the global assembly cache.</span></span>  
  
 <span data-ttu-id="59ebb-106">以字典為基礎名稱/值的使用方法的可輕鬆地在未來加入新項目釋出，並藉由避免包含不相關的屬性來解析方法和目前的解析程式類型而定，解析結果的大小降到最低。</span><span class="sxs-lookup"><span data-stu-id="59ebb-106">The use of a dictionary-based name/value approach makes it easier to add new items in future releases and minimizes the size of the resolution result by avoiding inclusion of non-relevant properties that depend on the resolution method and the current resolver type.</span></span>  
  
 <span data-ttu-id="59ebb-107">**解析程式**類別會公開兩個屬性：</span><span class="sxs-lookup"><span data-stu-id="59ebb-107">The **Resolver** class exposes two properties:</span></span>  
  
-   <span data-ttu-id="59ebb-108">**名稱**。</span><span class="sxs-lookup"><span data-stu-id="59ebb-108">**Name**.</span></span> <span data-ttu-id="59ebb-109">這是包含資訊之後已解決的連接字串所傳回的名稱/值組的名稱。</span><span class="sxs-lookup"><span data-stu-id="59ebb-109">This is the name of a name/value pair that contains information that is returned after a connection string is resolved.</span></span>  
  
-   <span data-ttu-id="59ebb-110">**值**。</span><span class="sxs-lookup"><span data-stu-id="59ebb-110">**Value**.</span></span> <span data-ttu-id="59ebb-111">這是對應名稱的名稱/值組的值。</span><span class="sxs-lookup"><span data-stu-id="59ebb-111">This is the value that corresponds to the name of the name/value pair.</span></span>