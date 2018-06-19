---
title: 設定 Oracle 資料庫配接器的連線 URI |Microsoft 文件
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
ms.openlocfilehash: 63cede1957c2f5f34396bbe2251a98cfc3965e7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216942"
---
# <a name="configure-the-connection-uri-for-the-oracle-database-adapter"></a><span data-ttu-id="f94bf-102">設定 Oracle 資料庫配接器的連線 URI</span><span class="sxs-lookup"><span data-stu-id="f94bf-102">Configure the connection URI for the Oracle Database adapter</span></span>
<span data-ttu-id="f94bf-103">連線 URI 是連接字串，其中包含連接到 Oracle 資料庫所需的參數。</span><span class="sxs-lookup"><span data-stu-id="f94bf-103">A connection URI is a connection string that contains parameters required to connect to the Oracle database.</span></span> <span data-ttu-id="f94bf-104">同時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定要連接到 Oracle 資料庫產生的中繼資料的 URI。</span><span class="sxs-lookup"><span data-stu-id="f94bf-104">While using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the URI to connect to the Oracle database to generate the metadata.</span></span> <span data-ttu-id="f94bf-105">設定協調流程使用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定要連接到 Oracle 資料庫執行作業的 URI。</span><span class="sxs-lookup"><span data-stu-id="f94bf-105">While configuring an orchestration using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the URI to connect to the Oracle database to perform operations.</span></span>  
  
## <a name="specifying-the-connection-uri-from-visual-studio"></a><span data-ttu-id="f94bf-106">指定連線 URI，從 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f94bf-106">Specifying the Connection URI from Visual Studio</span></span>  
 <span data-ttu-id="f94bf-107">從 Visual Studio 中，您必須指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f94bf-107">From Visual Studio, you must specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
#### <a name="to-specify-the-connection-uri-using-consume-adapter-service-add-in"></a><span data-ttu-id="f94bf-108">若要指定使用配接器服務增益集所使用的連線 URI</span><span class="sxs-lookup"><span data-stu-id="f94bf-108">To specify the Connection URI using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="f94bf-109">以滑鼠右鍵按一下您的 BizTalk 專案，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-109">Right-click your BizTalk project, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="f94bf-110">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f94bf-110">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="f94bf-111">使用</span><span class="sxs-lookup"><span data-stu-id="f94bf-111">Use this</span></span>|<span data-ttu-id="f94bf-112">動作</span><span class="sxs-lookup"><span data-stu-id="f94bf-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f94bf-113">**類別**</span><span class="sxs-lookup"><span data-stu-id="f94bf-113">**Categories**</span></span>|<span data-ttu-id="f94bf-114">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-114">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="f94bf-115">**範本**</span><span class="sxs-lookup"><span data-stu-id="f94bf-115">**Templates**</span></span>|<span data-ttu-id="f94bf-116">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-116">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="f94bf-117">若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-117">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="f94bf-118">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**oracleDBBinding**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-118">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and click **Configure**.</span></span>  
  
5.  <span data-ttu-id="f94bf-119">在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連接到 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="f94bf-119">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Oracle database:</span></span>  
  
    -   <span data-ttu-id="f94bf-120">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f94bf-120">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
    -   <span data-ttu-id="f94bf-121">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="f94bf-121">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
6.  <span data-ttu-id="f94bf-122">按一下**URI 屬性**索引標籤，然後指定不同參數的值。</span><span class="sxs-lookup"><span data-stu-id="f94bf-122">Click the **URI Properties** tab, and specify values for different parameters.</span></span> <span data-ttu-id="f94bf-123">如需有關連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="f94bf-123">For more information about the connection URI for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
7.  <span data-ttu-id="f94bf-124">按一下**繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需的。</span><span class="sxs-lookup"><span data-stu-id="f94bf-124">Click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema.</span></span> <span data-ttu-id="f94bf-125">如需繫結屬性的詳細資訊，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="f94bf-125">For more information about binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
8.  <span data-ttu-id="f94bf-126">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-126">Click **OK**.</span></span>  
  
#### <a name="to-specify-the-connection-uri-using-add-adapter-metadata-wizard"></a><span data-ttu-id="f94bf-127">若要指定連線 URI，使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="f94bf-127">To specify the Connection URI using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="f94bf-128">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-128">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="f94bf-129">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f94bf-129">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="f94bf-130">使用</span><span class="sxs-lookup"><span data-stu-id="f94bf-130">Use this</span></span>|<span data-ttu-id="f94bf-131">動作</span><span class="sxs-lookup"><span data-stu-id="f94bf-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f94bf-132">**類別**</span><span class="sxs-lookup"><span data-stu-id="f94bf-132">**Categories**</span></span>|<span data-ttu-id="f94bf-133">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-133">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="f94bf-134">**範本**</span><span class="sxs-lookup"><span data-stu-id="f94bf-134">**Templates**</span></span>|<span data-ttu-id="f94bf-135">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-135">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="f94bf-136">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-136">Click **Add**.</span></span> <span data-ttu-id="f94bf-137">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f94bf-137">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="f94bf-138">在[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取**Wcf-oracledb**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-138">In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select **WCF-OracleDB**.</span></span> <span data-ttu-id="f94bf-139">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="f94bf-139">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f94bf-140">如果您已設定在 BizTalk Wcf-oracledb 連接埠，選取從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="f94bf-140">If you already have a WCF-OracleDB port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="f94bf-141">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-141">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="f94bf-142">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**oracleDBBinding**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="f94bf-142">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="f94bf-143">在**設定配接器**對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**清單中，選取**Username**和指定使用者名稱和密碼來連接到 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="f94bf-143">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** list, select **Username** and specify the user name and password to connect to the Oracle database:</span></span>  
  
    -   <span data-ttu-id="f94bf-144">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f94bf-144">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
    -   <span data-ttu-id="f94bf-145">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="f94bf-145">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
