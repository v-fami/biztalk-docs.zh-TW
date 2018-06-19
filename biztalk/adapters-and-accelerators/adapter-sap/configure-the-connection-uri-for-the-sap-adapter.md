---
title: 設定 SAP 配接器的連線 URI |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection URI, specifying at run time
- connection URI, specifying at design time
ms.assetid: 8df8e4a7-13f7-48c0-8af2-451253ced7e7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b614f3a300dbda213cd45ba7eaf9215802bc48c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218534"
---
# <a name="configure-the-connection-uri-for-the-sap-adapter"></a><span data-ttu-id="ec5c2-102">設定 SAP 配接器的連線 URI</span><span class="sxs-lookup"><span data-stu-id="ec5c2-102">Configure the connection URI for the SAP adapter</span></span>
<span data-ttu-id="ec5c2-103">連線 URI 是連接至 SAP 系統的連接字串。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-103">A connection URI is a connection string to connect to an SAP system.</span></span> <span data-ttu-id="ec5c2-104">它包含各種建立與 SAP 系統的連線所需的參數。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-104">It contains various parameters required to establish connection with an SAP system.</span></span> <span data-ttu-id="ec5c2-105">在設計階段，您必須指定要連接到 SAP 系統產生的中繼資料的 URI。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-105">At design time, you must specify the URI to connect to the SAP system to generate the metadata.</span></span> <span data-ttu-id="ec5c2-106">在執行階段，您必須指定要連接到 SAP 系統，來執行作業的 URI。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-106">At run time, you must specify the URI to connect to the SAP system to perform operations.</span></span>  
  
## <a name="enter-the-connection-uri-at-design-time"></a><span data-ttu-id="ec5c2-107">輸入在設計階段的連線 URI</span><span class="sxs-lookup"><span data-stu-id="ec5c2-107">Enter the connection URI at design time</span></span>  
 <span data-ttu-id="ec5c2-108">設計階段，您可以指定連線 URI 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-108">For design time, you can specify the connection URI using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
### <a name="enter-the-connection-uri-using-consume-adapter-service-add-in"></a><span data-ttu-id="ec5c2-109">輸入的連接使用配接器服務增益集所使用的 URI</span><span class="sxs-lookup"><span data-stu-id="ec5c2-109">Enter the connection URI using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="ec5c2-110">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-110">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="ec5c2-111">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ec5c2-111">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="ec5c2-112">使用</span><span class="sxs-lookup"><span data-stu-id="ec5c2-112">Use this</span></span>|<span data-ttu-id="ec5c2-113">動作</span><span class="sxs-lookup"><span data-stu-id="ec5c2-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ec5c2-114">**類別**</span><span class="sxs-lookup"><span data-stu-id="ec5c2-114">**Categories**</span></span>|<span data-ttu-id="ec5c2-115">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-115">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="ec5c2-116">**範本**</span><span class="sxs-lookup"><span data-stu-id="ec5c2-116">**Templates**</span></span>|<span data-ttu-id="ec5c2-117">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-117">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="ec5c2-118">若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-118">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="ec5c2-119">在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中，選取**sapBinding**，然後按一下**設定**.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-119">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **sapBinding**, and click **Configure**.</span></span>  
  
5.  <span data-ttu-id="ec5c2-120">在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤。從**用戶端認證類型**下拉式清單方塊中，選取**Username**並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-120">In the **Configure Adapter** dialog box, click the **Security** tab. From the **Client credential type** drop-down list boxes, select **Username** and specify the user name and password to connect to the SAP system.</span></span>  
  
6.  <span data-ttu-id="ec5c2-121">按一下**URI 屬性**索引標籤並指定不同參數的值。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-121">Click the **URI Properties** tab and specify values for different parameters.</span></span> <span data-ttu-id="ec5c2-122">如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-122">For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
7.  <span data-ttu-id="ec5c2-123">按一下**繫結屬性**索引標籤上，並指定繫結值，如果有的話，也就是產生結構描述之前必須指定。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-123">Click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema.</span></span> <span data-ttu-id="ec5c2-124">例如，您必須指定的值**GenerateFlatFileCompatibleIDoc**屬性，才能產生從 SAP 系統接收 IDOC 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-124">For example, you must specify a value for the **GenerateFlatFileCompatibleIDoc** property before generating schema for receiving IDOC from an SAP system.</span></span> <span data-ttu-id="ec5c2-125">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-125">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
8.  <span data-ttu-id="ec5c2-126">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-126">Click **OK**.</span></span>  
  
