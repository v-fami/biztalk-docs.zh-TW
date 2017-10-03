---
title: "如何建立密碼同步配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: caa5bd13-efd9-4544-b5df-17d01c6ac5d8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c47381cc1ed71788673602c1db7eec5b5ac049ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-password-sync-adapter"></a><span data-ttu-id="c75b1-102">如何建立密碼同步配接器</span><span class="sxs-lookup"><span data-stu-id="c75b1-102">How to Create a Password Sync Adapter</span></span>
<span data-ttu-id="c75b1-103">密碼同步 (PS) 配接器是一套應用軟體，它使用「密碼同步協助程式」(Password Sync Helper) 元件傳送往來於「企業單一登入」(SSO) 的通知。</span><span class="sxs-lookup"><span data-stu-id="c75b1-103">A password sync (PS) adapter is an application that uses the Password Sync Helper component to pass notifications to and from Enterprise Single Sign-On (SSO).</span></span> <span data-ttu-id="c75b1-104">請注意，雖然 PS 協助程式元件使用 COM 介面和 .NET Framework 介面，但您的配接器不一定要是 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="c75b1-104">Note that although the PS Helper component exposes a COM and a .NET Framework interface, your adapter does not necessarily have to be a COM component.</span></span> <span data-ttu-id="c75b1-105">您可以將配接器設計為獨立程序、COM+ 應用程式或 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="c75b1-105">You can design your adapter as a stand-alone process, a COM+ application, or a Windows service.</span></span>  
  
### <a name="to-create-a-password-sync-adapter"></a><span data-ttu-id="c75b1-106">若要建立密碼同步配接器</span><span class="sxs-lookup"><span data-stu-id="c75b1-106">To create a password sync adapter</span></span>  
  
1.  <span data-ttu-id="c75b1-107">通知企業單一登入服務 (ENTSSO)，您的提供者正在使用 `ISSOPSWrapper.InitializeAdapter`。</span><span class="sxs-lookup"><span data-stu-id="c75b1-107">Inform Enterprise Single Sign-On service (ENTSSO) that your provider is active using `ISSOPSWrapper.InitializeAdapter`.</span></span>  
  
     <span data-ttu-id="c75b1-108">`InitializeAdapter` 會通知 ENTSSO，表示目前有一個提供者 (通常與進行呼叫的提供者為同一個) 正在進行呼叫，因此該提供者會將密碼更新傳入及傳出系統。</span><span class="sxs-lookup"><span data-stu-id="c75b1-108">`InitializeAdapter` informs ENTSSO that a provider, usually the same provider that is making the call, is currently turned on, and therefore will be communicating password updates to and from the system.</span></span> <span data-ttu-id="c75b1-109">您也可以使用`InitializeAdapter`啟動群組介面卡等其他資源。</span><span class="sxs-lookup"><span data-stu-id="c75b1-109">You can also use `InitializeAdapter` to activate other resources such as group adapters.</span></span>  
  
2.  <span data-ttu-id="c75b1-110">使用 `ISSOPSWrapper.SendNotification` 傳送密碼更新到 ENTSSO。</span><span class="sxs-lookup"><span data-stu-id="c75b1-110">Send password updates to ENTSSO by using `ISSOPSWrapper.SendNotification`.</span></span>  
  
     <span data-ttu-id="c75b1-111">您必須決定從非 Windows 系統接收密碼更新的方式。</span><span class="sxs-lookup"><span data-stu-id="c75b1-111">You must determine how you receive password updates from your non-Windows system.</span></span> <span data-ttu-id="c75b1-112">接收更新之後，您可以使用 `SendNotification` 將資訊傳送到 ENTSSO。</span><span class="sxs-lookup"><span data-stu-id="c75b1-112">After you receive the update, you can pass the information on to ENTSSO using `SendNotification`.</span></span> <span data-ttu-id="c75b1-113">請注意，`SendNotification`不限於傳送密碼更新： 的架構`SendNotification`也可讓您傳送其他類型的通知。</span><span class="sxs-lookup"><span data-stu-id="c75b1-113">Note that `SendNotification` is not limited to sending password updates: the architecture of `SendNotification` also enables you to send other types of notifications.</span></span>  
  
