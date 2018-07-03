---
title: 單一登入： 事件 10742 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba62f878-ed12-421f-81ea-9285b2624fe9
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43595ad7a6817bd63e200a80ea90e23bd0245ceb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012991"
---
# <a name="single-sign-on-event-10742"></a><span data-ttu-id="34caf-102">單一登入： 事件 10742</span><span class="sxs-lookup"><span data-stu-id="34caf-102">Single Sign-On: Event 10742</span></span>
## <a name="details"></a><span data-ttu-id="34caf-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="34caf-103">Details</span></span>  

|                 |                                                                                                                                                                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="34caf-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="34caf-104">Product Name</span></span>   |                                                                                                                                         <span data-ttu-id="34caf-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="34caf-105">Enterprise Single Sign-On</span></span>                                                                                                                                          |
| <span data-ttu-id="34caf-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="34caf-106">Product Version</span></span> |                                                                                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                         |
|    <span data-ttu-id="34caf-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="34caf-107">Event ID</span></span>     |                                                                                                                                                   <span data-ttu-id="34caf-108">10742</span><span class="sxs-lookup"><span data-stu-id="34caf-108">10742</span></span>                                                                                                                                                    |
|  <span data-ttu-id="34caf-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="34caf-109">Event Source</span></span>   |                                                                                                                                                   <span data-ttu-id="34caf-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="34caf-110">ENTSSO</span></span>                                                                                                                                                   |
|    <span data-ttu-id="34caf-111">元件</span><span class="sxs-lookup"><span data-stu-id="34caf-111">Component</span></span>    |                                                                                                                                                    <span data-ttu-id="34caf-112">N\A</span><span class="sxs-lookup"><span data-stu-id="34caf-112">N\A</span></span>                                                                                                                                                     |
|  <span data-ttu-id="34caf-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="34caf-113">Symbolic Name</span></span>  |                                                                                                                                         <span data-ttu-id="34caf-114">SSO_WARN_NO_UPDATE_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="34caf-114">SSO_WARN_NO_UPDATE_ADAPTER</span></span>                                                                                                                                         |
|  <span data-ttu-id="34caf-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="34caf-115">Message Text</span></span>   | <span data-ttu-id="34caf-116">用戶端使用者必須是 SSO 系統管理員帳戶或應用程式系統管理員帳戶的成員，才能更新 adapter.%r</span><span class="sxs-lookup"><span data-stu-id="34caf-116">The client user must be a member of the SSO Administrators account or the Application Administrators account to update the adapter.%r</span></span><br /><br /> <span data-ttu-id="34caf-117">用戶端使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="34caf-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="34caf-118">SSO 系統管理員: %2 %r</span><span class="sxs-lookup"><span data-stu-id="34caf-118">SSO Administrators: %2%r</span></span><br /><br /> <span data-ttu-id="34caf-119">應用程式系統管理員: %3 %r</span><span class="sxs-lookup"><span data-stu-id="34caf-119">Application Administrators: %3%r</span></span><br /><br /> <span data-ttu-id="34caf-120">配接器: %4 %r</span><span class="sxs-lookup"><span data-stu-id="34caf-120">Adapter: %4%r</span></span><br /><br /> <span data-ttu-id="34caf-121">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="34caf-121">Error Code: %5</span></span> |

## <a name="explanation"></a><span data-ttu-id="34caf-122">說明</span><span class="sxs-lookup"><span data-stu-id="34caf-122">Explanation</span></span>  
 <span data-ttu-id="34caf-123">這個警告事件表示，嘗試更新指定的配接器，但因為使用的使用者帳戶不是 SSO 系統管理員帳戶或應用程式系統管理員帳戶的成員，所以無法完成。</span><span class="sxs-lookup"><span data-stu-id="34caf-123">This Warning event indicates that an attempt to update the specified adapter was made, but could not be completed because the user account used is not a member of the SSO Administrators account or the Application Administrators account.</span></span>  

## <a name="user-action"></a><span data-ttu-id="34caf-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="34caf-124">User Action</span></span>  
 <span data-ttu-id="34caf-125">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="34caf-125">To resolve this warning, do one or more of the following:</span></span>  

- <span data-ttu-id="34caf-126">將使用者帳戶新增至 SSO 系統管理員帳戶或應用程式系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="34caf-126">Add user account to the SSO Administrators account or the Application Administrators account.</span></span>  

- <span data-ttu-id="34caf-127">重試更新。</span><span class="sxs-lookup"><span data-stu-id="34caf-127">Retry update.</span></span>  

  <span data-ttu-id="34caf-128">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="34caf-128">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="34caf-129">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="34caf-129">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)
