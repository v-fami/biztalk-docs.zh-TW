---
title: "BTAD_SilentMode |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTAD_SilentMode [environment variable], about BTAS_SilentMode
- BTAD_SilentMode [environment variable]
- BTAD_SilentMode [environment variable], warnings
ms.assetid: 271835cf-1587-44c5-b5af-b4df4e981ab4
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31715835c98d2f60a3b5f1c18251571ea57641d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="btadsilentmode"></a><span data-ttu-id="4dfa6-102">BTAD_SilentMode</span><span class="sxs-lookup"><span data-stu-id="4dfa6-102">BTAD_SilentMode</span></span>
<span data-ttu-id="4dfa6-103">BTAD_SilentMode 指定採用無訊息模式執行指令碼的選項。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-103">BTAD_SilentMode specifies options for running the script in silent mode.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dfa6-104">備註</span><span class="sxs-lookup"><span data-stu-id="4dfa6-104">Remarks</span></span>  
 <span data-ttu-id="4dfa6-105">當您指定無訊息模式的選項時，BTS Installer 便會將其值存放在 BTAD_SilentMode 變數中。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-105">When you specify an option for silent mode, BTS Installer places its value into the BTAD_SilentMode variable.</span></span>  
  
 <span data-ttu-id="4dfa6-106">BTAD_SilentMode 的預設值為 2，這會指定要在無訊息模式中執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-106">The default value of BTAD_SilentMode is 2, which specifies that the script runs in silent mode.</span></span> <span data-ttu-id="4dfa6-107">下表描述 BTAD_SilentMode 的可能值。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-107">The following table describes the possible values for BTAD_SilentMode.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4dfa6-108">如果您從指令碼中啟動 BizTalk Server 使用者介面，其強制回應對話方塊可能無法顯示或者沒有焦點，要加以檢視或關閉就變得很困難。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-108">If you start the BizTalk Server user interface from scripts, modal dialog boxes may not be visible or have focus, making them difficult to view and dismiss.</span></span> <span data-ttu-id="4dfa6-109">當強制回應對話方塊開啟時，可能會讓 BizTalk 資料庫處在鎖定狀態而無法存取。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-109">The BizTalk databases can become locked and inaccessible while modal dialog boxes are open.</span></span> <span data-ttu-id="4dfa6-110">因此，實際執行系統上的所有指令碼都應該在無訊息模式下執行。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-110">For this reason, on production systems, all scripts should run in silent mode.</span></span>  
  
|<span data-ttu-id="4dfa6-111">Value</span><span class="sxs-lookup"><span data-stu-id="4dfa6-111">Value</span></span>|<span data-ttu-id="4dfa6-112">描述</span><span class="sxs-lookup"><span data-stu-id="4dfa6-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4dfa6-113">0</span><span class="sxs-lookup"><span data-stu-id="4dfa6-113">0</span></span>|<span data-ttu-id="4dfa6-114">不會變更使用者介面 (UI) 層級。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-114">Does not change the user interface (UI) level.</span></span>|  
|<span data-ttu-id="4dfa6-115">1</span><span class="sxs-lookup"><span data-stu-id="4dfa6-115">1</span></span>|<span data-ttu-id="4dfa6-116">使用預設 UI 層級。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-116">Uses the default UI level.</span></span>|  
|<span data-ttu-id="4dfa6-117">2</span><span class="sxs-lookup"><span data-stu-id="4dfa6-117">2</span></span>|<span data-ttu-id="4dfa6-118">執行無訊息安裝 (預設)。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-118">Performs a silent installation (the default).</span></span>|  
|<span data-ttu-id="4dfa6-119">3</span><span class="sxs-lookup"><span data-stu-id="4dfa6-119">3</span></span>|<span data-ttu-id="4dfa6-120">提供簡單的進度和錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-120">Provides simple progress and error handling.</span></span>|  
|<span data-ttu-id="4dfa6-121">4</span><span class="sxs-lookup"><span data-stu-id="4dfa6-121">4</span></span>|<span data-ttu-id="4dfa6-122">提供設計的 UI，並將精靈隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-122">Provides authored UI; suppresses wizards.</span></span>|  
|<span data-ttu-id="4dfa6-123">0x80</span><span class="sxs-lookup"><span data-stu-id="4dfa6-123">0x80</span></span>|<span data-ttu-id="4dfa6-124">與上述任一個值合併使用時，如果指令碼執行成功或是發生錯誤，Windows Installer 將會顯示強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-124">If combined with any above value, Windows Installer displays a modal dialog box if the script has executed successfully or if there has been an error.</span></span> <span data-ttu-id="4dfa6-125">如果使用者取消作業，則不會顯示任何對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-125">No dialog box is displayed if the user cancels the operation.</span></span>|  
|<span data-ttu-id="4dfa6-126">0x40</span><span class="sxs-lookup"><span data-stu-id="4dfa6-126">0x40</span></span>|<span data-ttu-id="4dfa6-127">如果與 3 這個值合併使用，Windows Installer 將顯示進度對話方塊，但不會顯示任何強制回應對話方塊或錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-127">If combined with the 3 value, Windows Installer displays progress dialog boxes but does not display any modal dialog boxes or error dialog boxes.</span></span>|  
|<span data-ttu-id="4dfa6-128">0x20</span><span class="sxs-lookup"><span data-stu-id="4dfa6-128">0x20</span></span>|<span data-ttu-id="4dfa6-129">如果與 3 這個值合併使用，Windows Installer 將顯示進度對話方塊，但不會顯示任何強制回應對話方塊或錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-129">If combined with the 3 value, Windows Installer displays progress dialog boxes but does not display any modal dialog boxes or error dialog boxes.</span></span>|  
|<span data-ttu-id="4dfa6-130">0x100</span><span class="sxs-lookup"><span data-stu-id="4dfa6-130">0x100</span></span>|<span data-ttu-id="4dfa6-131">如果與 3 這個值合併使用，Windows Installer 將顯示進度對話方塊，但不會顯示任何強制回應對話方塊或錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-131">If combined with the 3 value, Windows Installer displays progress dialog boxes but does not display any modal dialog boxes or error dialog boxes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4dfa6-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dfa6-132">See Also</span></span>  
 <span data-ttu-id="4dfa6-133">[前置和後置處理指令碼環境變數](../core/pre-and-post-processing-script-environment-variables.md) </span><span class="sxs-lookup"><span data-stu-id="4dfa6-133">[Pre- and Post-processing Script Environment Variables](../core/pre-and-post-processing-script-environment-variables.md) </span></span>  
 [<span data-ttu-id="4dfa6-134">環境變數如何指示部署狀態</span><span class="sxs-lookup"><span data-stu-id="4dfa6-134">How Environment Variables Indicate Deployment State</span></span>](../core/how-environment-variables-indicate-deployment-state.md)