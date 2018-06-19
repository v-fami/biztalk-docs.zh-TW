---
title: 連接到 Visual Studio 中使用 新增配接器中繼資料精靈中的 Oracle E-business Suite |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4fadc722-0098-457e-a2e2-3e9cc96eab5e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5950b9ea6a0f5fc9856720202059cf1fd058a251
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216206"
---
# <a name="connect-to-oracle-e-business-suite-in-visual-studio-using-add-adapter-metadata-wizard"></a><span data-ttu-id="526cf-102">連接到 Oracle E-business Suite，在 Visual Studio 中使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="526cf-102">Connect to Oracle E-Business Suite in Visual Studio using Add Adapter Metadata Wizard</span></span>
<span data-ttu-id="526cf-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]也會公開成 BizTalk 配接器，因此，您可以使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述您想要在 Oracle E-business Suite 使用配接器上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="526cf-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is also exposed as a BizTalk adapter and, therefore, you can use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate schema for the operations you want to perform on Oracle E-Business Suite using the adapter.</span></span>  
  
## <a name="connecting-to-oracle-e-business-suite-using-the-add-adapter-metadata-wizard"></a><span data-ttu-id="526cf-104">連接到 Oracle E-business Suite 使用新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="526cf-104">Connecting to Oracle E-Business Suite Using the Add Adapter Metadata Wizard</span></span>  
 <span data-ttu-id="526cf-105">執行下列步驟來連接 Oracle E-business Suite 使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="526cf-105">Perform the following steps to connect to Oracle E-Business Suite using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
#### <a name="to-connect-to-oracle-e-business-suite"></a><span data-ttu-id="526cf-106">若要連接到 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="526cf-106">To connect to Oracle E-Business Suite</span></span>  
  
1.  <span data-ttu-id="526cf-107">若要使用連接[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]BizTalk 解決方案中：</span><span class="sxs-lookup"><span data-stu-id="526cf-107">To connect using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in a BizTalk solution:</span></span>  
  
    1.  <span data-ttu-id="526cf-108">建立使用 Visual Studio BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="526cf-108">Create a BizTalk project using Visual Studio.</span></span>  
  
    2.  <span data-ttu-id="526cf-109">以滑鼠右鍵按一下方案總管] 中的專案，指向**新增**，然後按一下 [**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="526cf-109">Right-click the project in Solution Explorer, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
    3.  <span data-ttu-id="526cf-110">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="526cf-110">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
        |<span data-ttu-id="526cf-111">使用</span><span class="sxs-lookup"><span data-stu-id="526cf-111">Use this</span></span>|<span data-ttu-id="526cf-112">動作</span><span class="sxs-lookup"><span data-stu-id="526cf-112">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="526cf-113">**類別**</span><span class="sxs-lookup"><span data-stu-id="526cf-113">**Categories**</span></span>|<span data-ttu-id="526cf-114">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="526cf-114">Click **Add Adapter**.</span></span>|  
        |<span data-ttu-id="526cf-115">**範本**</span><span class="sxs-lookup"><span data-stu-id="526cf-115">**Templates**</span></span>|<span data-ttu-id="526cf-116">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="526cf-116">Click **Add Adapter Metadata**.</span></span>|  
  
    4.  <span data-ttu-id="526cf-117">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="526cf-117">Click **Add**.</span></span> <span data-ttu-id="526cf-118">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="526cf-118">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
    5.  <span data-ttu-id="526cf-119">在[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取**Wcf-oracleebs**。</span><span class="sxs-lookup"><span data-stu-id="526cf-119">In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select **WCF-OracleEBS**.</span></span> <span data-ttu-id="526cf-120">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="526cf-120">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="526cf-121">如果您已設定在 BizTalk Wcf-oracleebs 連接埠，選取從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="526cf-121">If you already have a WCF-OracleEBS port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
    6.  <span data-ttu-id="526cf-122">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="526cf-122">Click **Next**.</span></span>  
  
2.  <span data-ttu-id="526cf-123">從**選取繫結**下拉式清單中選取**oracleEBSBinding**按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="526cf-123">From the **Select a binding** drop-down list, select **oracleEBSBinding** and click **Configure**.</span></span>  
  
3.  <span data-ttu-id="526cf-124">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼，以連接到 Oracle E-business Suite 的資訊。</span><span class="sxs-lookup"><span data-stu-id="526cf-124">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Oracle E-Business Suite.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="526cf-125">使用</span><span class="sxs-lookup"><span data-stu-id="526cf-125">Use this</span></span>|<span data-ttu-id="526cf-126">動作</span><span class="sxs-lookup"><span data-stu-id="526cf-126">To do this</span></span>|  
    |<span data-ttu-id="526cf-127">**若要使用 Oracle 資料庫的認證進行連接**</span><span class="sxs-lookup"><span data-stu-id="526cf-127">**To connect using Oracle database credentials**</span></span>|<span data-ttu-id="526cf-128">指定**ClientCredentialType**內容繫結至**資料庫**和指定的資料庫認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="526cf-128">Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.</span></span>|  
    |<span data-ttu-id="526cf-129">**使用 Oracle E-business Suite 認證進行連接**</span><span class="sxs-lookup"><span data-stu-id="526cf-129">**To connect using Oracle E-Business Suite credentials**</span></span>|<span data-ttu-id="526cf-130">指定**ClientCredentialType**內容繫結至**EBusiness**指定 Oracle E-business Suite 認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="526cf-130">Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes.</span></span> <span data-ttu-id="526cf-131">在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**和**OraclePassword**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="526cf-131">In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.</span></span>|  
    |<span data-ttu-id="526cf-132">**如果 ClientCredentialType 設定為 「 資料庫 」，請使用 Windows 驗證進行連接**</span><span class="sxs-lookup"><span data-stu-id="526cf-132">**To connect using Windows Authentication if ClientCredentialType is set to “Database”**</span></span>|<span data-ttu-id="526cf-133">指定"/"表示**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="526cf-133">Specify a “/” for the **User name** text box and leave the **Password** text box blank.</span></span>|  
    |<span data-ttu-id="526cf-134">**如果 ClientCredentialType 設定為"EBusiness 「 使用 Windows 驗證進行連接**</span><span class="sxs-lookup"><span data-stu-id="526cf-134">**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**</span></span>|<span data-ttu-id="526cf-135">指定 Oracle E-business Suite 認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="526cf-135">Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes.</span></span> <span data-ttu-id="526cf-136">您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="526cf-136">You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.</span></span>|  
  
4.  <span data-ttu-id="526cf-137">按一下**URI 屬性**索引標籤，然後指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="526cf-137">Click the **URI Properties** tab, and specify values for the connection parameters.</span></span> <span data-ttu-id="526cf-138">如需有關連線 URI 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md))。</span><span class="sxs-lookup"><span data-stu-id="526cf-138">For more information about the connection URI for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Create the Oracle E-Business Suite connection URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="526cf-139">如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。</span><span class="sxs-lookup"><span data-stu-id="526cf-139">If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters.</span></span> <span data-ttu-id="526cf-140">不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="526cf-140">However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.</span></span>  
  
