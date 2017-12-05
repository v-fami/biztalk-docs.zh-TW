---
title: "配接器登錄精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- utilities, Adapter Registration Wizard
- Adapter Registration Wizard
ms.assetid: bd15d0c7-01bb-41f9-9157-cdcf4bb4e39a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b721294acb07d4c69c5b2ae7b58b0e135625eee8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="adapter-registry-wizard"></a><span data-ttu-id="014bb-102">配接器登錄精靈</span><span class="sxs-lookup"><span data-stu-id="014bb-102">Adapter Registry Wizard</span></span>
<span data-ttu-id="014bb-103">您可以使用配接器登錄精靈來建立設定和註冊自訂的配接器所需的登錄檔。</span><span class="sxs-lookup"><span data-stu-id="014bb-103">You use the Adapter Registry Wizard to create the registry files needed to configure and register a custom adapter.</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="014bb-104">SDK 中的位置</span><span class="sxs-lookup"><span data-stu-id="014bb-104">Location in SDK</span></span>  
 <span data-ttu-id="014bb-105">*\<安裝路徑\>*\SDK\Utilities\AdapterRegistryWizard\\</span><span class="sxs-lookup"><span data-stu-id="014bb-105">*\<Installation Path\>*\SDK\Utilities\AdapterRegistryWizard\\</span></span>  
  
## <a name="to-run-this-utility"></a><span data-ttu-id="014bb-106">執行此公用程式</span><span class="sxs-lookup"><span data-stu-id="014bb-106">To Run This Utility</span></span>  
 <span data-ttu-id="014bb-107">執行 AdapterRegistryWizard.exe 可執行檔，以啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="014bb-107">Start the wizard by running the AdapterRegistryWizard.exe executable.</span></span> <span data-ttu-id="014bb-108">接下來將會出現幾個頁面，提示您輸入有關配接器的資訊，以及配接器支援的屬性。</span><span class="sxs-lookup"><span data-stu-id="014bb-108">The pages that follow prompt you for information about your adapter and the properties that it supports.</span></span> <span data-ttu-id="014bb-109">下列各節將描述「配接器登錄精靈」的各個頁面。</span><span class="sxs-lookup"><span data-stu-id="014bb-109">The individual Adapter Registry Wizard pages are described in the sections that follow.</span></span>  
  
### <a name="generic-adapter-properties-page"></a><span data-ttu-id="014bb-110">一般配接器屬性頁面</span><span class="sxs-lookup"><span data-stu-id="014bb-110">Generic Adapter Properties page</span></span>  
 <span data-ttu-id="014bb-111">使用 [一般配接器屬性] 頁面可指定配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="014bb-111">Use the Generic Adapter Properties page to specify adapter properties.</span></span>  
  
|<span data-ttu-id="014bb-112">使用</span><span class="sxs-lookup"><span data-stu-id="014bb-112">Use this</span></span>|<span data-ttu-id="014bb-113">動作</span><span class="sxs-lookup"><span data-stu-id="014bb-113">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="014bb-114">**傳輸配接器類型**</span><span class="sxs-lookup"><span data-stu-id="014bb-114">**Transport adapter type**</span></span>|<span data-ttu-id="014bb-115">指定配接器類型。</span><span class="sxs-lookup"><span data-stu-id="014bb-115">Specify the adapter type.</span></span>|  
|<span data-ttu-id="014bb-116">**屬性命名空間**</span><span class="sxs-lookup"><span data-stu-id="014bb-116">**Property namespace**</span></span>|<span data-ttu-id="014bb-117">指定配接器命名空間。</span><span class="sxs-lookup"><span data-stu-id="014bb-117">Specify the adapter namespace.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="014bb-118">會將配接器特定屬性儲存在這個命名空間中的訊息內容。</span><span class="sxs-lookup"><span data-stu-id="014bb-118"> stores adapter-specific properties on the message context in this namespace.</span></span>|  
|<span data-ttu-id="014bb-119">**配接器接收訊息，並將它們送出至 BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="014bb-119">**Adapter can receive messages and submit them to BizTalk Server**</span></span>|<span data-ttu-id="014bb-120">識別配接器支援的通訊模式。</span><span class="sxs-lookup"><span data-stu-id="014bb-120">Identify communication patterns supported by the adapter.</span></span> <span data-ttu-id="014bb-121">用來計算配接器的 Constraints 登錄項目。</span><span class="sxs-lookup"><span data-stu-id="014bb-121">Used to calculate the Constraints registry entry for the adapter.</span></span>|  
|<span data-ttu-id="014bb-122">**配接器可以從 BizTalk Server 傳送訊息**</span><span class="sxs-lookup"><span data-stu-id="014bb-122">**Adapter can send messages from BizTalk Server**</span></span>|<span data-ttu-id="014bb-123">識別配接器支援的通訊模式。</span><span class="sxs-lookup"><span data-stu-id="014bb-123">Identify communication patterns supported by the adapter.</span></span> <span data-ttu-id="014bb-124">用來計算配接器的 Constraints 登錄項目。</span><span class="sxs-lookup"><span data-stu-id="014bb-124">Used to calculate the Constraints registry entry for the adapter.</span></span>|  
  
