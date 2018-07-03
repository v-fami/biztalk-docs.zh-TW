---
title: 叫用類別的靜態成員 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a51171c-8de0-45dd-8659-f674cf27acbe
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3cb6a673fcf7fb363de678eceefd62802a063ca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022076"
---
# <a name="invoking-static-members-of-a-class"></a><span data-ttu-id="903af-102">叫用類別的靜態成員</span><span class="sxs-lookup"><span data-stu-id="903af-102">Invoking Static Members of a Class</span></span>
<span data-ttu-id="903af-103">根據預設，規則引擎需要您評估 .NET 類別的執行個體以執行叫用 .NET 類別之靜態成員的原則。</span><span class="sxs-lookup"><span data-stu-id="903af-103">By default, the rule engine requires you to assert an instance of a .NET class to execute a policy that invokes a static member of the .NET class.</span></span> <span data-ttu-id="903af-104">您可以修改此行為變更的值**StaticSupport**登錄機碼底下**HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**其中一個下表中的值。</span><span class="sxs-lookup"><span data-stu-id="903af-104">You can modify this behavior by changing the value of the **StaticSupport** registry key under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0** to one of the values in the following table.</span></span>  
  
|<span data-ttu-id="903af-105">StaticSupport 登錄值</span><span class="sxs-lookup"><span data-stu-id="903af-105">StaticSupport registry value</span></span>|<span data-ttu-id="903af-106">規則引擎行為</span><span class="sxs-lookup"><span data-stu-id="903af-106">Rule engine behavior</span></span>|  
|----------------------------------|--------------------------|  
|<span data-ttu-id="903af-107">0</span><span class="sxs-lookup"><span data-stu-id="903af-107">0</span></span>|<span data-ttu-id="903af-108">預設值。</span><span class="sxs-lookup"><span data-stu-id="903af-108">Default value.</span></span> <span data-ttu-id="903af-109">規則引擎遵循 BizTalk Server 2004 模型，其中只有在評估 .NET 類別的執行個體時，才會呼叫靜態方法。</span><span class="sxs-lookup"><span data-stu-id="903af-109">The rule engine follows the BizTalk Server 2004 model, where the static method is called only when an instance of the .NET class is asserted.</span></span>|  
|<span data-ttu-id="903af-110">@shouldalert</span><span class="sxs-lookup"><span data-stu-id="903af-110">1</span></span>|<span data-ttu-id="903af-111">不需要物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="903af-111">An object instance is not required.</span></span> <span data-ttu-id="903af-112">當評估或執行規則時便會呼叫靜態方法。</span><span class="sxs-lookup"><span data-stu-id="903af-112">The static method is called when the rule is evaluated or executed.</span></span>|  
|<span data-ttu-id="903af-113">2</span><span class="sxs-lookup"><span data-stu-id="903af-113">2</span></span>|<span data-ttu-id="903af-114">不需要物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="903af-114">An object instance is not required.</span></span> <span data-ttu-id="903af-115">如果所有的參數都是常數，便會在原則轉譯時呼叫靜態方法。</span><span class="sxs-lookup"><span data-stu-id="903af-115">The static method is called at the policy translation time if all parameters are constant.</span></span> <span data-ttu-id="903af-116">這是一項效能最佳化，因為即使是在多規則的狀況下使用，依然只會呼叫一次靜態方法。</span><span class="sxs-lookup"><span data-stu-id="903af-116">This is a performance optimization because the static method is called only once even though it is used in multiple rules in conditions.</span></span> <span data-ttu-id="903af-117">請注意，用來做為動作的靜態方法將不會在轉譯時執行，不過卻可能會執行用來做為參數的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="903af-117">Note that static methods used as actions will not be executed at the translation time, but static methods used as parameters may be executed.</span></span>|  
  
## <a name="adding-and-changing-the-staticsupport-registry-key"></a><span data-ttu-id="903af-118">新增和變更 StaticSupport 登錄機碼</span><span class="sxs-lookup"><span data-stu-id="903af-118">Adding and Changing the StaticSupport Registry Key</span></span>  
 <span data-ttu-id="903af-119">如果您看不見**StaticSupport**登錄機碼底下**HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**，您應該執行下列步驟來新增。</span><span class="sxs-lookup"><span data-stu-id="903af-119">If you do not see the **StaticSupport** registry key under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**, you should add it by performing the following steps.</span></span>  
  
 <span data-ttu-id="903af-120">**若要新增 StaticSupport 登錄機碼**</span><span class="sxs-lookup"><span data-stu-id="903af-120">**To add the StaticSupport registry key**</span></span>  
  
