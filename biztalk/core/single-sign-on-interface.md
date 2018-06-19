---
title: 單一登入介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2e3c2d3-a7e9-4a45-965d-bfe4bf200c34
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee479a29a424228b31bc3fcd5752f8da7cc3ce28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276790"
---
# <a name="single-sign-on-interface"></a><span data-ttu-id="6ec4a-102">單一登入介面</span><span class="sxs-lookup"><span data-stu-id="6ec4a-102">Single Sign-On Interface</span></span>

## <a name="interfaces"></a><span data-ttu-id="6ec4a-103">介面</span><span class="sxs-lookup"><span data-stu-id="6ec4a-103">Interfaces</span></span>
<span data-ttu-id="6ec4a-104">下表描述組成單一登入介面的 COM 和.NET Framework 介面。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-104">The following table describes the COM and .NET Framework interfaces that make up the Single Sign-On interface.</span></span>  
  
|<span data-ttu-id="6ec4a-105">.NET</span><span class="sxs-lookup"><span data-stu-id="6ec4a-105">.NET</span></span>|<span data-ttu-id="6ec4a-106">COM</span><span class="sxs-lookup"><span data-stu-id="6ec4a-106">COM</span></span>|<span data-ttu-id="6ec4a-107">Description</span><span class="sxs-lookup"><span data-stu-id="6ec4a-107">Description</span></span>|  
|----------|---------|-----------------|  
|<span data-ttu-id="6ec4a-108">Microsoft.EnterpriseSingleSignOn.Interop.ISSOAdmin</span><span class="sxs-lookup"><span data-stu-id="6ec4a-108">Microsoft.EnterpriseSingleSignOn.Interop.ISSOAdmin</span></span>|<span data-ttu-id="6ec4a-109">ISSOAdmin 介面 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-109">ISSOAdmin Interface (COM)</span></span>|<span data-ttu-id="6ec4a-110">建立、更新和刪除 SSO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-110">Creates, updates, and deletes an SSO application.</span></span> <span data-ttu-id="6ec4a-111">也會執行其他的管理功能。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-111">Also performs other administration functions.</span></span>|  
|<span data-ttu-id="6ec4a-112">Microsoft.EnterpriseSingleSignOn.Interop.ISSOConfigStore</span><span class="sxs-lookup"><span data-stu-id="6ec4a-112">Microsoft.EnterpriseSingleSignOn.Interop.ISSOConfigStore</span></span>|<span data-ttu-id="6ec4a-113">ISSOConfigStore 介面 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-113">ISSOConfigStore Interface (COM)</span></span>|<span data-ttu-id="6ec4a-114">取得和設定 SSO 組態存放區中的資訊。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-114">Gets and sets information in the SSO configuration store.</span></span>|  
|<span data-ttu-id="6ec4a-115">Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup1</span><span class="sxs-lookup"><span data-stu-id="6ec4a-115">Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup1</span></span>|<span data-ttu-id="6ec4a-116">ISSOLookup1 介面 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-116">ISSOLookup1 Interface (COM)</span></span>|<span data-ttu-id="6ec4a-117">可讓您查詢目前使用者在指定應用程式上的外部認證。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-117">Enables you to look up the external credentials on a specified application for the current user.</span></span>|  
|<span data-ttu-id="6ec4a-118">Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup2</span><span class="sxs-lookup"><span data-stu-id="6ec4a-118">Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup2</span></span>|<span data-ttu-id="6ec4a-119">ISSOLookup2 介面 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-119">ISSOLookup2 Interface (COM)</span></span>|<span data-ttu-id="6ec4a-120">如上所示，還可讓您查詢指定的外部使用者的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-120">As above, but also enables you to look up the Windows credentials for a specified external user.</span></span>|  
|<span data-ttu-id="6ec4a-121">Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapper</span><span class="sxs-lookup"><span data-stu-id="6ec4a-121">Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapper</span></span>|<span data-ttu-id="6ec4a-122">ISSOMapper 介面 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-122">ISSOMapper Interface (COM)</span></span>|<span data-ttu-id="6ec4a-123">可讓您設定目前使用者在指定應用程式上的外部認證。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-123">Enables you to set the external credentials for the current user for a specified application.</span></span>|  
|<span data-ttu-id="6ec4a-124">Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapping</span><span class="sxs-lookup"><span data-stu-id="6ec4a-124">Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapping</span></span>|<span data-ttu-id="6ec4a-125">ISSOMapping 介面 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-125">ISSOMapping Interface (COM)</span></span>|<span data-ttu-id="6ec4a-126">建立和維護使用者與附屬應用程式之間的對應。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-126">Creates and maintains the mapping between users and affiliated applications.</span></span>|  
|<span data-ttu-id="6ec4a-127">Microsoft.EnterpriseSingleSignOn.Interop.ISSOTicket</span><span class="sxs-lookup"><span data-stu-id="6ec4a-127">Microsoft.EnterpriseSingleSignOn.Interop.ISSOTicket</span></span>|<span data-ttu-id="6ec4a-128">ISSOTicket 介面 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-128">ISSOTicket Interface (COM)</span></span>|<span data-ttu-id="6ec4a-129">建立包含適當的安全性資訊的票證。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-129">Creates the ticket that contains the appropriate security information.</span></span> <span data-ttu-id="6ec4a-130">然後會傳送此票證與來自應用程式的適當訊息。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-130">This ticket is then sent on with the appropriate message from your application.</span></span>|  