### <a name="inbound-part-page"></a><span data-ttu-id="014bb-125">輸入部分頁面</span><span class="sxs-lookup"><span data-stu-id="014bb-125">Inbound Part page</span></span>  
 <span data-ttu-id="014bb-126">使用 [輸入部分] 頁面可指定配接器的輸入接收邏輯。</span><span class="sxs-lookup"><span data-stu-id="014bb-126">Use the Inbound Part page to specify inbound receiving logic for your adapter.</span></span>  
  
|<span data-ttu-id="014bb-127">使用</span><span class="sxs-lookup"><span data-stu-id="014bb-127">Use this</span></span>|<span data-ttu-id="014bb-128">動作</span><span class="sxs-lookup"><span data-stu-id="014bb-128">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="014bb-129">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="014bb-129">**Browse**</span></span>|<span data-ttu-id="014bb-130">為您的配接器選取會實作輸入接收邏輯的組件。</span><span class="sxs-lookup"><span data-stu-id="014bb-130">Select the assembly that implements the inbound receiving logic for your adapter.</span></span> <span data-ttu-id="014bb-131">此組件所公開的公用型別清單隨即出現在下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="014bb-131">A list of the public types exposed by this assembly appear in the drop-down list.</span></span> <span data-ttu-id="014bb-132">請從下拉式清單中，在針對此配接器實作輸入邏輯的指定組件內，選取型別。</span><span class="sxs-lookup"><span data-stu-id="014bb-132">Select the type within the specified assembly that implements the inbound logic for this adapter from the drop-down list.</span></span>|  
|<span data-ttu-id="014bb-133">**配接器支援要求-回應通訊協定**</span><span class="sxs-lookup"><span data-stu-id="014bb-133">**Adapter supports request-response protocol**</span></span>|<span data-ttu-id="014bb-134">指定配接器的接收功能。</span><span class="sxs-lookup"><span data-stu-id="014bb-134">Specify the receive capabilities of your adapter.</span></span> <span data-ttu-id="014bb-135">用來計算配接器的 Constraints 登錄項目。</span><span class="sxs-lookup"><span data-stu-id="014bb-135">Used to calculate the Constraints registry entry for your adapter.</span></span>|  
|<span data-ttu-id="014bb-136">**配接器是外掛式 （裝載在不同的處理序）**</span><span class="sxs-lookup"><span data-stu-id="014bb-136">**Adapter is isolated (that is hosted in a different process)**</span></span>|<span data-ttu-id="014bb-137">指定配接器的接收功能。</span><span class="sxs-lookup"><span data-stu-id="014bb-137">Specify the receive capabilities of your adapter.</span></span> <span data-ttu-id="014bb-138">用來計算配接器的 Constraints 登錄項目。</span><span class="sxs-lookup"><span data-stu-id="014bb-138">Used to calculate the Constraints registry entry for your adapter.</span></span>|  
  
### <a name="outbound-part-page"></a><span data-ttu-id="014bb-139">輸出部分頁面</span><span class="sxs-lookup"><span data-stu-id="014bb-139">Outbound Part page</span></span>  
 <span data-ttu-id="014bb-140">使用 [輸出部分] 頁面可指定配接器的輸出接收邏輯。</span><span class="sxs-lookup"><span data-stu-id="014bb-140">Use the Outbound Part page to specify outbound receiving logic for your adapter.</span></span>  
  