1. <span data-ttu-id="903af-121">按一下 **開始**，按一下**執行**，型別**RegEdit**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="903af-121">Click **Start**, click **Run**, type **RegEdit**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="903af-122">依序展開**HKEY_LOCAL_MACHINE**，展開**軟體**，展開**Microsoft**，展開**BusinessRules**，然後選取  **3.0**。</span><span class="sxs-lookup"><span data-stu-id="903af-122">Expand **HKEY_LOCAL_MACHINE**, expand **Software**, expand **Microsoft**, expand **BusinessRules**, and then select **3.0**.</span></span>  
  
3. <span data-ttu-id="903af-123">在右窗格中，以滑鼠右鍵按一下，指向**的新**，然後按一下**DWORD 值**。</span><span class="sxs-lookup"><span data-stu-id="903af-123">In the right pane, right-click, point to **New**, and then click **DWORD value**.</span></span>  
  
4. <span data-ttu-id="903af-124">針對**名稱**，型別**StaticSupport**。</span><span class="sxs-lookup"><span data-stu-id="903af-124">For **Name**, type **StaticSupport**.</span></span>  
  
   <span data-ttu-id="903af-125">如果**StaticSupport**登錄機碼已經存在，而且您需要變更其值，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="903af-125">If the **StaticSupport** registry key already exists, and you need to change its value, perform the following steps.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="903af-126">如果 BizTalk 安裝在 64 位元電腦上，則您可以加入**StaticSupport**登錄機碼使用下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="903af-126">If BizTalk is installed on a 64-bit machine, then you can add **StaticSupport** registry key using either of the following options:</span></span>  
> 
> - <span data-ttu-id="903af-127">您需要查看 HKLM\Software\Wow6432Node\Microsoft\BusinessRules\3.0 底下。</span><span class="sxs-lookup"><span data-stu-id="903af-127">You need to look under HKLM\Software\Wow6432Node\Microsoft\BusinessRules\3.0.</span></span> <span data-ttu-id="903af-128">如果此機碼存在，則您可以加入**StaticSupport**這裡。</span><span class="sxs-lookup"><span data-stu-id="903af-128">If this key exists, then you can add **StaticSupport** here.</span></span>  
>   -   <span data-ttu-id="903af-129">另一個選項是將放**StaticSupport**中**BTNTsvc [64].exe.config**檔案，因為此處的任何設定覆寫功能的登錄。</span><span class="sxs-lookup"><span data-stu-id="903af-129">Another option is to put **StaticSupport** in the **BTNTsvc[64].exe.config** file, as any settings here override what's in the Registry.</span></span>  <span data-ttu-id="903af-130">此外，其中也可以將引數，這是慣用選項因為它會隔離的預設行為變更至 BizTalk，而登錄設定是全域的作業系統。</span><span class="sxs-lookup"><span data-stu-id="903af-130">Further, one can also make the argument that this option is preferred since it isolates the change in default behavior to BizTalk only, whereas Registry settings are global to the Operating System.</span></span>  
  
 <span data-ttu-id="903af-131">**若要變更 StaticSupport 登錄機碼值**</span><span class="sxs-lookup"><span data-stu-id="903af-131">**To change the value of the StaticSupport registry key**</span></span>  
  
1.  <span data-ttu-id="903af-132">按一下 **開始**，按一下**執行**，型別**RegEdit**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="903af-132">Click **Start**, click **Run**, type **RegEdit**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="903af-133">依序展開**HKEY_LOCAL_MACHINE**，展開**軟體**，展開**Microsoft**，展開**BusinessRules**，然後展開  **3.0**。</span><span class="sxs-lookup"><span data-stu-id="903af-133">Expand **HKEY_LOCAL_MACHINE**, expand **Software**, expand **Microsoft**, expand **BusinessRules**, and then expand **3.0**.</span></span>  
  
3.  <span data-ttu-id="903af-134">按兩下**StaticSupport**登錄機碼，或以滑鼠右鍵按一下它，然後按一下**修改**。</span><span class="sxs-lookup"><span data-stu-id="903af-134">Double-click the **StaticSupport** registry key, or right-click it and then click **Modify**.</span></span>