## <a name="password-sync-helper"></a><span data-ttu-id="6ec4a-131">密碼同步協助程式</span><span class="sxs-lookup"><span data-stu-id="6ec4a-131">Password Sync Helper</span></span>  
 <span data-ttu-id="6ec4a-132">此外，Host Integration Server 還支援「密碼同步協助程式」(PS 協助程式) 元件。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-132">In addition, Host Integration Server supports the Password Sync Helper (PS Helper) component.</span></span> <span data-ttu-id="6ec4a-133">在設計密碼同步元件時可以使用「PS 協助程式」。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-133">You can use PS Helper when you design password synchronization components.</span></span> <span data-ttu-id="6ec4a-134">下表描述「PS 協助程式」所公開的 COM 和 .NET Framework 介面。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-134">The following table describes the COM and .NET Framework interfaces exposed by PS Helper.</span></span>  
  
|<span data-ttu-id="6ec4a-135">.NET</span><span class="sxs-lookup"><span data-stu-id="6ec4a-135">.NET</span></span>|<span data-ttu-id="6ec4a-136">COM</span><span class="sxs-lookup"><span data-stu-id="6ec4a-136">COM</span></span>|<span data-ttu-id="6ec4a-137">Description</span><span class="sxs-lookup"><span data-stu-id="6ec4a-137">Description</span></span>|  
|----------|---------|-----------------|  
|<span data-ttu-id="6ec4a-138">Microsoft.EnterpriseSingleSignOn.Interop.ISSOPSWrapper</span><span class="sxs-lookup"><span data-stu-id="6ec4a-138">Microsoft.EnterpriseSingleSignOn.Interop.ISSOPSWrapper</span></span>|<span data-ttu-id="6ec4a-139">ISSONotification 介面 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-139">ISSONotification Interface (COM)</span></span>|<span data-ttu-id="6ec4a-140">處理非 Windows 作業系統的密碼變更。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-140">Handles password changes to and from non-Windows operating systems.</span></span>|  
||<span data-ttu-id="6ec4a-141">SExternalAccount 結構 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-141">SExternalAccount Structure (COM)</span></span>|<span data-ttu-id="6ec4a-142">描述外部帳戶。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-142">Describes an external account.</span></span>|  
||<span data-ttu-id="6ec4a-143">SPasswordChange 結構 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-143">SPasswordChange Structure (COM)</span></span>|<span data-ttu-id="6ec4a-144">描述密碼變更。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-144">Describes a password change.</span></span>|  
||<span data-ttu-id="6ec4a-145">SPasswordChangeComplete 結構 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-145">SPasswordChangeComplete Structure (COM)</span></span>|<span data-ttu-id="6ec4a-146">描述密碼變更完成。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-146">Describes the completion of a password change.</span></span>|  
||<span data-ttu-id="6ec4a-147">SStatus 結構 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-147">SStatus Structure (COM)</span></span>|<span data-ttu-id="6ec4a-148">描述錯誤或事件。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-148">Describes an error or event.</span></span>|  
||<span data-ttu-id="6ec4a-149">SAdapterInGroup 結構 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-149">SAdapterInGroup Structure (COM)</span></span>|<span data-ttu-id="6ec4a-150">描述指定群組中的配接器。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-150">Describes the adapters in a given group.</span></span>|  
||<span data-ttu-id="6ec4a-151">SAdapter 結構 (COM)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-151">SAdapter Structure (COM)</span></span>|<span data-ttu-id="6ec4a-152">描述特定的配接器。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-152">Describes a specific adapter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6ec4a-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ec4a-153">See also</span></span>
<span data-ttu-id="6ec4a-154">請參閱 SSO COM 物件[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="6ec4a-154">See the SSO COM objects [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 