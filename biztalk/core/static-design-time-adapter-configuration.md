---
title: 靜態設計階段配接器組態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 332723a4-e39d-43f5-af4d-bf9f56496535
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8337e4f53afe22ccbde0e1d1d2a6437d280011d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278894"
---
# <a name="static-design-time-adapter-configuration"></a><span data-ttu-id="8e0fb-102">靜態設計階段配接器組態</span><span class="sxs-lookup"><span data-stu-id="8e0fb-102">Static Design-Time Adapter Configuration</span></span>
<span data-ttu-id="8e0fb-103">配接器的設計階段部分必須負責定義所有可用屬性並驗證使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-103">The design-time part of the adapter is responsible for defining all the available properties and for validating user input.</span></span> <span data-ttu-id="8e0fb-104">在靜態設計階段組態中，配接器使用預設使用者介面 (UI) 來顯示和編輯其屬性。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-104">In a static design-time configuration the adapter uses the default user interface (UI) for displaying and editing its properties.</span></span>  
  
 <span data-ttu-id="8e0fb-105">本節說明如何實作自訂配接器的靜態設計階段組態功能。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-105">This section explains how to implement static design-time configuration capability for your custom adapter.</span></span> <span data-ttu-id="8e0fb-106">您所決定進行的變更，將會根據配接器與應用程式通訊的需要，以及配接器所需要實作的邏輯。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-106">The changes you decide to make will be based on the needs of the applications with which the adapter communicates and the logic that the adapter needs to implement.</span></span> <span data-ttu-id="8e0fb-107">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]「說明」章節的連結，會以更多細節描述這些步驟，或是提供額外的背景資訊 (如果存在)。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-107">Links to sections of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help that describe these steps in more detail or provide additional background are provided when available.</span></span> <span data-ttu-id="8e0fb-108">此外，它還會叫出範例檔配接器文件中提供相關範例的位置。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-108">Additionally it calls out the places in the sample file adapter documentation that provide relevant examples.</span></span>  
  
## <a name="guidelines-for-the-static-development-process"></a><span data-ttu-id="8e0fb-109">靜態開發程序的指導方針</span><span class="sxs-lookup"><span data-stu-id="8e0fb-109">Guidelines for the Static Development Process</span></span>  
 <span data-ttu-id="8e0fb-110">下列清單提供將靜態設計階段功能建置到配接器中的建議。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-110">The following list provides recommendations for building static design-time functionality into your adapter.</span></span> <span data-ttu-id="8e0fb-111">在開發期間，您可能不需要進行所有這些步驟，也不需以固定的順序執行它們。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-111">During development you may not need to do all of these steps, nor execute them in a rigid sequence.</span></span>  
  
1.  <span data-ttu-id="8e0fb-112">建立配接器組態需求以及需要設定之組態參數的清單。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-112">Create a list of adapter configuration requirements and configuration parameters that you need to set.</span></span> <span data-ttu-id="8e0fb-113">如果參數要讓所有接收位置和傳送埠在全域使用，請在處理常式結構描述組態檔中指定它們。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-113">If the parameters are globally used for all receive locations and send ports, specify them in the handler schema configuration file.</span></span> <span data-ttu-id="8e0fb-114">如果它們有特定的連接埠或位置，請在傳送埠和接收位置組態檔中予以設定。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-114">If they are port or location specific, configure them in the send port and receive location configuration files.</span></span>  
  
2.  <span data-ttu-id="8e0fb-115">修改配接器屬性頁以納入任何新的組態參數。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-115">Modify the adapter property pages to account for any new configuration parameters.</span></span> <span data-ttu-id="8e0fb-116">如需這個步驟的資訊，請參閱[配接器組態結構描述](../core/adapter-configuration-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-116">For information about this step, see [Adapter Configuration Schemas](../core/adapter-configuration-schemas.md).</span></span>  
  
3.  <span data-ttu-id="8e0fb-117">使用 [新增配接器中繼資料精靈] 修改結構描述類別的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-117">Modify the tree view of the schema categories by using the Add Adapter Metadata Wizard.</span></span> <span data-ttu-id="8e0fb-118">如需有關此步驟的詳細資訊，請參閱[新增配接器中繼資料精靈 中的結構描述類別](../core/schema-categories-in-the-add-adapter-metadata-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="8e0fb-118">For more information about this step, see [Schema Categories in the Add Adapter Metadata Wizard](../core/schema-categories-in-the-add-adapter-metadata-wizard.md)</span></span>  
  
