---
title: 使用路線設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06742cb8-f6d6-46e2-adc0-6be9a3d6a447
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 747ce8a750f2b2c775deaa1123a1b6b1d387eafc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999399"
---
# <a name="working-in-itinerary-designer"></a><span data-ttu-id="3dca6-102">使用路線設計工具</span><span class="sxs-lookup"><span data-stu-id="3dca6-102">Working in Itinerary Designer</span></span>
<span data-ttu-id="3dca6-103">建立 Microsoft Visual C# 專案之後，您可以建立新的路線模型，並加入專案中現有的路線。</span><span class="sxs-lookup"><span data-stu-id="3dca6-103">After you create a Microsoft Visual C# project, you can create new itinerary models and add existing itineraries to the project.</span></span> <span data-ttu-id="3dca6-104">下列步驟說明如何建立新的路線、 加入現有的路線模型，或變更路線的名稱。</span><span class="sxs-lookup"><span data-stu-id="3dca6-104">The following steps describe how to create a new itinerary, add an existing itinerary model, or change the name of an itinerary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3dca6-105">之前使用路線設計工具，您必須安裝 Microsoft.Practices.ESB.CORE Windows Installer （.msi 檔案） 從[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="3dca6-105">Before working with the Itinerary Designer, you must install the Microsoft.Practices.ESB.CORE Windows Installer (.msi file) from the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] install folder.</span></span> <span data-ttu-id="3dca6-106">此步驟會安裝必要的執行階段組件至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="3dca6-106">This step installs the required run-time assemblies to the global assembly cache.</span></span>  
  
## <a name="basic-operations"></a><span data-ttu-id="3dca6-107">基本作業</span><span class="sxs-lookup"><span data-stu-id="3dca6-107">Basic Operations</span></span>  

#### <a name="create-an-itinerary"></a><span data-ttu-id="3dca6-108">建立路線</span><span class="sxs-lookup"><span data-stu-id="3dca6-108">Create an itinerary</span></span>  
  
1.  <span data-ttu-id="3dca6-109">在 [方案總管] 中，以滑鼠右鍵按一下 C# 專案名稱，指向**新增**，然後按一下**新路線**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-109">In Solution Explorer, right-click the C# project name, point to **Add**, and then click **New Itinerary**.</span></span>  
  
2.  <span data-ttu-id="3dca6-110">在 **名稱**方塊底部的  對話方塊中，輸入路線，名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-110">In the **Name** box at the bottom of the dialog box, type the name for the itinerary, and then click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3dca6-111">建立並顯示在路線設計工具中，新的路線，並建立對應的.itinerary 檔並將其顯示在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="3dca6-111">The new itinerary is created and displayed in Itinerary Designer, and a corresponding .itinerary file is created and displayed in Solution Explorer.</span></span>  
  
#### <a name="add-an-existing-itinerary-to-the-project"></a><span data-ttu-id="3dca6-112">加入專案中的現有路線</span><span class="sxs-lookup"><span data-stu-id="3dca6-112">Add an existing itinerary to the project</span></span>
  
1.  <span data-ttu-id="3dca6-113">在 [方案總管] 中，以滑鼠右鍵按一下 C# 專案名稱，指向**新增**，然後按一下**現有項目**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-113">In Solution explorer, right click the C# project name, point to **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="3dca6-114">在 **加入現有項目** 對話方塊中，瀏覽至目錄，其中包含路線，按一下 路線，然後**新增**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-114">In the **Add Existing Item** dialog box, navigate to the directory that contains the itinerary, click the itinerary, and then click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3dca6-115">以路線為加入至專案。</span><span class="sxs-lookup"><span data-stu-id="3dca6-115">The itinerary is added to the project.</span></span>  
  
#### <a name="change-the-name-of-an-itinerary"></a><span data-ttu-id="3dca6-116">路線的名稱變更</span><span class="sxs-lookup"><span data-stu-id="3dca6-116">Change the name of an itinerary</span></span>  
  
1.  <span data-ttu-id="3dca6-117">在 [方案總管] 中，以滑鼠右鍵按一下您想要重新命名，然後按一下.itinerary 檔案**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-117">In Solution Explorer, right-click the .itinerary file you want to rename, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="3dca6-118">輸入新的檔案名稱，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="3dca6-118">Type the new file name, and then press ENTER.</span></span>  
  
#### <a name="save-an-itinerary"></a><span data-ttu-id="3dca6-119">儲存路線</span><span class="sxs-lookup"><span data-stu-id="3dca6-119">Save an itinerary</span></span>  
  
