---
title: "傳統單一登入應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a49bdae7-215a-43fb-875e-f64abb37aef0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4396ecfab477fe1ae17b1abbb09ebf71c9bcb58c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="traditional-single-sign-on-applications"></a><span data-ttu-id="78c34-102">傳統單一登入應用程式</span><span class="sxs-lookup"><span data-stu-id="78c34-102">Traditional Single Sign-On Applications</span></span>
<span data-ttu-id="78c34-103">「單一登入」(SSO) 程式設計架構包含用以對應應用程式與使用者的對應元件、用以尋查特定用途之認證的尋查元件，以及用以執行管理工作的管理元件。</span><span class="sxs-lookup"><span data-stu-id="78c34-103">The Single Sign-On (SSO) programming architecture contains a mapping component to map between applications and users, a lookup component to look up credentials for a specified use, and an administration component to perform administrative tasks.</span></span> <span data-ttu-id="78c34-104">此外，SSO 也包含票證介面，以便應用程式可發出和贖回票證。</span><span class="sxs-lookup"><span data-stu-id="78c34-104">In addition, SSO also contains a ticketing interface so that your application can issue and redeem tickets.</span></span>  
  
## <a name="mapping"></a><span data-ttu-id="78c34-105">對應</span><span class="sxs-lookup"><span data-stu-id="78c34-105">Mapping</span></span>  
 <span data-ttu-id="78c34-106">對應是連結特定使用者與特定應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="78c34-106">Mapping is the process of linking a specified user with a specified application.</span></span> <span data-ttu-id="78c34-107">您可以對應分支機構應用程式與使用 `ISSOMapping`、`ISSOMapper` 和 `ISSOMapper2` 的使用者。</span><span class="sxs-lookup"><span data-stu-id="78c34-107">You can map between affiliate applications and users who are using `ISSOMapping`, `ISSOMapper`, and `ISSOMapper2`.</span></span> <span data-ttu-id="78c34-108">有了 `ISSOMapping`，您就可以建立、刪除、啟用和停用對應。</span><span class="sxs-lookup"><span data-stu-id="78c34-108">With `ISSOMapping`, you can create, delete, enable, and disable mappings.</span></span> <span data-ttu-id="78c34-109">有了 `ISSOMapper` 和 `ISSOMapper2`，您就可以取得和設定目前使用者的對應資料。</span><span class="sxs-lookup"><span data-stu-id="78c34-109">With `ISSOMapper`, and `ISSOMapper2`, you can get and set mapping data for the current user.</span></span>  
  
## <a name="lookup"></a><span data-ttu-id="78c34-110">查閱</span><span class="sxs-lookup"><span data-stu-id="78c34-110">Lookup</span></span>  
 <span data-ttu-id="78c34-111">「單一登入」程式設計介面的核心是尋查特定使用者之認證的能力。</span><span class="sxs-lookup"><span data-stu-id="78c34-111">The core of the Single Sign-On programming interface is the ability to look up credentials for specified users.</span></span> <span data-ttu-id="78c34-112">您可以使用 `ISSOLookup1` 和 `ISSOLookup2` 查詢認證。</span><span class="sxs-lookup"><span data-stu-id="78c34-112">You can look up credentials using `ISSOLookup1`, and `ISSOLookup2`.</span></span> <span data-ttu-id="78c34-113">`ISSOLookup1` 可讓使用者擷取自己的外部認證。</span><span class="sxs-lookup"><span data-stu-id="78c34-113">`ISSOLookup1`, enables the user to retrieve their own external credentials.</span></span> <span data-ttu-id="78c34-114">相較之下，`ISSOLookup2` 也可讓您為本機分支機構應用程式尋查遠端使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="78c34-114">In contrast, `ISSOLookup2` also enables you to look up the credentials of a remote user for a local affiliate application.</span></span> <span data-ttu-id="78c34-115">前者為傳統「單一登入」應用程式的必要項目，而後者則在撰寫主控件初始化的「單一登入」應用程式時十分有用。</span><span class="sxs-lookup"><span data-stu-id="78c34-115">The former is necessary for a traditional Single Sign-On application, whereas the latter is useful when you are writing a host-initiated Single Sign-On application.</span></span>  
  
## <a name="administration"></a><span data-ttu-id="78c34-116">系統管理</span><span class="sxs-lookup"><span data-stu-id="78c34-116">Administration</span></span>  
 <span data-ttu-id="78c34-117">您可以透過 `ISSOAdmin`、`ISSOAdmin2` 和 `ISSOConfigStore`，以程式設計的方式執行許多管理功能。</span><span class="sxs-lookup"><span data-stu-id="78c34-117">You can perform many of the administrative capabilities programmatically through `ISSOAdmin`, `ISSOAdmin2`, and `ISSOConfigStore`.</span></span> <span data-ttu-id="78c34-118">這類工作包括設定單一登入以及建立和描述要單一登入的應用程式。</span><span class="sxs-lookup"><span data-stu-id="78c34-118">Such tasks include configuring Single Sign-On and creating and describing an application to Single Sign-On.</span></span> <span data-ttu-id="78c34-119">您也可以使用 `ISSOConfigDB`、`ISSOConfigOM` 和 `ISSOConfigSS` 來建立及修改 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="78c34-119">You also can create and modify SSO databases using `ISSOConfigDB`, `ISSOConfigOM`, and `ISSOConfigSS`.</span></span> <span data-ttu-id="78c34-120">最後，您可以使用 `ISSOPSAdmin` 來管理密碼同步功能。</span><span class="sxs-lookup"><span data-stu-id="78c34-120">Finally, you can administer the password sync features using `ISSOPSAdmin`.</span></span>  
  
## <a name="communication-and-ticketing"></a><span data-ttu-id="78c34-121">通訊和票證</span><span class="sxs-lookup"><span data-stu-id="78c34-121">Communication and Ticketing</span></span>  
 <span data-ttu-id="78c34-122">您的應用程式極可能會發出訊息，以便您的使用者可以與遠端應用程式通訊。</span><span class="sxs-lookup"><span data-stu-id="78c34-122">Your application will most likely issue messages so that your user can communicate with a remote application.</span></span> <span data-ttu-id="78c34-123">若要更安全地與遠端應用程式通訊，您必須發出和贖回「單一登入」票證。</span><span class="sxs-lookup"><span data-stu-id="78c34-123">To communicate with a remote application more securely, you must issue and redeem a Single Sign-On ticket.</span></span> <span data-ttu-id="78c34-124">您也可以藉由程式設計的方式來發出和贖回票證。</span><span class="sxs-lookup"><span data-stu-id="78c34-124">You can also issue and redeem tickets programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c34-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78c34-125">See Also</span></span>  
 [<span data-ttu-id="78c34-126">單一登入應用程式</span><span class="sxs-lookup"><span data-stu-id="78c34-126">Single Sign-On Applications</span></span>](../core/single-sign-on-applications.md)