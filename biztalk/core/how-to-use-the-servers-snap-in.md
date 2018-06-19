---
title: 如何使用伺服器嵌入式管理單元 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f520692-9606-41f5-98ed-5a4962bd1f09
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12eb72323a6dcd1132f03febc9b4d9bd75316c84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256558"
---
# <a name="how-to-use-the-servers-snap-in"></a><span data-ttu-id="023f2-102">如何使用伺服器嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="023f2-102">How to Use the Servers Snap-in</span></span>
<span data-ttu-id="023f2-103">此版本的「企業單一登入」(SSO) 包含 ENTSSO「伺服器嵌入式管理單元」，可讓您透過 Windows 介面對 ENTSSO 伺服器進行檢視、監控以及執行某些動作。</span><span class="sxs-lookup"><span data-stu-id="023f2-103">This version of Enterprise Single Sign-On (SSO) includes the ENTSSO Servers Snap-In, which allows you to view, monitor, and perform certain actions on your ENTSSO Server through the Windows interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="023f2-104">如果您的系統有防火牆，而且伺服器名稱使用 FQDN 格式，則您可能無法連線到伺服器。</span><span class="sxs-lookup"><span data-stu-id="023f2-104">If your system has a firewall and your server name uses the FQDN format, you may not be able to contact the server.</span></span> <span data-ttu-id="023f2-105">您必須改為指定 NetBIOS 名稱或相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="023f2-105">Instead, you must specify the NetBIOS name or the associated IP address.</span></span>  
  
### <a name="to-use-the-entsso-servers-snap-in"></a><span data-ttu-id="023f2-106">若要使用 ENTSSO 伺服器嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="023f2-106">To use the ENTSSO Servers Snap-In</span></span>  
  
1.  <span data-ttu-id="023f2-107">開啟 [企業單一登入]。</span><span class="sxs-lookup"><span data-stu-id="023f2-107">Open Enterprise Single Sign-On.</span></span>  
  
2.  <span data-ttu-id="023f2-108">在 [領域] 窗格中，按一下**伺服器**節點。</span><span class="sxs-lookup"><span data-stu-id="023f2-108">In the Scope pane, click the **Servers** node.</span></span>  
  
     <span data-ttu-id="023f2-109">[結果] 窗格隨即顯示下列資訊。</span><span class="sxs-lookup"><span data-stu-id="023f2-109">The following information is displayed in the Results pane.</span></span>  
  
    -   <span data-ttu-id="023f2-110">**名稱**： 指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="023f2-110">**Name**: Name specified.</span></span>  
  
    -   <span data-ttu-id="023f2-111">**狀態**: ENTSSO 服務 （線上、 離線，暫止狀態，啟動、 停止、 開始擱置、 停止擱置） 的狀態。</span><span class="sxs-lookup"><span data-stu-id="023f2-111">**Status**: Status of the ENTSSO service (Online, Offline, Pending, Started, Stopped, Start Pending, Stop Pending).</span></span>  
  
    -   <span data-ttu-id="023f2-112">**日期**： 取得資訊的日期。</span><span class="sxs-lookup"><span data-stu-id="023f2-112">**Date**: Date when information was obtained.</span></span>  
  
    -   <span data-ttu-id="023f2-113">**時間**： 取得資訊的時間。</span><span class="sxs-lookup"><span data-stu-id="023f2-113">**Time**: Time when information was obtained.</span></span>  
  
    -   <span data-ttu-id="023f2-114">**SSO 伺服器**： 伺服器的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="023f2-114">**SSO Server**: Fully qualified name of server.</span></span>  
  
    -   <span data-ttu-id="023f2-115">**服務帳戶**: ENTSSO 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="023f2-115">**Service Account**: ENTSSO service account.</span></span>  
  
    -   <span data-ttu-id="023f2-116">**SSO 資料庫**： 與此伺服器進行通訊的 ENTSSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="023f2-116">**SSO Database**: ENTSSO Database with which this server is communicating.</span></span>  
  
    -   <span data-ttu-id="023f2-117">**密碼伺服器**： 指出是否正在執行的密碼伺服器模組。</span><span class="sxs-lookup"><span data-stu-id="023f2-117">**Secret Server**: Indicates whether the Secret Server module is running.</span></span>  
  
    -   <span data-ttu-id="023f2-118">**密碼同步**： 指出是否已安裝密碼同步處理。</span><span class="sxs-lookup"><span data-stu-id="023f2-118">**Password Sync**: Indicates whether Password Sync is installed.</span></span>  
  
    -   <span data-ttu-id="023f2-119">**電腦**： 電腦的 NETBIOS 名稱。</span><span class="sxs-lookup"><span data-stu-id="023f2-119">**Computer**: NETBIOS name of computer.</span></span>  
  
    -   <span data-ttu-id="023f2-120">**事件會計算**： 資訊/警告/錯誤事件計數。</span><span class="sxs-lookup"><span data-stu-id="023f2-120">**Event counts**: Info/Warning/Errors event count.</span></span> <span data-ttu-id="023f2-121">重設此欄位會使計數器從 0 開始。</span><span class="sxs-lookup"><span data-stu-id="023f2-121">Resetting this will start the counter from 0.</span></span>  
  
    -   <span data-ttu-id="023f2-122">**安裝的 SSO 版本**: ENTSSO.exe 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="023f2-122">**Version of SSO installed**: Version number of ENTSSO.exe.</span></span> <span data-ttu-id="023f2-123">此項資訊也會指出這是 32 位元 (x86) 或 64 位元 (x64)。</span><span class="sxs-lookup"><span data-stu-id="023f2-123">Also indicates whether this is 32-bit (x86) or 64-bit (x64).</span></span>  
  