<span data-ttu-id="3dca6-120">在 **檔案**功能表上，按一下**儲存\<路線名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-120">On the **File** menu, click **Save \<itinerary name\>**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3dca6-121">路線的檔案會儲存為 DSL 模型中對應的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="3dca6-121">Itinerary files are saved as DSL models in corresponding XML format.</span></span>  
  
#### <a name="set-itinerary-export-properties"></a><span data-ttu-id="3dca6-122">設定路線的匯出屬性</span><span class="sxs-lookup"><span data-stu-id="3dca6-122">Set itinerary export properties</span></span>  
  
1. <span data-ttu-id="3dca6-123">在 [屬性] 視窗中，輸入**名稱**屬性。</span><span class="sxs-lookup"><span data-stu-id="3dca6-123">In the Properties window, type a **Name** property.</span></span>  
  
2. <span data-ttu-id="3dca6-124">在 [屬性] 視窗中，輸入**版本**屬性。</span><span class="sxs-lookup"><span data-stu-id="3dca6-124">In the Properties window, type a **Version** property.</span></span>  
  
3. <span data-ttu-id="3dca6-125">在 [屬性] 視窗中，指定**是要求回應**使用下拉式清單的屬性。</span><span class="sxs-lookup"><span data-stu-id="3dca6-125">In the Properties window, specify the **Is Request Response** property using the drop-down list.</span></span> <span data-ttu-id="3dca6-126">將此屬性設定為**真**如果[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]匝道與通訊的用戶端應用程式使用要求-回應訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="3dca6-126">Set this property to **true** if the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] client application communicates with an on-ramp using request-response message exchange pattern.</span></span>  
  
4. <span data-ttu-id="3dca6-127">在 [屬性] 視窗中，設定**匯出模式**屬性設**預設**或是**Strict**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-127">In the Properties window, set the **Export Mode** property to **Default** or **Strict**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="3dca6-128">建立時[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]使用路線設計工具的路線**匯出模式**屬性可用來定義服務執行的位置。</span><span class="sxs-lookup"><span data-stu-id="3dca6-128">When creating [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itineraries using the Itinerary Designer, the **Export Mode** property can be used to define where the service will execute.</span></span> <span data-ttu-id="3dca6-129">設定**匯出模式**屬性設**Strict**確保路線服務會在其指定的容器中執行; 在此情況下，XML 路線中的每個路線服務有階段屬性，指定服務執行所在的管線。</span><span class="sxs-lookup"><span data-stu-id="3dca6-129">Setting the **Export Mode** property to **Strict** ensures that the itinerary service executes in its prescribed container; in this case, each itinerary service in the XML itinerary has a stage property that specifies the pipeline in which the service executes.</span></span> <span data-ttu-id="3dca6-130">如果這個屬性設定為**預設**、 建立相容於 Microsoft ESB 路線，使用指定的任何階段和路線服務執行規定的順序，但不是一定是所需的管線階段中。</span><span class="sxs-lookup"><span data-stu-id="3dca6-130">If this property is set to **Default**, an itinerary compatible with Microsoft ESB is created, with no stage specified, and the itinerary service executes in the order prescribed, but not necessarily in the pipeline stage desired.</span></span>  
  
#### <a name="export-an-itinerary-to-a-file"></a><span data-ttu-id="3dca6-131">匯出至檔案的路線</span><span class="sxs-lookup"><span data-stu-id="3dca6-131">Export an itinerary to a file</span></span>  
  
1.  <span data-ttu-id="3dca6-132">在 [屬性] 視窗中，按一下**XML 路線匯出工具**中**模型匯出工具**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="3dca6-132">In the Properties window, click **XML Itinerary Exporter** in the **Model Exporter** drop-down list.</span></span>  
  
2.  <span data-ttu-id="3dca6-133">在 [屬性] 視窗中，設定**路線 XML 檔案**屬性設為新值。</span><span class="sxs-lookup"><span data-stu-id="3dca6-133">In the Properties window, set the **Itinerary XML file** property to a new value.</span></span>  
  
#### <a name="export-an-itinerary-to-a-database"></a><span data-ttu-id="3dca6-134">匯出到資料庫的路線</span><span class="sxs-lookup"><span data-stu-id="3dca6-134">Export an itinerary to a database</span></span>  
  
1. <span data-ttu-id="3dca6-135">在 [屬性] 視窗中，按一下**資料庫路線匯出工具**中**模型匯出工具**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="3dca6-135">In the Properties window, click **Database Itinerary Exporter** in the **Model Exporter** drop-down list.</span></span>  
  
2. <span data-ttu-id="3dca6-136">在 [屬性] 視窗中，設定**路線資料庫**屬性以指向路線資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="3dca6-136">In the Properties window, set the **Itinerary Database** property connection string to point to the itinerary database.</span></span>  
  