### <a name="enter-the-connection-uri-using-add-adapter-metadata-wizard"></a><span data-ttu-id="ec5c2-127">輸入連線 URI，使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="ec5c2-127">Enter the connection URI using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="ec5c2-128">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-128">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="ec5c2-129">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ec5c2-129">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="ec5c2-130">使用</span><span class="sxs-lookup"><span data-stu-id="ec5c2-130">Use this</span></span>|<span data-ttu-id="ec5c2-131">動作</span><span class="sxs-lookup"><span data-stu-id="ec5c2-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ec5c2-132">**類別**</span><span class="sxs-lookup"><span data-stu-id="ec5c2-132">**Categories**</span></span>|<span data-ttu-id="ec5c2-133">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-133">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="ec5c2-134">**範本**</span><span class="sxs-lookup"><span data-stu-id="ec5c2-134">**Templates**</span></span>|<span data-ttu-id="ec5c2-135">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-135">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="ec5c2-136">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-136">Click **Add**.</span></span> <span data-ttu-id="ec5c2-137">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-137">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="ec5c2-138">在 新增配接器精靈 中，選取  **WCF SAP**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-138">In the Add Adapter Wizard, select **WCF-SAP**.</span></span> <span data-ttu-id="ec5c2-139">選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-139">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ec5c2-140">如果您已經在 BizTalk 中設定 WCF SAP 連接埠，選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-140">If you already have a WCF-SAP port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="ec5c2-141">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-141">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="ec5c2-142">在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中，選取**sapBinding**，然後按一下**設定**.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-142">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **sapBinding**, and click **Configure**.</span></span>  
  
7.  <span data-ttu-id="ec5c2-143">在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤。從**用戶端認證類型**下拉式清單方塊中，選取**Username**並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-143">In the **Configure Adapter** dialog box, click the **Security** tab. From the **Client credential type** drop-down list boxes, select **Username** and specify the user name and password to connect to the SAP system.</span></span>  
  
8.  <span data-ttu-id="ec5c2-144">按一下**URI 屬性**索引標籤並指定不同參數的值。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-144">Click the **URI Properties** tab and specify values for different parameters.</span></span> <span data-ttu-id="ec5c2-145">如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-145">For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
9. <span data-ttu-id="ec5c2-146">按一下**繫結屬性**索引標籤上，並指定繫結值，如果有的話，也就是產生結構描述之前必須指定。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-146">Click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema.</span></span> <span data-ttu-id="ec5c2-147">例如，您必須指定的值**GenerateFlatFileCompatibleIDoc**屬性，才能產生從 SAP 系統接收 IDOC 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-147">For example, you must specify a value for the **GenerateFlatFileCompatibleIDoc** property before generating schema for receiving IDOC from an SAP system.</span></span> <span data-ttu-id="ec5c2-148">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-148">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ec5c2-149">如果您選取現有的 WCF SAP 傳送埠時，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-149">If you selected an existing WCF-SAP send port, you need not specify the binding properties.</span></span> <span data-ttu-id="ec5c2-150">繫結屬性是從傳送埠組態中挑選。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-150">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="ec5c2-151">不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-151">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="ec5c2-152">在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-152">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="ec5c2-153">不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-153">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  
  
10. <span data-ttu-id="ec5c2-154">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-154">Click **OK**.</span></span>  
  
## <a name="enter-the-connection-uri-at-run-time"></a><span data-ttu-id="ec5c2-155">輸入連線 URI，在執行階段</span><span class="sxs-lookup"><span data-stu-id="ec5c2-155">Enter the connection URI at run time</span></span>  
 <span data-ttu-id="ec5c2-156">執行階段，您可以指定 URI 中的 WCF 自訂 」 或 「 WCF SAP 連接埠組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-156">For run time, you can specify the URI as part of the WCF-Custom or WCF-SAP port configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