5.  <span data-ttu-id="526cf-141">按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="526cf-141">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="526cf-142">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="526cf-142">For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="526cf-143">如果產生的中繼資料使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]且您選取現有的 Wcf-oracleebs 傳送埠，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="526cf-143">If you are generating metadata using [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] and you selected an existing WCF-OracleEBS send port, you need not specify the binding properties.</span></span> <span data-ttu-id="526cf-144">繫結屬性是從傳送埠組態中挑選。</span><span class="sxs-lookup"><span data-stu-id="526cf-144">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="526cf-145">不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="526cf-145">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="526cf-146">在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="526cf-146">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="526cf-147">不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="526cf-147">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  
  
6.  <span data-ttu-id="526cf-148">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="526cf-148">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="526cf-149">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="526cf-149">Click **Connect**.</span></span> <span data-ttu-id="526cf-150">建立連接之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="526cf-150">After the connection is established, the connection status is shown as **Connected**.</span></span>  
  
     <span data-ttu-id="526cf-151">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。</span><span class="sxs-lookup"><span data-stu-id="526cf-151">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span>  
  
     <span data-ttu-id="526cf-152">![使用配接器服務對話方塊](../../adapters-and-accelerators/adapter-oracle-ebs/media/6a2b21ed-0fd2-4874-a6a6-e59a467533f8.gif "6a2b21ed-0fd2-4874-a6a6-e59a467533f8")</span><span class="sxs-lookup"><span data-stu-id="526cf-152">![Consume Adapter Service dialog box](../../adapters-and-accelerators/adapter-oracle-ebs/media/6a2b21ed-0fd2-4874-a6a6-e59a467533f8.gif "6a2b21ed-0fd2-4874-a6a6-e59a467533f8")</span></span>  
  
     <span data-ttu-id="526cf-153">[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]顯示不同的節點包含各種可以 Oracle E-business Suite 和 Oracle 資料庫執行的作業。</span><span class="sxs-lookup"><span data-stu-id="526cf-153">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] displays different nodes containing various operations that can be performed on the Oracle E-Business Suite and the Oracle database.</span></span> <span data-ttu-id="526cf-154">如需有關如何在不同的節點下的中繼資料的分類方式的詳細資訊，請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中使用 新增配接器中繼資料精靈](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-metadata-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="526cf-154">For more information on how the metadata is categorized under the various nodes, see [Connect to Oracle E-Business Suite in Visual Studio using Add Adapter Metadata Wizard](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-metadata-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="526cf-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="526cf-155">See Also</span></span>  
 <span data-ttu-id="526cf-156">[連接到 Oracle E-business Suite，Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="526cf-156">[Connect to the Oracle E-Business Suite in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) </span></span>  
 [<span data-ttu-id="526cf-157">連接到 Oracle E-business Suite 使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="526cf-157">Connect to Oracle E-Business Suite using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)