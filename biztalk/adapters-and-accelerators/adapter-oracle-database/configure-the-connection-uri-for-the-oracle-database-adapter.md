---
title: 設定 Oracle 資料庫配接器的連線 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection URI, specifying at design time
- connection URI, specifying at run time
ms.assetid: 9f302b67-0bcc-44d1-9517-10d402873540
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 849adf16faa96726fb3d182930be8f4965eb180d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007205"
---
# <a name="configure-the-connection-uri-for-the-oracle-database-adapter"></a><span data-ttu-id="b0676-102">設定 Oracle 資料庫配接器的連線 URI</span><span class="sxs-lookup"><span data-stu-id="b0676-102">Configure the connection URI for the Oracle Database adapter</span></span>
<span data-ttu-id="b0676-103">連線 URI 會是包含參數，才能連接到 Oracle 資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="b0676-103">A connection URI is a connection string that contains parameters required to connect to the Oracle database.</span></span> <span data-ttu-id="b0676-104">在使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或是[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定要連接到 Oracle 資料庫產生的中繼資料的 URI。</span><span class="sxs-lookup"><span data-stu-id="b0676-104">While using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the URI to connect to the Oracle database to generate the metadata.</span></span> <span data-ttu-id="b0676-105">在設定協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定要連接到 Oracle 資料庫執行作業的 URI。</span><span class="sxs-lookup"><span data-stu-id="b0676-105">While configuring an orchestration using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the URI to connect to the Oracle database to perform operations.</span></span>  

## <a name="specifying-the-connection-uri-from-visual-studio"></a><span data-ttu-id="b0676-106">指定連線 URI，從 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b0676-106">Specifying the Connection URI from Visual Studio</span></span>  
 <span data-ttu-id="b0676-107">從 Visual Studio 中，您必須指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0676-107">From Visual Studio, you must specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  

#### <a name="to-specify-the-connection-uri-using-consume-adapter-service-add-in"></a><span data-ttu-id="b0676-108">若要指定使用配接器服務增益集所使用的連線 URI</span><span class="sxs-lookup"><span data-stu-id="b0676-108">To specify the Connection URI using Consume Adapter Service Add-in</span></span>  

1. <span data-ttu-id="b0676-109">以滑鼠右鍵按一下您的 BizTalk 專案，然後按**加入產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="b0676-109">Right-click your BizTalk project, and then select **Add Generated Items**.</span></span>  

2. <span data-ttu-id="b0676-110">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b0676-110">In the **Add Generated Items** dialog box, do the following:</span></span>  


   |    <span data-ttu-id="b0676-111">使用</span><span class="sxs-lookup"><span data-stu-id="b0676-111">Use this</span></span>    |             <span data-ttu-id="b0676-112">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="b0676-112">To do this</span></span>             |
   |----------------|------------------------------------|
   | <span data-ttu-id="b0676-113">**類別**</span><span class="sxs-lookup"><span data-stu-id="b0676-113">**Categories**</span></span> | <span data-ttu-id="b0676-114">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="b0676-114">Click **Consume Adapter Service**.</span></span> |
   | <span data-ttu-id="b0676-115">**範本**</span><span class="sxs-lookup"><span data-stu-id="b0676-115">**Templates**</span></span>  | <span data-ttu-id="b0676-116">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="b0676-116">Click **Consume Adapter Service**.</span></span> |


3. <span data-ttu-id="b0676-117">若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="b0676-117">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  

4. <span data-ttu-id="b0676-118">在**取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**oracleDBBinding**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="b0676-118">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and click **Configure**.</span></span>  

5. <span data-ttu-id="b0676-119">中**設定介面卡** 對話方塊中，按一下**安全性** 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連接到 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="b0676-119">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Oracle database:</span></span>  

   -   <span data-ttu-id="b0676-120">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-120">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

   -   <span data-ttu-id="b0676-121">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-121">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

6. <span data-ttu-id="b0676-122">按一下  **URI 屬性**索引標籤，然後指定不同參數的值。</span><span class="sxs-lookup"><span data-stu-id="b0676-122">Click the **URI Properties** tab, and specify values for different parameters.</span></span> <span data-ttu-id="b0676-123">如需有關連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="b0676-123">For more information about the connection URI for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  

7. <span data-ttu-id="b0676-124">按一下 **繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需。</span><span class="sxs-lookup"><span data-stu-id="b0676-124">Click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema.</span></span> <span data-ttu-id="b0676-125">如需有關繫結屬性的詳細資訊，請參閱 < [Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="b0676-125">For more information about binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  

8. <span data-ttu-id="b0676-126">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="b0676-126">Click **OK**.</span></span>  

#### <a name="to-specify-the-connection-uri-using-add-adapter-metadata-wizard"></a><span data-ttu-id="b0676-127">若要指定連線 URI，使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="b0676-127">To specify the Connection URI using Add Adapter Metadata Wizard</span></span>  

1. <span data-ttu-id="b0676-128">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="b0676-128">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  

2. <span data-ttu-id="b0676-129">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b0676-129">In the **Add Generated Items** dialog box, do the following:</span></span>  


   |    <span data-ttu-id="b0676-130">使用</span><span class="sxs-lookup"><span data-stu-id="b0676-130">Use this</span></span>    |           <span data-ttu-id="b0676-131">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="b0676-131">To do this</span></span>            |
   |----------------|---------------------------------|
   | <span data-ttu-id="b0676-132">**類別**</span><span class="sxs-lookup"><span data-stu-id="b0676-132">**Categories**</span></span> |     <span data-ttu-id="b0676-133">按一下 **新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="b0676-133">Click **Add Adapter**.</span></span>      |
   | <span data-ttu-id="b0676-134">**範本**</span><span class="sxs-lookup"><span data-stu-id="b0676-134">**Templates**</span></span>  | <span data-ttu-id="b0676-135">按一下 **新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="b0676-135">Click **Add Adapter Metadata**.</span></span> |


3. <span data-ttu-id="b0676-136">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="b0676-136">Click **Add**.</span></span> <span data-ttu-id="b0676-137">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="b0676-137">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  

4. <span data-ttu-id="b0676-138">在  [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取**Wcf-oracledb**。</span><span class="sxs-lookup"><span data-stu-id="b0676-138">In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select **WCF-OracleDB**.</span></span> <span data-ttu-id="b0676-139">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0676-139">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="b0676-140">如果您已經設定 biztalk Wcf-oracledb 連接埠，請選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="b0676-140">If you already have a WCF-OracleDB port configured in BizTalk, select the port from the **Port** list.</span></span>  

5. <span data-ttu-id="b0676-141">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="b0676-141">Click **Next**.</span></span>  

6. <span data-ttu-id="b0676-142">在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**oracleDBBinding**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="b0676-142">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and then click **Configure**.</span></span>  

7. <span data-ttu-id="b0676-143">在**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**清單中，選取**使用者名稱**和指定使用者名稱和密碼來連接到 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="b0676-143">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** list, select **Username** and specify the user name and password to connect to the Oracle database:</span></span>  

   -   <span data-ttu-id="b0676-144">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-144">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

   -   <span data-ttu-id="b0676-145">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-145">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

8. <span data-ttu-id="b0676-146">按一下  **URI 屬性**索引標籤，然後指定不同參數的值。</span><span class="sxs-lookup"><span data-stu-id="b0676-146">Click the **URI Properties** tab, and specify values for different parameters.</span></span> <span data-ttu-id="b0676-147">如需有關連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="b0676-147">For more information about the connection URI for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  

9. <span data-ttu-id="b0676-148">按一下 **繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需。</span><span class="sxs-lookup"><span data-stu-id="b0676-148">Click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema.</span></span> <span data-ttu-id="b0676-149">如需有關繫結屬性的詳細資訊，請參閱 < [Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="b0676-149">For more information about binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  

10. <span data-ttu-id="b0676-150">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="b0676-150">Click **OK**.</span></span>  

## <a name="specifying-the-connection-uri-from-the-biztalk-server-administration-console"></a><span data-ttu-id="b0676-151">指定連線 URI，從 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="b0676-151">Specifying the Connection URI from the BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="b0676-152">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定認證，Wcf-custom 或 Wcf-oracledb 的連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="b0676-152">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the credentials as part of the WCF-Custom or WCF-OracleDB port configuration.</span></span>  

#### <a name="to-specify-the-connection-uri-for-the-wcf-custom-port"></a><span data-ttu-id="b0676-153">若要指定 WCF 自訂連接埠的連線 URI</span><span class="sxs-lookup"><span data-stu-id="b0676-153">To specify the Connection URI for the WCF-Custom Port</span></span>  

1. <span data-ttu-id="b0676-154">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="b0676-154">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="b0676-155">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="b0676-155">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="b0676-156">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="b0676-156">In the right pane, you can choose to create a port or select an existing port.</span></span>  

3. <span data-ttu-id="b0676-157">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="b0676-157">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  

4. <span data-ttu-id="b0676-158">傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="b0676-158">For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  

   -   <span data-ttu-id="b0676-159">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b0676-159">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an Oracle database.</span></span>  

       -   <span data-ttu-id="b0676-160">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-160">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

       -   <span data-ttu-id="b0676-161">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-161">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

   -   <span data-ttu-id="b0676-162">選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="b0676-162">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  

5. <span data-ttu-id="b0676-163">接收埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="b0676-163">For a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  

   -   <span data-ttu-id="b0676-164">選取 **使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b0676-164">Select **User account** option, and specify the user name and password to connect to an Oracle database.</span></span>  

       -   <span data-ttu-id="b0676-165">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-165">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

       -   <span data-ttu-id="b0676-166">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-166">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

   -   <span data-ttu-id="b0676-167">選取 **取得認證，從分支機構應用程式**選項，並指定分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0676-167">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  

6. <span data-ttu-id="b0676-168">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="b0676-168">Click **OK**.</span></span>  

#### <a name="to-specify-the-connection-uri-for-the-wcf-oracledb-port"></a><span data-ttu-id="b0676-169">若要指定 Wcf-oracledb 連接埠的連線 URI</span><span class="sxs-lookup"><span data-stu-id="b0676-169">To specify the Connection URI for the WCF-OracleDB port</span></span>  

1. <span data-ttu-id="b0676-170">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="b0676-170">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="b0676-171">新增 Wcf-oracledb 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="b0676-171">Add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="b0676-172">如需相關指示，請參閱 <<c0> [ 將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="b0676-172">For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  

3. <span data-ttu-id="b0676-173">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="b0676-173">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="b0676-174">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="b0676-174">In the right pane, you can choose to create a port or select an existing port.</span></span>  

4. <span data-ttu-id="b0676-175">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-oracledb**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="b0676-175">In the port properties dialog box, from the **Type** drop-down list, select **WCF-OracleDB**, and then click **Configure**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="b0676-176">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="b0676-176">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  

5. <span data-ttu-id="b0676-177">在 連接埠屬性 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="b0676-177">In the port properties dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **oracleDBBinding**.</span></span>  

6. <span data-ttu-id="b0676-178">如果您要建立傳送埠，在傳輸屬性對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="b0676-178">If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab, and do one of the following:</span></span>  

   -   <span data-ttu-id="b0676-179">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b0676-179">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the Oracle database.</span></span>  

       -   <span data-ttu-id="b0676-180">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-180">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

       -   <span data-ttu-id="b0676-181">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-181">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

   -   <span data-ttu-id="b0676-182">選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="b0676-182">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  

7. <span data-ttu-id="b0676-183">如果您要建立接收埠，在傳輸屬性對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="b0676-183">If you are creating a receive port, in the transport properties dialog box, click the **Other** tab, and do one of the following:</span></span>  

   -   <span data-ttu-id="b0676-184">選取 **使用者帳戶**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b0676-184">Select **User account** option, and specify the user name and password to connect to the Oracle database.</span></span>  

       -   <span data-ttu-id="b0676-185">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-185">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

       -   <span data-ttu-id="b0676-186">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b0676-186">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

   -   <span data-ttu-id="b0676-187">選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0676-187">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  

8. <span data-ttu-id="b0676-188">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="b0676-188">Click **OK**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="b0676-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0676-189">See Also</span></span>  
<span data-ttu-id="b0676-190">[若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) </span><span class="sxs-lookup"><span data-stu-id="b0676-190">[Building Blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) </span></span>  
 [<span data-ttu-id="b0676-191">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="b0676-191">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)