4.  <span data-ttu-id="8e0fb-119">修改範例程式碼，將結構描述傳回為 Web 服務描述語言 (WSDL) 檔案。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-119">Modify the sample code to return schemas as Web Services Description Language (WSDL) files.</span></span> <span data-ttu-id="8e0fb-120">如需有關此步驟的詳細資訊，請參閱[靜態配接器 IStaticAdapterConfig 介面](../core/static-adapter-istaticadapterconfig-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-120">For more information about this step, see [Static Adapter IStaticAdapterConfig Interface](../core/static-adapter-istaticadapterconfig-interface.md).</span></span>  
  
5.  <span data-ttu-id="8e0fb-121">修改現有的 WSDL 檔案或建立新的 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-121">Modify the existing WSDL files or create new WSDL files.</span></span> <span data-ttu-id="8e0fb-122">如需有關此步驟的詳細資訊，請參閱[配接器 WSDL 檔案](../core/adapter-wsdl-files.md)。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-122">For more information about this step, see [Adapter WSDL Files](../core/adapter-wsdl-files.md).</span></span>  
  
6.  <span data-ttu-id="8e0fb-123">修改範例程式碼，傳回配接器所需要卻未包含在 WSDL 檔案中的其他 XSD 檔案。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-123">Modify the sample code to return additional XSD files needed by the adapter that are not included in the WSDL files.</span></span> <span data-ttu-id="8e0fb-124">如需有關此步驟的詳細資訊，請參閱[配接器 GetSchema 方法](../core/adapter-getschema-method.md)。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-124">For more information about this step, see [Adapter GetSchema Method](../core/adapter-getschema-method.md).</span></span>  
  
7.  <span data-ttu-id="8e0fb-125">修改配接器登錄機碼並執行配接器登錄檔。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-125">Modify the adapter registry keys and run the adapter registry file.</span></span> <span data-ttu-id="8e0fb-126">如需有關此步驟的詳細資訊，請參閱[配接器登錄檔案](../core/adapter-registration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-126">For more information about this step, see [Adapter Registration File](../core/adapter-registration-file.md).</span></span>  
  
8.  <span data-ttu-id="8e0fb-127">將靜態配接器安裝到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-127">Install the static adapter into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="8e0fb-128">如需有關此步驟的詳細資訊，請參閱[配接器安裝到 BizTalk Server](../core/install-the-adapter-into-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-128">For more information about this step, see [Install the Adapter into BizTalk Server](../core/install-the-adapter-into-biztalk-server.md).</span></span>  
  
9. <span data-ttu-id="8e0fb-129">測試對配接器屬性頁進行的變更。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-129">Test the changes made to the adapter property pages.</span></span> <span data-ttu-id="8e0fb-130">重新建置配接器，測試出現在 [新增配接器中繼資料精靈] 中的 UI。</span><span class="sxs-lookup"><span data-stu-id="8e0fb-130">Rebuild the adapter to test the UI that appears in the Add Adapter Metadata Wizard.</span></span> <span data-ttu-id="8e0fb-131">如需有關此步驟的詳細資訊，請參閱[建置和測試配接器專案](../core/build-and-test-the-adapter-project.md)</span><span class="sxs-lookup"><span data-stu-id="8e0fb-131">For more information about this step, see [Build and Test the Adapter Project](../core/build-and-test-the-adapter-project.md)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e0fb-132">本節內容</span><span class="sxs-lookup"><span data-stu-id="8e0fb-132">In This Section</span></span>  
  
-   [<span data-ttu-id="8e0fb-133">靜態配接器 IStaticAdapterConfig 介面</span><span class="sxs-lookup"><span data-stu-id="8e0fb-133">Static Adapter IStaticAdapterConfig Interface</span></span>](../core/static-adapter-istaticadapterconfig-interface.md)  
  
-   [<span data-ttu-id="8e0fb-134">結構描述中的類別目錄新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="8e0fb-134">Schema Categories in the Add Adapter Metadata Wizard</span></span>](../core/schema-categories-in-the-add-adapter-metadata-wizard.md)