---
title: 設定登入認證，Oracle 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Enter the credentials
helpviewer_keywords:
- credentials, specifying at run time
- credentials, specifying at design time
ms.assetid: d8f62829-ce77-4d82-a411-2eeefb6fe75a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eda20ad4e04a9962e471ab98eb0bc5695b391007
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-sign-in-credentials-for-the-oracle-database"></a><span data-ttu-id="a5000-102">設定登入認證，Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="a5000-102">Configure the sign in credentials for the Oracle Database</span></span>
<span data-ttu-id="a5000-103">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]需要配接器用戶端提供用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="a5000-103">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] requires the adapter clients to provide client credentials.</span></span> <span data-ttu-id="a5000-104">配接器使用這些認證來驗證與 Oracle 資料庫使用者，並建立連接。</span><span class="sxs-lookup"><span data-stu-id="a5000-104">The adapter uses these credentials to authenticate the user with the Oracle database and to establish a connection.</span></span>  
  
 <span data-ttu-id="a5000-105">配接器用戶端可以使用時的用戶端認證同時提供[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以及何時使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a5000-105">Adapter clients can provide the client credentials both when using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and when using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="a5000-106">當使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，產生的中繼資料所需的認證。</span><span class="sxs-lookup"><span data-stu-id="a5000-106">When using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], credentials are required to generate the metadata.</span></span> <span data-ttu-id="a5000-107">當使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，不需要的認證來執行的 Oracle 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="a5000-107">When using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, credentials are required to perform operations on the Oracle database.</span></span> <span data-ttu-id="a5000-108">本主題提供有關指定在用戶端認證資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a5000-108">This topic provides information about specifying client credentials in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="specifying-client-credentials-from-visual-studio"></a><span data-ttu-id="a5000-109">指定從 Visual Studio 的用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="a5000-109">Specifying Client Credentials from Visual Studio</span></span>  
 <span data-ttu-id="a5000-110">從 Visual Studio 中，您必須指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a5000-110">From Visual Studio, you must specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
#### <a name="to-specify-credentials-using-consume-adapter-service-add-in"></a><span data-ttu-id="a5000-111">若要指定使用配接器服務增益集所使用的認證</span><span class="sxs-lookup"><span data-stu-id="a5000-111">To specify credentials using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="a5000-112">以滑鼠右鍵按一下您的 BizTalk 專案，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="a5000-112">Right-click your BizTalk project, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="a5000-113">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a5000-113">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="a5000-114">使用</span><span class="sxs-lookup"><span data-stu-id="a5000-114">Use this</span></span>|<span data-ttu-id="a5000-115">動作</span><span class="sxs-lookup"><span data-stu-id="a5000-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a5000-116">**類別**</span><span class="sxs-lookup"><span data-stu-id="a5000-116">**Categories**</span></span>|<span data-ttu-id="a5000-117">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="a5000-117">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="a5000-118">**範本**</span><span class="sxs-lookup"><span data-stu-id="a5000-118">**Templates**</span></span>|<span data-ttu-id="a5000-119">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="a5000-119">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="a5000-120">若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="a5000-120">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="a5000-121">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**oracleDBBinding**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="a5000-121">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and click **Configure**.</span></span>  
  
5.  <span data-ttu-id="a5000-122">在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連接到 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="a5000-122">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Oracle database:</span></span>  
  
    -   <span data-ttu-id="a5000-123">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a5000-123">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
    -   <span data-ttu-id="a5000-124">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="a5000-124">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
6.  <span data-ttu-id="a5000-125">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a5000-125">Click **OK**.</span></span>  
  
#### <a name="to-specify-credentials-using-add-adapter-metadata-wizard"></a><span data-ttu-id="a5000-126">若要指定認證，使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="a5000-126">To specify credentials using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="a5000-127">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="a5000-127">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="a5000-128">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a5000-128">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="a5000-129">使用</span><span class="sxs-lookup"><span data-stu-id="a5000-129">Use this</span></span>|<span data-ttu-id="a5000-130">動作</span><span class="sxs-lookup"><span data-stu-id="a5000-130">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a5000-131">**類別**</span><span class="sxs-lookup"><span data-stu-id="a5000-131">**Categories**</span></span>|<span data-ttu-id="a5000-132">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="a5000-132">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="a5000-133">**範本**</span><span class="sxs-lookup"><span data-stu-id="a5000-133">**Templates**</span></span>|<span data-ttu-id="a5000-134">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="a5000-134">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="a5000-135">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="a5000-135">Click **Add**.</span></span> <span data-ttu-id="a5000-136">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="a5000-136">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="a5000-137">在[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取**Wcf-oracledb**。</span><span class="sxs-lookup"><span data-stu-id="a5000-137">In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select **WCF-OracleDB**.</span></span> <span data-ttu-id="a5000-138">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a5000-138">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a5000-139">如果您已設定在 BizTalk Wcf-oracledb 連接埠，選取從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="a5000-139">If you already have a WCF-OracleDB port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="a5000-140">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="a5000-140">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="a5000-141">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**oracleDBBinding**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="a5000-141">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="a5000-142">在**設定配接器**對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**清單中，選取**Username**和指定使用者名稱和密碼來連接到 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="a5000-142">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** list, select **Username** and specify the user name and password to connect to the Oracle database:</span></span>  
  
    -   <span data-ttu-id="a5000-143">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a5000-143">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
    -   <span data-ttu-id="a5000-144">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="a5000-144">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
8.  <span data-ttu-id="a5000-145">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a5000-145">Click **OK**.</span></span>  
  
## <a name="specifying-client-credentials-from-the-biztalk-server-administration-console"></a><span data-ttu-id="a5000-146">指定用戶端認證從 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="a5000-146">Specifying Client Credentials from the BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="a5000-147">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定認證，Wcf-custom 或 Wcf-oracledb 的連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="a5000-147">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the credentials as part of the WCF-Custom or WCF-OracleDB port configuration.</span></span>  
  
#### <a name="to-specify-client-credentials-for-the-wcf-custom-port"></a><span data-ttu-id="a5000-148">若要指定 WCF 自訂連接埠的用戶端認證</span><span class="sxs-lookup"><span data-stu-id="a5000-148">To specify client credentials for the WCF-Custom Port</span></span>  
  
1.  <span data-ttu-id="a5000-149">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a5000-149">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="a5000-150">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="a5000-150">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="a5000-151">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="a5000-151">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="a5000-152">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="a5000-152">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="a5000-153">傳送埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a5000-153">For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="a5000-154">選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a5000-154">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an Oracle database.</span></span>  
  
        -   <span data-ttu-id="a5000-155">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a5000-155">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="a5000-156">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="a5000-156">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="a5000-157">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a5000-157">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
5.  <span data-ttu-id="a5000-158">接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a5000-158">For a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="a5000-159">選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a5000-159">Select **User account** option, and specify the user name and password to connect to an Oracle database.</span></span>  
  
        -   <span data-ttu-id="a5000-160">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a5000-160">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="a5000-161">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="a5000-161">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="a5000-162">選取**取得認證從分支機構應用程式**選項，並指定分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="a5000-162">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  
  
6.  <span data-ttu-id="a5000-163">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a5000-163">Click **OK**.</span></span>  
  
#### <a name="to-specify-credentials-for-the-wcf-oracledb-port"></a><span data-ttu-id="a5000-164">若要指定認證 Wcf-oracledb 連接埠</span><span class="sxs-lookup"><span data-stu-id="a5000-164">To specify credentials for the WCF-OracleDB port</span></span>  
  
1.  <span data-ttu-id="a5000-165">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a5000-165">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="a5000-166">新增 Wcf-oracledb 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a5000-166">Add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="a5000-167">如需指示，請參閱[將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="a5000-167">For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="a5000-168">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="a5000-168">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="a5000-169">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="a5000-169">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="a5000-170">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-oracledb**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="a5000-170">In the port properties dialog box, from the **Type** drop-down list, select **WCF-OracleDB**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a5000-171">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="a5000-171">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="a5000-172">在 連接埠屬性 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="a5000-172">In the port properties dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **oracleDBBinding**.</span></span>  
  
6.  <span data-ttu-id="a5000-173">如果您要建立傳送埠，在 [傳輸屬性] 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a5000-173">If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="a5000-174">選取**不會使用單一登入**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a5000-174">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the Oracle database.</span></span>  
  
        -   <span data-ttu-id="a5000-175">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a5000-175">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="a5000-176">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="a5000-176">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="a5000-177">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a5000-177">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
7.  <span data-ttu-id="a5000-178">如果您要建立接收埠，在 [傳輸屬性] 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a5000-178">If you are creating a receive port, in the transport properties dialog box, click the **Other** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="a5000-179">選取**使用者帳戶**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a5000-179">Select **User account** option, and specify the user name and password to connect to the Oracle database.</span></span>  
  
        -   <span data-ttu-id="a5000-180">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a5000-180">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="a5000-181">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="a5000-181">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="a5000-182">選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="a5000-182">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
8.  <span data-ttu-id="a5000-183">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a5000-183">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5000-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5000-184">See Also</span></span>  
<span data-ttu-id="a5000-185">[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) </span><span class="sxs-lookup"><span data-stu-id="a5000-185">[Building Blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) </span></span>  
 [<span data-ttu-id="a5000-186">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="a5000-186">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)