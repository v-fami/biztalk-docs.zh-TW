---
title: 無法建立繫結組態項目進行編輯 |Microsoft Docs
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
ms.openlocfilehash: 98e58ec9966d0e0534d078fc5741f267bf02e735
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974335"
---
# <a name="unable-to-create-binding-configuration-element-for-editing"></a><span data-ttu-id="1d1f8-102">無法建立繫結組態項目進行編輯</span><span class="sxs-lookup"><span data-stu-id="1d1f8-102">Unable to create binding configuration element for editing</span></span>
## <a name="details"></a><span data-ttu-id="1d1f8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1d1f8-103">Details</span></span>  
  
|                 |                                                                                                                                      |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="1d1f8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1d1f8-104">Product Name</span></span>   |                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                          |
| <span data-ttu-id="1d1f8-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1d1f8-105">Product Version</span></span> |                                      [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                      |
|    <span data-ttu-id="1d1f8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1d1f8-106">Event ID</span></span>     |                                                                  <span data-ttu-id="1d1f8-107">0</span><span class="sxs-lookup"><span data-stu-id="1d1f8-107">0</span></span>                                                                   |
|  <span data-ttu-id="1d1f8-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1d1f8-108">Event Source</span></span>   |                                                                  <span data-ttu-id="1d1f8-109">0</span><span class="sxs-lookup"><span data-stu-id="1d1f8-109">0</span></span>                                                                   |
|    <span data-ttu-id="1d1f8-110">元件</span><span class="sxs-lookup"><span data-stu-id="1d1f8-110">Component</span></span>    |                                                                  <span data-ttu-id="1d1f8-111">0</span><span class="sxs-lookup"><span data-stu-id="1d1f8-111">0</span></span>                                                                   |
|  <span data-ttu-id="1d1f8-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1d1f8-112">Symbolic Name</span></span>  |                                                                  <span data-ttu-id="1d1f8-113">0</span><span class="sxs-lookup"><span data-stu-id="1d1f8-113">0</span></span>                                                                   |
|  <span data-ttu-id="1d1f8-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1d1f8-114">Message Text</span></span>   | <span data-ttu-id="1d1f8-115">無法建立繫結組態項目進行編輯。</span><span class="sxs-lookup"><span data-stu-id="1d1f8-115">Unable to create binding configuration element for editing.</span></span> <span data-ttu-id="1d1f8-116">請檢查 BindingType 和 BindingConfiguration 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1d1f8-116">Check the values of the BindingType and BindingConfiguration properties.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="1d1f8-117">說明</span><span class="sxs-lookup"><span data-stu-id="1d1f8-117">Explanation</span></span>  
 <span data-ttu-id="1d1f8-118">正在載入使用者介面中顯示的繫結項目時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1d1f8-118">There was an error loading a binding element for display in the user interface.</span></span> <span data-ttu-id="1d1f8-119">自訂繫結通常會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="1d1f8-119">This error often occurs with custom binding.</span></span> <span data-ttu-id="1d1f8-120">繫結項目遺漏可能在組態檔中，因此並不適用於繫結的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="1d1f8-120">The binding element is probably missing in the configuration file and is therefore not available on the drop-down list for binding.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1d1f8-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1d1f8-121">User Action</span></span>  
 <span data-ttu-id="1d1f8-122">檢查的值**BindingType**並**BindingConfiguration**屬性。</span><span class="sxs-lookup"><span data-stu-id="1d1f8-122">Check the values of the **BindingType** and **BindingConfiguration** properties.</span></span>  
  
 <span data-ttu-id="1d1f8-123">如需建立繫結組態項目詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="1d1f8-123">For further information on creating binding configuration elements, see the following resource:</span></span>  
  
-   [<span data-ttu-id="1d1f8-124">設定 WCF-NetMsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="1d1f8-124">Configuring the WCF-NetMsmq Adapter</span></span>](../core/configuring-the-wcf-netmsmq-adapter.md)