### <a name="enter-the-connection-uri-for-the-wcf-custom-port"></a><span data-ttu-id="ec5c2-157">輸入 WCF 自訂連接埠的連線 URI</span><span class="sxs-lookup"><span data-stu-id="ec5c2-157">Enter the connection URI for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="ec5c2-158">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-158">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="ec5c2-159">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-159">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="ec5c2-160">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-160">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="ec5c2-161">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-161">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ec5c2-162">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-162">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="ec5c2-163">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-163">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="ec5c2-164">在**位址 (URI)** 文字方塊中，指定的連接來連接到 SAP 系統的 URI。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-164">In the **Address (URI)** text box, specify the connection URI to connect to the SAP system.</span></span> <span data-ttu-id="ec5c2-165">如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-165">For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
6.  <span data-ttu-id="ec5c2-166">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。從**繫結的型別**下拉式清單中，選取**sapBinding**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-166">In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **sapBinding**.</span></span>  
  
7.  <span data-ttu-id="ec5c2-167">如果您要建立傳送埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="ec5c2-167">If you are creating a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    1.  <span data-ttu-id="ec5c2-168">選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-168">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the SAP system.</span></span>  
  
    2.  <span data-ttu-id="ec5c2-169">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-169">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
8.  <span data-ttu-id="ec5c2-170">如果您要建立接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="ec5c2-170">If you are creating a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  
  
    1.  <span data-ttu-id="ec5c2-171">選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-171">Select **User account** option, and specify the user name and password to connect to the SAP system.</span></span>  
  
    2.  <span data-ttu-id="ec5c2-172">選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-172">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
9. <span data-ttu-id="ec5c2-173">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-173">Click **OK**.</span></span>  
  
### <a name="enter-the-connection-uri-for-the-wcf-sap-port"></a><span data-ttu-id="ec5c2-174">輸入 WCF SAP 連接埠的連線 URI</span><span class="sxs-lookup"><span data-stu-id="ec5c2-174">Enter the connection URI for the WCF-SAP port</span></span>  
  
1.  <span data-ttu-id="ec5c2-175">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-175">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="ec5c2-176">加入 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-176">Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="ec5c2-177">如需指示，請參閱[將 SAP 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-177">For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="ec5c2-178">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-178">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="ec5c2-179">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-179">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="ec5c2-180">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您之前，加入 WCF SAP 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-180">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ec5c2-181">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-181">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="ec5c2-182">在 傳輸屬性對話方塊中，按一下 **一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-182">In the transport properties dialog box, click the **General** tab.</span></span>  
  
6.  <span data-ttu-id="ec5c2-183">按一下**設定**按鈕，並提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-183">Click the **Configure** button and provide values for the connection parameters.</span></span> <span data-ttu-id="ec5c2-184">如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-184">For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
7.  <span data-ttu-id="ec5c2-185">在 傳輸屬性對話方塊中，按一下 **繫結**索引標籤上，並且指定繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-185">In the transport properties dialog box, click the **Binding** tab and specify values for binding properties.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ec5c2-186">根據您要設定傳送埠或接收埠會繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-186">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="ec5c2-187">比方說，繫結內容相關的輸入都無法使用作業時設定的傳送埠，因為輸入的操作需要接收埠組態。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-187">For example, binding properties related to inbound operations are not available while configuring a send port because inbound operations require a receive port configuration.</span></span>  
  
8.  <span data-ttu-id="ec5c2-188">如果您要建立傳送埠，在 [傳輸屬性] 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="ec5c2-188">If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    1.  <span data-ttu-id="ec5c2-189">選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-189">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the SAP system.</span></span>  
  
    2.  <span data-ttu-id="ec5c2-190">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-190">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
9. <span data-ttu-id="ec5c2-191">如果您要建立接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="ec5c2-191">If you are creating a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  
  
    1.  <span data-ttu-id="ec5c2-192">選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-192">Select **User account** option, and specify the user name and password to connect to the SAP system.</span></span>  
  
    2.  <span data-ttu-id="ec5c2-193">選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-193">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
10. <span data-ttu-id="ec5c2-194">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ec5c2-194">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec5c2-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec5c2-195">See Also</span></span>  
[<span data-ttu-id="ec5c2-196">若要建立的 SAP 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="ec5c2-196">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)