3.  <span data-ttu-id="c75b1-114">使用 `ISSOPSWrapper.ReceiveNotification` 向 ENTSSO 要求密碼更新。</span><span class="sxs-lookup"><span data-stu-id="c75b1-114">Request password updates from ENTSSO by using `ISSOPSWrapper.ReceiveNotification`.</span></span>  
  
     <span data-ttu-id="c75b1-115">因為密碼同步配接器是一種提取技術 (Pull technology)，所以 ENTSSO 永遠都不會呼叫您的配接器。</span><span class="sxs-lookup"><span data-stu-id="c75b1-115">Because the password sync adapter is a pull technology, ENTSSO never calls your adapter.</span></span> <span data-ttu-id="c75b1-116">不過，您的配接器將定期呼叫 `ReceiveNotification`，以檢查是否有可用的密碼更新。</span><span class="sxs-lookup"><span data-stu-id="c75b1-116">Instead, your adapter periodically calls `ReceiveNotification` to see whether any password updates are available.</span></span> <span data-ttu-id="c75b1-117">您可以選擇設定 `ReceiveNotification` 上的 WAIT 旗標。</span><span class="sxs-lookup"><span data-stu-id="c75b1-117">You can choose to set the WAIT flag on `ReceiveNotification`.</span></span> <span data-ttu-id="c75b1-118">設定 WAIT 將會封鎖執行緒，直到有通知為止。</span><span class="sxs-lookup"><span data-stu-id="c75b1-118">Setting WAIT blocks the thread until a notification is available.</span></span>  
  
     <span data-ttu-id="c75b1-119">請注意，ENTSSO 會以純文字傳送密碼變更到您的配接器。</span><span class="sxs-lookup"><span data-stu-id="c75b1-119">Note that ENTSSO delivers a password change to your adapter in plain text.</span></span> <span data-ttu-id="c75b1-120">保護密碼資訊免於不當的洩漏將是配接器的責任。</span><span class="sxs-lookup"><span data-stu-id="c75b1-120">It is the responsibility of the adapter to protect that password information against incorrect disclosure.</span></span> <span data-ttu-id="c75b1-121">配接器也有責任保護自己免於其他無效來源的詐騙和攻擊，包括對「密碼同步協助程式」元件的詐騙。</span><span class="sxs-lookup"><span data-stu-id="c75b1-121">It is also the responsibility of the adapter to protect itself against spoofing or attacks from other invalid sources, including spoofing of the Password Sync Helper component.</span></span>  
  
     <span data-ttu-id="c75b1-122">在透過 `pReceiveNotification` 參數從 ENTSSO 接收密碼更新以後，您必須將此資訊傳送到您的非 Windows 系統。</span><span class="sxs-lookup"><span data-stu-id="c75b1-122">After you receive a password update from ENTSSO through the `pReceiveNotification` parameter, you must pass this information on to your non-Windows system.</span></span> <span data-ttu-id="c75b1-123">和 `SendNotification` 一樣，您必須決定與遠端伺服器通訊的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="c75b1-123">As with `SendNotification`, you must determine the best way to communicate with the remote server.</span></span>  
  
4.  <span data-ttu-id="c75b1-124">使用 `ISSOPSWrapper.ShutdownAdapter` 關閉配接器。</span><span class="sxs-lookup"><span data-stu-id="c75b1-124">Turn off your adapter using `ISSOPSWrapper.ShutdownAdapter`.</span></span>  
  
     <span data-ttu-id="c75b1-125">`ShutdownApplication` 應是配接器所呼叫的最後一個方法，它表示配接器將不再對 ENTSSO 傳送或接收密碼更新。</span><span class="sxs-lookup"><span data-stu-id="c75b1-125">`ShutdownApplication` should be the last method called by an adapter, and indicates that the adapter will no longer send or receive password updates to ENTSSO.</span></span>  
  
     <span data-ttu-id="c75b1-126">請注意，當配接器為關閉時，ENTSSO 會緩衝使用者所變更的密碼，直到達到緩衝區的大小限制。</span><span class="sxs-lookup"><span data-stu-id="c75b1-126">Note that ENTSSO buffers any password changes a user makes while the adapter is shut down, up to a buffer size limit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75b1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c75b1-127">See Also</span></span>  
 <span data-ttu-id="c75b1-128">[使用企業單一登入進行程式設計](../core/programming-with-enterprise-single-sign-on.md) </span><span class="sxs-lookup"><span data-stu-id="c75b1-128">[Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md) </span></span>  
 [<span data-ttu-id="c75b1-129">同步處理密碼</span><span class="sxs-lookup"><span data-stu-id="c75b1-129">Synchronizing Passwords</span></span>](../core/synchronizing-passwords.md)