8.  <span data-ttu-id="f94bf-146">按一下**URI 屬性**索引標籤，然後指定不同參數的值。</span><span class="sxs-lookup"><span data-stu-id="f94bf-146">Click the **URI Properties** tab, and specify values for different parameters.</span></span> <span data-ttu-id="f94bf-147">如需有關連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="f94bf-147">For more information about the connection URI for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
9. <span data-ttu-id="f94bf-148">按一下**繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需的。</span><span class="sxs-lookup"><span data-stu-id="f94bf-148">Click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema.</span></span> <span data-ttu-id="f94bf-149">如需繫結屬性的詳細資訊，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="f94bf-149">For more information about binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
10. <span data-ttu-id="f94bf-150">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-150">Click **OK**.</span></span>  
  
## <a name="specifying-the-connection-uri-from-the-biztalk-server-administration-console"></a><span data-ttu-id="f94bf-151">指定連線 URI 從 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="f94bf-151">Specifying the Connection URI from the BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="f94bf-152">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定認證，Wcf-custom 或 Wcf-oracledb 的連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="f94bf-152">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the credentials as part of the WCF-Custom or WCF-OracleDB port configuration.</span></span>  
  
#### <a name="to-specify-the-connection-uri-for-the-wcf-custom-port"></a><span data-ttu-id="f94bf-153">若要指定 WCF 自訂連接埠的連線 URI</span><span class="sxs-lookup"><span data-stu-id="f94bf-153">To specify the Connection URI for the WCF-Custom Port</span></span>  
  
1.  <span data-ttu-id="f94bf-154">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f94bf-154">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="f94bf-155">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-155">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="f94bf-156">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f94bf-156">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="f94bf-157">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-157">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="f94bf-158">傳送埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f94bf-158">For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="f94bf-159">選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f94bf-159">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an Oracle database.</span></span>  
  
        -   <span data-ttu-id="f94bf-160">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f94bf-160">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="f94bf-161">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="f94bf-161">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="f94bf-162">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f94bf-162">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
5.  <span data-ttu-id="f94bf-163">接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f94bf-163">For a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="f94bf-164">選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f94bf-164">Select **User account** option, and specify the user name and password to connect to an Oracle database.</span></span>  
  
        -   <span data-ttu-id="f94bf-165">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f94bf-165">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="f94bf-166">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="f94bf-166">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="f94bf-167">選取**取得認證從分支機構應用程式**選項，並指定分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="f94bf-167">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  
  
6.  <span data-ttu-id="f94bf-168">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-168">Click **OK**.</span></span>  
  
#### <a name="to-specify-the-connection-uri-for-the-wcf-oracledb-port"></a><span data-ttu-id="f94bf-169">若要指定 Wcf-oracledb 連接埠的連線 URI</span><span class="sxs-lookup"><span data-stu-id="f94bf-169">To specify the Connection URI for the WCF-OracleDB port</span></span>  
  
1.  <span data-ttu-id="f94bf-170">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f94bf-170">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="f94bf-171">新增 Wcf-oracledb 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f94bf-171">Add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="f94bf-172">如需指示，請參閱[將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="f94bf-172">For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="f94bf-173">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-173">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="f94bf-174">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f94bf-174">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="f94bf-175">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-oracledb**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-175">In the port properties dialog box, from the **Type** drop-down list, select **WCF-OracleDB**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f94bf-176">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-176">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="f94bf-177">在 連接埠屬性 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-177">In the port properties dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **oracleDBBinding**.</span></span>  
  
6.  <span data-ttu-id="f94bf-178">如果您要建立傳送埠，在 [傳輸屬性] 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f94bf-178">If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="f94bf-179">選取**不會使用單一登入**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f94bf-179">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the Oracle database.</span></span>  
  
        -   <span data-ttu-id="f94bf-180">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f94bf-180">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="f94bf-181">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="f94bf-181">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="f94bf-182">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f94bf-182">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
7.  <span data-ttu-id="f94bf-183">如果您要建立接收埠，在 [傳輸屬性] 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f94bf-183">If you are creating a receive port, in the transport properties dialog box, click the **Other** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="f94bf-184">選取**使用者帳戶**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f94bf-184">Select **User account** option, and specify the user name and password to connect to the Oracle database.</span></span>  
  
        -   <span data-ttu-id="f94bf-185">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f94bf-185">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="f94bf-186">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="f94bf-186">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="f94bf-187">選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="f94bf-187">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
8.  <span data-ttu-id="f94bf-188">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f94bf-188">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f94bf-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f94bf-189">See Also</span></span>  
<span data-ttu-id="f94bf-190">[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) </span><span class="sxs-lookup"><span data-stu-id="f94bf-190">[Building Blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) </span></span>  
 [<span data-ttu-id="f94bf-191">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="f94bf-191">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)