|<span data-ttu-id="014bb-141">使用</span><span class="sxs-lookup"><span data-stu-id="014bb-141">Use this</span></span>|<span data-ttu-id="014bb-142">動作</span><span class="sxs-lookup"><span data-stu-id="014bb-142">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="014bb-143">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="014bb-143">**Browse**</span></span>|<span data-ttu-id="014bb-144">為您的配接器選取會實作輸出接收邏輯的組件。</span><span class="sxs-lookup"><span data-stu-id="014bb-144">Select the assembly that implements the outbound receiving logic for your adapter.</span></span> <span data-ttu-id="014bb-145">這個組件所公開的公用型別清單隨即出現在下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="014bb-145">A list of the public types exposed by this assembly appears in the drop-down list .</span></span> <span data-ttu-id="014bb-146">請從下拉式清單中，在針對此配接器實作輸出邏輯的指定組件內，選取型別。</span><span class="sxs-lookup"><span data-stu-id="014bb-146">Select the type for the specified assembly that implements the outbound logic for this adapter from the drop-down list.</span></span> <span data-ttu-id="014bb-147">您也必須輸入用於識別通訊協定 (由此配接器所使用) 之以逗號分隔的別名清單 (例如 submit://)。</span><span class="sxs-lookup"><span data-stu-id="014bb-147">You must also enter a comma-separated list of aliases used to identify the protocol used by this adapter (for example, submit://).</span></span>|  
|<span data-ttu-id="014bb-148">**配接器支援請求-回應通訊協定**</span><span class="sxs-lookup"><span data-stu-id="014bb-148">**Adapter supports solicit-response protocol**</span></span>|<span data-ttu-id="014bb-149">識別配接器的傳輸功能。</span><span class="sxs-lookup"><span data-stu-id="014bb-149">Identify the transmitting capabilities of your adapter.</span></span> <span data-ttu-id="014bb-150">這些值可用來計算配接器的 Constraints 登錄項目。</span><span class="sxs-lookup"><span data-stu-id="014bb-150">These values are used to calculate the Constraints registry entry for your adapter.</span></span>|  
  
### <a name="adapter-management-page"></a><span data-ttu-id="014bb-151">配接器管理頁面</span><span class="sxs-lookup"><span data-stu-id="014bb-151">Adapter Management page</span></span>  
 <span data-ttu-id="014bb-152">使用 [配接器管理] 頁面可指定配接器的設計階段管理邏輯。</span><span class="sxs-lookup"><span data-stu-id="014bb-152">Use the Adapter Management page to specify design-time management logic for your adapter.</span></span>  
  
|<span data-ttu-id="014bb-153">使用</span><span class="sxs-lookup"><span data-stu-id="014bb-153">Use this</span></span>|<span data-ttu-id="014bb-154">動作</span><span class="sxs-lookup"><span data-stu-id="014bb-154">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="014bb-155">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="014bb-155">**Browse**</span></span>|<span data-ttu-id="014bb-156">為您的配接器選取會實作設計階段配接器管理邏輯的組件。</span><span class="sxs-lookup"><span data-stu-id="014bb-156">Select the assembly that implements the design-time adapter management logic for your adapter.</span></span> <span data-ttu-id="014bb-157">此組件所公開的公用型別清單隨即出現在下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="014bb-157">A list of the public types exposed by this assembly appears in the drop-down list.</span></span> <span data-ttu-id="014bb-158">請從下拉式清單中，在針對此配接器實作配接器管理邏輯的指定組件內，選取型別。</span><span class="sxs-lookup"><span data-stu-id="014bb-158">Select the type for the specified assembly that implements the adapter management logic for this adapter from the drop-down list.</span></span>|  
  
### <a name="output-file-name"></a><span data-ttu-id="014bb-159">輸出檔名稱</span><span class="sxs-lookup"><span data-stu-id="014bb-159">Output File name</span></span>  
 <span data-ttu-id="014bb-160">使用 [輸出檔名稱] 頁面可指定輸出檔的名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="014bb-160">Use the Output file name page to specify an output file name and location.</span></span>  
  
|<span data-ttu-id="014bb-161">使用</span><span class="sxs-lookup"><span data-stu-id="014bb-161">Use this</span></span>|<span data-ttu-id="014bb-162">動作</span><span class="sxs-lookup"><span data-stu-id="014bb-162">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="014bb-163">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="014bb-163">**Browse**</span></span>|<span data-ttu-id="014bb-164">選擇輸出檔的名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="014bb-164">Choose an output file name and location.</span></span> <span data-ttu-id="014bb-165">配接器登錄會寫入這個檔案。</span><span class="sxs-lookup"><span data-stu-id="014bb-165">The adapter registry is written to this file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="014bb-166">備註</span><span class="sxs-lookup"><span data-stu-id="014bb-166">Remarks</span></span>  
 <span data-ttu-id="014bb-167">「配接器登錄精靈」公用程式會在「企業單一登入」(SSO) 組態存放區屬性中填入預設值。</span><span class="sxs-lookup"><span data-stu-id="014bb-167">The Adapter Registry Wizard utility populates the Enterprise Single Sign-On (SSO) configuration store properties with default values.</span></span> <span data-ttu-id="014bb-168">如果您的配接器並未使用配接器架構提供的標準屬性頁面做為處理常式和位置配接器屬性，您必須手動編輯登錄檔來修改這些值。</span><span class="sxs-lookup"><span data-stu-id="014bb-168">If your adapter does not use the standard property pages provided by the Adapter Framework for handler and location adapter properties, you must edit the registry file manually to modify these values.</span></span> <span data-ttu-id="014bb-169">如需這些設定的詳細資訊，請參閱 「 SSO 組態存放區的配接器屬性登錄 」 主題中[登錄配接器](../core/registering-an-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="014bb-169">For more information about these settings, see "Registration of adapter properties for SSO configuration store" in the topic [Registering an Adapter](../core/registering-an-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014bb-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="014bb-170">See Also</span></span>  
 <span data-ttu-id="014bb-171">[在 SDK 中的公用程式](../core/utilities-in-the-sdk.md) </span><span class="sxs-lookup"><span data-stu-id="014bb-171">[Utilities in the SDK](../core/utilities-in-the-sdk.md) </span></span>  
 [<span data-ttu-id="014bb-172">註冊配接器</span><span class="sxs-lookup"><span data-stu-id="014bb-172">Registering an Adapter</span></span>](../core/registering-an-adapter.md)