### <a name="to-start-or-stop-the-server-service"></a><span data-ttu-id="023f2-124">若要啟動或停止伺服器服務</span><span class="sxs-lookup"><span data-stu-id="023f2-124">To start or stop the server service</span></span>  
  
-   <span data-ttu-id="023f2-125">在 ENTSSO 伺服器嵌入式管理單元，以滑鼠右鍵按一下伺服器，然後按一下**啟動**或**停止**。</span><span class="sxs-lookup"><span data-stu-id="023f2-125">In the ENTSSO Servers Snap-In, right-click the server and click **Start** or **Stop**.</span></span>  
  
### <a name="to-display-information-for-one-server"></a><span data-ttu-id="023f2-126">若要顯示某部伺服器的資訊</span><span class="sxs-lookup"><span data-stu-id="023f2-126">To display information for one server</span></span>  
  
-   <span data-ttu-id="023f2-127">在 [伺服器] 樹狀目錄中，按一下該部伺服器。</span><span class="sxs-lookup"><span data-stu-id="023f2-127">In the Server tree, click the server.</span></span>  
  
     <span data-ttu-id="023f2-128">資訊隨即顯示在 [結果] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="023f2-128">The information is displayed in the results pane.</span></span>  
  
### <a name="to-add-a-server"></a><span data-ttu-id="023f2-129">若要新增伺服器</span><span class="sxs-lookup"><span data-stu-id="023f2-129">To add a server</span></span>  
  
-   <span data-ttu-id="023f2-130">在 [領域] 窗格中，按一下滑鼠右鍵，然後按一下**新增伺服器**。</span><span class="sxs-lookup"><span data-stu-id="023f2-130">Right-click in the Scope pane, and then click **Add Server**.</span></span>  
  
     <span data-ttu-id="023f2-131">**新增伺服器** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="023f2-131">The **Add Server** dialog box appears.</span></span> <span data-ttu-id="023f2-132">輸入或瀏覽至您要新增的伺服器。</span><span class="sxs-lookup"><span data-stu-id="023f2-132">Type or browse to the server you want to add.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="023f2-133">在某些工作群組環境中，按一下**瀏覽**按鈕會關閉此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="023f2-133">In certain Workgroup environments, clicking the **Browse** button will cause this dialog box to close.</span></span> <span data-ttu-id="023f2-134">而不是使用**瀏覽**按鈕，只要在方塊中輸入伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="023f2-134">Instead of using the **Browse** button, simply type the server name in the box.</span></span>  
  
### <a name="to-view-or-change-server-properties"></a><span data-ttu-id="023f2-135">檢視或變更伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="023f2-135">To view or change server properties</span></span>  
  
-   <span data-ttu-id="023f2-136">在伺服器樹狀目錄中，以滑鼠右鍵按一下伺服器，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="023f2-136">In the Server tree, right-click the server, and click **Properties**.</span></span>  
  
     <span data-ttu-id="023f2-137">**伺服器屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="023f2-137">The **Server Properties** dialog box appears.</span></span> <span data-ttu-id="023f2-138">您可以檢視或變更下列索引標籤中的資訊：</span><span class="sxs-lookup"><span data-stu-id="023f2-138">You can view or change information in the following tabs:</span></span>  
  
    -   <span data-ttu-id="023f2-139">**稽核層級**</span><span class="sxs-lookup"><span data-stu-id="023f2-139">**Audit Levels**</span></span>  
  
    -   <span data-ttu-id="023f2-140">**SSO 資料庫**</span><span class="sxs-lookup"><span data-stu-id="023f2-140">**SSO Database**</span></span>  
  
    -   <span data-ttu-id="023f2-141">**SSO 服務**</span><span class="sxs-lookup"><span data-stu-id="023f2-141">**SSO Service**</span></span>  
  
    -   <span data-ttu-id="023f2-142">**密碼同步**</span><span class="sxs-lookup"><span data-stu-id="023f2-142">**Password Sync**</span></span>  
  
    -   <span data-ttu-id="023f2-143">**進階**</span><span class="sxs-lookup"><span data-stu-id="023f2-143">**Advanced**</span></span>