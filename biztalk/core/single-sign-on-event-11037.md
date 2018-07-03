---
title: 單一登入： 事件 11037 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b523ff56-112e-4798-97d2-b1b19e130ec7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ceec837a53d4cad3c236373a907497795efbd12a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998895"
---
# <a name="single-sign-on-event-11037"></a><span data-ttu-id="2f12b-102">單一登入： 事件 11037</span><span class="sxs-lookup"><span data-stu-id="2f12b-102">Single Sign-On: Event 11037</span></span>
## <a name="details"></a><span data-ttu-id="2f12b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2f12b-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                       |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="2f12b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2f12b-104">Product Name</span></span>   |                                                                                                               <span data-ttu-id="2f12b-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="2f12b-105">Enterprise Single Sign-On</span></span>                                                                                                               |
| <span data-ttu-id="2f12b-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="2f12b-106">Product Version</span></span> |                                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                               |
|    <span data-ttu-id="2f12b-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2f12b-107">Event ID</span></span>     |                                                                                                                         <span data-ttu-id="2f12b-108">11037</span><span class="sxs-lookup"><span data-stu-id="2f12b-108">11037</span></span>                                                                                                                         |
|  <span data-ttu-id="2f12b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2f12b-109">Event Source</span></span>   |                                                                                                                        <span data-ttu-id="2f12b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2f12b-110">ENTSSO</span></span>                                                                                                                         |
|    <span data-ttu-id="2f12b-111">元件</span><span class="sxs-lookup"><span data-stu-id="2f12b-111">Component</span></span>    |                                                                                                                          <span data-ttu-id="2f12b-112">不適用</span><span class="sxs-lookup"><span data-stu-id="2f12b-112">N/A</span></span>                                                                                                                          |
|  <span data-ttu-id="2f12b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2f12b-113">Symbolic Name</span></span>  |                                                                                                              <span data-ttu-id="2f12b-114">SSO_INFO_PS_MAPPING_INVALID</span><span class="sxs-lookup"><span data-stu-id="2f12b-114">SSO_INFO_PS_MAPPING_INVALID</span></span>                                                                                                              |
|  <span data-ttu-id="2f12b-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2f12b-115">Message Text</span></span>   | <span data-ttu-id="2f12b-116">外部密碼變更。</span><span class="sxs-lookup"><span data-stu-id="2f12b-116">External password change.</span></span> <span data-ttu-id="2f12b-117">因為對應不再有效，所以外部帳戶的密碼未變更。%r</span><span class="sxs-lookup"><span data-stu-id="2f12b-117">The password was not changed for the external account because the mapping is no longer valid.%r</span></span><br /><br /> <span data-ttu-id="2f12b-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="2f12b-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="2f12b-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="2f12b-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="2f12b-120">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="2f12b-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="2f12b-121">外部帳戶： %4</span><span class="sxs-lookup"><span data-stu-id="2f12b-121">External Account: %4</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="2f12b-122">說明</span><span class="sxs-lookup"><span data-stu-id="2f12b-122">Explanation</span></span>  
 <span data-ttu-id="2f12b-123">對應不再是應用程式使用者群組的一部分。</span><span class="sxs-lookup"><span data-stu-id="2f12b-123">The mapping is no longer a part of the Application Users group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2f12b-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2f12b-124">User Action</span></span>  
 <span data-ttu-id="2f12b-125">訊息列出外部帳戶和應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f12b-125">The message lists the name of the external account and application.</span></span> <span data-ttu-id="2f12b-126">您可以使用這項資訊來找出對應不再有效的原因。</span><span class="sxs-lookup"><span data-stu-id="2f12b-126">You can use this information to find out why the mapping is no longer valid.</span></span>