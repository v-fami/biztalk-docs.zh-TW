---
title: 配接器程式設計組態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e5fef6c-6928-42e7-9a1f-42b5bd769937
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e908b3ac79970b917e1e7964868b3b9d5bd852d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229982"
---
# <a name="adapter-programming-configuration"></a><span data-ttu-id="c5e5c-102">配接器程式設計組態</span><span class="sxs-lookup"><span data-stu-id="c5e5c-102">Adapter Programming Configuration</span></span>
<span data-ttu-id="c5e5c-103">每個密碼同步配接器類型都有不同的組態需求，取決於您將配接器設計用於何種非 Windows 系統而定。</span><span class="sxs-lookup"><span data-stu-id="c5e5c-103">Every type of password sync adapter has different configuration requirements, depending on what non-Windows system you design the adapter for.</span></span> <span data-ttu-id="c5e5c-104">像分支機構應用程式，您可以使用企業單一登入的組態存放區來集中及更安全地儲存組態屬性。</span><span class="sxs-lookup"><span data-stu-id="c5e5c-104">Like affiliate applications, you can use the Enterprise Single Sign-On configuration store to store configuration properties centrally and more securely.</span></span>  
  
 <span data-ttu-id="c5e5c-105">如同其他組態存放區應用程式，系統管理員可以使用「企業單一登入」管理使用者介面，找出並讀取描述配接器之組態屬性的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="c5e5c-105">As with other configuration store applications, an administrator can use the Enterprise Single Sign-On management user interface to locate and read an XML file that describes the configuration properties for your adapter.</span></span> <span data-ttu-id="c5e5c-106">管理工具利用 XML 檔案顯示屬性頁，為指定的配接器收集所需的屬性值。</span><span class="sxs-lookup"><span data-stu-id="c5e5c-106">The management tools use the XML file to render a property page to gather the required property values, for the specified adapter.</span></span> <span data-ttu-id="c5e5c-107">您也可以使用 ISSOConfigStore 將 XML 名稱/值組合載入到組態存放區或從其中讀取，或者您可以使用 SSOPS 工具。</span><span class="sxs-lookup"><span data-stu-id="c5e5c-107">You can also use ISSOConfigStore to load and read XML name/value combinations to and from the configuration store, or you can use the SSOPS tool.</span></span>  
  
 <span data-ttu-id="c5e5c-108">您也可以使用「企業單一登入」管理工具以啟用和停用配接器。</span><span class="sxs-lookup"><span data-stu-id="c5e5c-108">You can also use the Enterprise Single Sign-On administration tools to enable and disable an adapter.</span></span> <span data-ttu-id="c5e5c-109">在初始建立時，配接器為停用。</span><span class="sxs-lookup"><span data-stu-id="c5e5c-109">On initial creation, an adapter is disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e5c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5e5c-110">See Also</span></span>  
 [<span data-ttu-id="c5e5c-111">密碼同步配接器</span><span class="sxs-lookup"><span data-stu-id="c5e5c-111">Password Sync Adapters</span></span>](../core/password-sync-adapters.md)