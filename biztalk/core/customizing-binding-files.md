---
title: 自訂繫結檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, binding files
- binding files
- binding files, about binding files
- binding files, customizing
ms.assetid: 4714e6c2-4912-43aa-ba5a-0be06916a30a
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1534be96255084b963ed3883a1370af00f73b605
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238366"
---
# <a name="customizing-binding-files"></a><span data-ttu-id="eaffc-102">自訂繫結檔案</span><span class="sxs-lookup"><span data-stu-id="eaffc-102">Customizing Binding Files</span></span>
<span data-ttu-id="eaffc-103">繫結檔案是描述 BizTalk 管理資料庫中的成品，以及這些成品之間關係的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="eaffc-103">Binding files are XML files that describe artifacts in a BizTalk Management database and the relationship between these artifacts.</span></span> <span data-ttu-id="eaffc-104">繫結檔案有助於從一個 BizTalk 組態資料庫，將組態資訊匯出到另一個 BizTalk 組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="eaffc-104">Binding files are useful for exporting configuration information from one BizTalk configuration database and importing this information into another BizTalk configuration database.</span></span> <span data-ttu-id="eaffc-105">例如，開發人員可能會在開發環境中設計 BizTalk 解決方案及其相關成品，然後將這些成品匯出到繫結檔案，最後再將這些成品匯入到實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="eaffc-105">For example, a developer may design a BizTalk solution and its related artifacts in a development environment, then export these artifacts to a binding file and finally, import these artifacts into a production environment.</span></span> <span data-ttu-id="eaffc-106">您也可以使用繫結檔案來更新現有的組態。</span><span class="sxs-lookup"><span data-stu-id="eaffc-106">You can also use a binding file to update an existing configuration.</span></span> <span data-ttu-id="eaffc-107">例如，您可以使用繫結檔案，將在開發環境中所做的組態變更，套用到您的實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="eaffc-107">For example you can apply configuration changes made in a development environment to your production environment with a binding file.</span></span> <span data-ttu-id="eaffc-108">本主題會討論以繫結檔案更新現有組態時的考量、繫結檔案的結構，以及可在繫結檔案中設定的配接器特定組態屬性。</span><span class="sxs-lookup"><span data-stu-id="eaffc-108">This topic discusses considerations when updating an existing configuration with a binding file, the structure of a binding file, and adapter specific configuration properties that can be set in a binding file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eaffc-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="eaffc-109">In This Section</span></span>  
  
-   [<span data-ttu-id="eaffc-110">與繫結檔案更新現有的組態</span><span class="sxs-lookup"><span data-stu-id="eaffc-110">Updating an Existing Configuration with a Binding File</span></span>](../core/updating-an-existing-configuration-with-a-binding-file.md)  
  
-   [<span data-ttu-id="eaffc-111">繫結檔案的結構</span><span class="sxs-lookup"><span data-stu-id="eaffc-111">Structure of a Binding File</span></span>](../core/structure-of-a-binding-file.md)  
  
-   [<span data-ttu-id="eaffc-112">整合式的 BizTalk 配接器的組態屬性</span><span class="sxs-lookup"><span data-stu-id="eaffc-112">Configuration Properties for Integrated BizTalk Adapters</span></span>](../core/configuration-properties-for-integrated-biztalk-adapters.md)