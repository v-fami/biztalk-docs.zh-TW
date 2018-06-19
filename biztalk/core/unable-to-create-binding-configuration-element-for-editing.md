---
title: 無法建立繫結組態項目進行編輯 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71853662-5a4a-417e-8160-c93dbcbea336
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5c4387e0cb9287ecc4d491291fdfd1fa6b79ab9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286422"
---
# <a name="unable-to-create-binding-configuration-element-for-editing"></a><span data-ttu-id="43734-102">無法建立繫結組態項目進行編輯</span><span class="sxs-lookup"><span data-stu-id="43734-102">Unable to create binding configuration element for editing</span></span>
## <a name="details"></a><span data-ttu-id="43734-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="43734-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43734-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="43734-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="43734-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="43734-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="43734-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="43734-106">Event ID</span></span>|<span data-ttu-id="43734-107">0</span><span class="sxs-lookup"><span data-stu-id="43734-107">0</span></span>|  
|<span data-ttu-id="43734-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="43734-108">Event Source</span></span>|<span data-ttu-id="43734-109">0</span><span class="sxs-lookup"><span data-stu-id="43734-109">0</span></span>|  
|<span data-ttu-id="43734-110">元件</span><span class="sxs-lookup"><span data-stu-id="43734-110">Component</span></span>|<span data-ttu-id="43734-111">0</span><span class="sxs-lookup"><span data-stu-id="43734-111">0</span></span>|  
|<span data-ttu-id="43734-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="43734-112">Symbolic Name</span></span>|<span data-ttu-id="43734-113">0</span><span class="sxs-lookup"><span data-stu-id="43734-113">0</span></span>|  
|<span data-ttu-id="43734-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="43734-114">Message Text</span></span>|<span data-ttu-id="43734-115">無法建立繫結組態項目進行編輯。</span><span class="sxs-lookup"><span data-stu-id="43734-115">Unable to create binding configuration element for editing.</span></span> <span data-ttu-id="43734-116">請檢查 BindingType] 和 [BindingConfiguration 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="43734-116">Check the values of the BindingType and BindingConfiguration properties.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="43734-117">說明</span><span class="sxs-lookup"><span data-stu-id="43734-117">Explanation</span></span>  
 <span data-ttu-id="43734-118">載入使用者介面中顯示的資料繫結項目時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="43734-118">There was an error loading a binding element for display in the user interface.</span></span> <span data-ttu-id="43734-119">使用自訂繫結通常會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="43734-119">This error often occurs with custom binding.</span></span> <span data-ttu-id="43734-120">繫結項目可能遺失的組態檔中，因此並沒有出現在下拉式清單，以繫結。</span><span class="sxs-lookup"><span data-stu-id="43734-120">The binding element is probably missing in the configuration file and is therefore not available on the drop-down list for binding.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="43734-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="43734-121">User Action</span></span>  
 <span data-ttu-id="43734-122">檢查值**BindingType**和**BindingConfiguration**屬性。</span><span class="sxs-lookup"><span data-stu-id="43734-122">Check the values of the **BindingType** and **BindingConfiguration** properties.</span></span>  
  
 <span data-ttu-id="43734-123">如需建立繫結組態項目詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="43734-123">For further information on creating binding configuration elements, see the following resource:</span></span>  
  
-   [<span data-ttu-id="43734-124">設定 Wcf-netmsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="43734-124">Configuring the WCF-NetMsmq Adapter</span></span>](../core/configuring-the-wcf-netmsmq-adapter.md)