3. <span data-ttu-id="3dca6-137">在 [屬性] 視窗中，設定**路線狀態**屬性設**已發佈**或是**部署**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-137">In the Properties window, set the **Itinerary Status** property to **Published** or **Deployed**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="3dca6-138">路線匯出至資料庫時**路線狀態**設為**已發佈**、 路線的會變成適用於[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]執行之前的時間之後的屬性設定為,**部署**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-138">When an itinerary is exported to a database with **Itinerary Status** set to **Published**, the itinerary will not become effective for the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] run time until after the property is set to **Deployed**.</span></span>  
  
## <a name="security-operations"></a><span data-ttu-id="3dca6-139">安全性作業</span><span class="sxs-lookup"><span data-stu-id="3dca6-139">Security Operations</span></span>  
 <span data-ttu-id="3dca6-140">使用路線設計工具，您可以保護機密資料，例如密碼和其他認證儲存在[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線，方法是加密此使用 X.509 憑證的資訊。</span><span class="sxs-lookup"><span data-stu-id="3dca6-140">By using the Itinerary Designer, you can protect sensitive information, such as passwords and other credentials stored in a [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary, by encrypting this information using X.509 certificates.</span></span>  
  
#### <a name="select-the-x509-certificate-for-an-itinerary"></a><span data-ttu-id="3dca6-141">選取 路線的 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="3dca6-141">Select the X.509 certificate for an itinerary</span></span>  
  
1.  <span data-ttu-id="3dca6-142">在路線設計工具屬性視窗中，依序展開**加密憑證**屬性，，然後按一下**存放區位置**下拉式清單，並選取**CurrentUser**或是**LocalMachine**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-142">In the Itinerary Designer Properties window, expand the **Encryption Certificate** property, and then click the **Store Location** drop-down list, and select the **CurrentUser** or **LocalMachine**.</span></span> <span data-ttu-id="3dca6-143">這將與目前的使用者或本機電腦關聯的 X.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3dca6-143">This associates the X.509 certificate store with the current user or the local computer.</span></span>  
  
2.  <span data-ttu-id="3dca6-144">在 [屬性] 視窗中，按一下**存放區名稱**下拉式清單，然後選取其對應至您的憑證存放區的值。</span><span class="sxs-lookup"><span data-stu-id="3dca6-144">In the Properties window, click the **Store Name** drop-down list and select the value which corresponds to your certificate store.</span></span>  
  
3.  <span data-ttu-id="3dca6-145">在 [屬性] 視窗中，按一下 [加密憑證屬性旁的省略符號按鈕 （...），然後選取**X.509 憑證**中**選取憑證**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3dca6-145">In the Properties window, click the ellipsis button (...) next to the Encryption Certificate property, and then select the **X.509 certificate** in the **Select Certificate** dialog box.</span></span>  
  
#### <a name="remove-the-x509-certificate-from-an-itinerary"></a><span data-ttu-id="3dca6-146">移除路線的 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="3dca6-146">Remove the X.509 certificate from an itinerary</span></span>  
  
- <span data-ttu-id="3dca6-147">在路線設計工具屬性視窗中，依序展開**加密憑證**屬性，然後再把**存放區位置**屬性設為不同的值。</span><span class="sxs-lookup"><span data-stu-id="3dca6-147">In the Itinerary Designer Properties window, expand the **Encryption Certificate** property, and then set the **Store Location** property to a different value.</span></span> <span data-ttu-id="3dca6-148">此解除關聯的舊憑證[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線的模型。</span><span class="sxs-lookup"><span data-stu-id="3dca6-148">This disassociates the old certificate with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary model.</span></span>  
  
#### <a name="disable-the-x509-certificate-validation"></a><span data-ttu-id="3dca6-149">停用的 X.509 憑證驗證</span><span class="sxs-lookup"><span data-stu-id="3dca6-149">Disable the X.509 certificate validation</span></span>  
  
<span data-ttu-id="3dca6-150">在登錄編輯器中，移至子機碼**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk ESB Toolkit\2.0\Designer**，然後將**RequireX509Certificate**屬性值，以**false**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-150">In the Registry Editor, go to the subkey **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk ESB Toolkit\2.0\Designer**, and then set the **RequireX509Certificate** property value to **false**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3dca6-151">如果您已安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]子機碼是具有 64 位元支援作業系統上**HKEY_LOCAL_MACHINE\SOFTWARE\SysWOW64\Microsoft\BizTalk ESB Toolkit\2.0\Designer**。</span><span class="sxs-lookup"><span data-stu-id="3dca6-151">If you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] on an operating system that has 64-bit support, the subkey is **HKEY_LOCAL_MACHINE\SOFTWARE\SysWOW64\Microsoft\BizTalk ESB Toolkit\2.0\Designer**.</span></span>