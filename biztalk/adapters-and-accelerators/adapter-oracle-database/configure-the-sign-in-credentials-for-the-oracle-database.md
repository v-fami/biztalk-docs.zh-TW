---
title: 設定登入認證，Oracle 資料庫 |Microsoft Docs
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
ms.openlocfilehash: d6b19b79d05a925f02938669693c5eb92e9185b0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995655"
---
# <a name="configure-the-sign-in-credentials-for-the-oracle-database"></a><span data-ttu-id="398ae-102">設定登入認證，Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="398ae-102">Configure the sign in credentials for the Oracle Database</span></span>
<span data-ttu-id="398ae-103">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]需要配接器用戶端，以提供用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="398ae-103">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] requires the adapter clients to provide client credentials.</span></span> <span data-ttu-id="398ae-104">配接器會使用這些認證來驗證與 Oracle 資料庫使用者，並建立連線。</span><span class="sxs-lookup"><span data-stu-id="398ae-104">The adapter uses these credentials to authenticate the user with the Oracle database and to establish a connection.</span></span>  

 <span data-ttu-id="398ae-105">配接器用戶端可以提供使用時的用戶端認證兩者[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以及何時使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="398ae-105">Adapter clients can provide the client credentials both when using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and when using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="398ae-106">當使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，產生中繼資料所需的認證。</span><span class="sxs-lookup"><span data-stu-id="398ae-106">When using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], credentials are required to generate the metadata.</span></span> <span data-ttu-id="398ae-107">當使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，認證所需執行的 Oracle 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="398ae-107">When using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, credentials are required to perform operations on the Oracle database.</span></span> <span data-ttu-id="398ae-108">本主題提供有關指定在用戶端認證的詳細資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]而[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="398ae-108">This topic provides information about specifying client credentials in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

## <a name="specifying-client-credentials-from-visual-studio"></a><span data-ttu-id="398ae-109">指定用戶端認證從 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="398ae-109">Specifying Client Credentials from Visual Studio</span></span>  
 <span data-ttu-id="398ae-110">從 Visual Studio 中，您必須指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="398ae-110">From Visual Studio, you must specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  

#### <a name="to-specify-credentials-using-consume-adapter-service-add-in"></a><span data-ttu-id="398ae-111">若要指定使用配接器服務增益集所使用的認證</span><span class="sxs-lookup"><span data-stu-id="398ae-111">To specify credentials using Consume Adapter Service Add-in</span></span>  

1.  <span data-ttu-id="398ae-112">以滑鼠右鍵按一下您的 BizTalk 專案，然後按**加入產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="398ae-112">Right-click your BizTalk project, and then select **Add Generated Items**.</span></span>  

2.  <span data-ttu-id="398ae-113">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="398ae-113">In the **Add Generated Items** dialog box, do the following:</span></span>  

    |<span data-ttu-id="398ae-114">使用</span><span class="sxs-lookup"><span data-stu-id="398ae-114">Use this</span></span>|<span data-ttu-id="398ae-115">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="398ae-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="398ae-116">**類別**</span><span class="sxs-lookup"><span data-stu-id="398ae-116">**Categories**</span></span>|<span data-ttu-id="398ae-117">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="398ae-117">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="398ae-118">**範本**</span><span class="sxs-lookup"><span data-stu-id="398ae-118">**Templates**</span></span>|<span data-ttu-id="398ae-119">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="398ae-119">Click **Consume Adapter Service**.</span></span>|  

3.  <span data-ttu-id="398ae-120">若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="398ae-120">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  

4.  <span data-ttu-id="398ae-121">在**取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**oracleDBBinding**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="398ae-121">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and click **Configure**.</span></span>  

5.  <span data-ttu-id="398ae-122">中**設定介面卡** 對話方塊中，按一下**安全性** 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連接到 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="398ae-122">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Oracle database:</span></span>  

    -   <span data-ttu-id="398ae-123">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-123">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

    -   <span data-ttu-id="398ae-124">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-124">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

6.  <span data-ttu-id="398ae-125">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="398ae-125">Click **OK**.</span></span>  

#### <a name="to-specify-credentials-using-add-adapter-metadata-wizard"></a><span data-ttu-id="398ae-126">若要指定認證，使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="398ae-126">To specify credentials using Add Adapter Metadata Wizard</span></span>  

1. <span data-ttu-id="398ae-127">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="398ae-127">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  

2. <span data-ttu-id="398ae-128">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="398ae-128">In the **Add Generated Items** dialog box, do the following:</span></span>  


   |    <span data-ttu-id="398ae-129">使用</span><span class="sxs-lookup"><span data-stu-id="398ae-129">Use this</span></span>    |           <span data-ttu-id="398ae-130">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="398ae-130">To do this</span></span>            |
   |----------------|---------------------------------|
   | <span data-ttu-id="398ae-131">**類別**</span><span class="sxs-lookup"><span data-stu-id="398ae-131">**Categories**</span></span> |     <span data-ttu-id="398ae-132">按一下 **新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="398ae-132">Click **Add Adapter**.</span></span>      |
   | <span data-ttu-id="398ae-133">**範本**</span><span class="sxs-lookup"><span data-stu-id="398ae-133">**Templates**</span></span>  | <span data-ttu-id="398ae-134">按一下 **新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="398ae-134">Click **Add Adapter Metadata**.</span></span> |


3. <span data-ttu-id="398ae-135">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="398ae-135">Click **Add**.</span></span> <span data-ttu-id="398ae-136">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="398ae-136">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  

4. <span data-ttu-id="398ae-137">在  [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取**Wcf-oracledb**。</span><span class="sxs-lookup"><span data-stu-id="398ae-137">In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select **WCF-OracleDB**.</span></span> <span data-ttu-id="398ae-138">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="398ae-138">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="398ae-139">如果您已經設定 biztalk Wcf-oracledb 連接埠，請選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="398ae-139">If you already have a WCF-OracleDB port configured in BizTalk, select the port from the **Port** list.</span></span>  

5. <span data-ttu-id="398ae-140">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="398ae-140">Click **Next**.</span></span>  

6. <span data-ttu-id="398ae-141">在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**oracleDBBinding**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="398ae-141">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and then click **Configure**.</span></span>  

7. <span data-ttu-id="398ae-142">在**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**清單中，選取**使用者名稱**和指定使用者名稱和密碼來連接到 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="398ae-142">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** list, select **Username** and specify the user name and password to connect to the Oracle database:</span></span>  

   -   <span data-ttu-id="398ae-143">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-143">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

   -   <span data-ttu-id="398ae-144">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-144">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

8. <span data-ttu-id="398ae-145">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="398ae-145">Click **OK**.</span></span>  

## <a name="specifying-client-credentials-from-the-biztalk-server-administration-console"></a><span data-ttu-id="398ae-146">指定用戶端認證從 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="398ae-146">Specifying Client Credentials from the BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="398ae-147">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定認證，Wcf-custom 或 Wcf-oracledb 的連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="398ae-147">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the credentials as part of the WCF-Custom or WCF-OracleDB port configuration.</span></span>  

#### <a name="to-specify-client-credentials-for-the-wcf-custom-port"></a><span data-ttu-id="398ae-148">若要指定 WCF 自訂連接埠的用戶端認證</span><span class="sxs-lookup"><span data-stu-id="398ae-148">To specify client credentials for the WCF-Custom Port</span></span>  

1. <span data-ttu-id="398ae-149">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="398ae-149">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="398ae-150">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="398ae-150">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="398ae-151">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="398ae-151">In the right pane, you can choose to create a port or select an existing port.</span></span>  

3. <span data-ttu-id="398ae-152">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="398ae-152">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  

4. <span data-ttu-id="398ae-153">傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="398ae-153">For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  

   -   <span data-ttu-id="398ae-154">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="398ae-154">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an Oracle database.</span></span>  

       -   <span data-ttu-id="398ae-155">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-155">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

       -   <span data-ttu-id="398ae-156">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-156">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

   -   <span data-ttu-id="398ae-157">選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="398ae-157">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  

5. <span data-ttu-id="398ae-158">接收埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="398ae-158">For a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  

   -   <span data-ttu-id="398ae-159">選取 **使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="398ae-159">Select **User account** option, and specify the user name and password to connect to an Oracle database.</span></span>  

       -   <span data-ttu-id="398ae-160">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-160">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

       -   <span data-ttu-id="398ae-161">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-161">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

   -   <span data-ttu-id="398ae-162">選取 **取得認證，從分支機構應用程式**選項，並指定分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="398ae-162">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  

6. <span data-ttu-id="398ae-163">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="398ae-163">Click **OK**.</span></span>  

#### <a name="to-specify-credentials-for-the-wcf-oracledb-port"></a><span data-ttu-id="398ae-164">若要指定認證 Wcf-oracledb 連接埠</span><span class="sxs-lookup"><span data-stu-id="398ae-164">To specify credentials for the WCF-OracleDB port</span></span>  

1. <span data-ttu-id="398ae-165">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="398ae-165">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="398ae-166">新增 Wcf-oracledb 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="398ae-166">Add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="398ae-167">如需相關指示，請參閱 <<c0> [ 將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="398ae-167">For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  

3. <span data-ttu-id="398ae-168">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="398ae-168">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="398ae-169">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="398ae-169">In the right pane, you can choose to create a port or select an existing port.</span></span>  

4. <span data-ttu-id="398ae-170">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-oracledb**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="398ae-170">In the port properties dialog box, from the **Type** drop-down list, select **WCF-OracleDB**, and then click **Configure**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="398ae-171">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="398ae-171">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  

5. <span data-ttu-id="398ae-172">在 連接埠屬性 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="398ae-172">In the port properties dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **oracleDBBinding**.</span></span>  

6. <span data-ttu-id="398ae-173">如果您要建立傳送埠，在傳輸屬性對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="398ae-173">If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab, and do one of the following:</span></span>  

   -   <span data-ttu-id="398ae-174">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="398ae-174">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the Oracle database.</span></span>  

       -   <span data-ttu-id="398ae-175">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-175">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

       -   <span data-ttu-id="398ae-176">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-176">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

   -   <span data-ttu-id="398ae-177">選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="398ae-177">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  

7. <span data-ttu-id="398ae-178">如果您要建立接收埠，在傳輸屬性對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="398ae-178">If you are creating a receive port, in the transport properties dialog box, click the **Other** tab, and do one of the following:</span></span>  

   -   <span data-ttu-id="398ae-179">選取 **使用者帳戶**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="398ae-179">Select **User account** option, and specify the user name and password to connect to the Oracle database.</span></span>  

       -   <span data-ttu-id="398ae-180">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-180">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  

       -   <span data-ttu-id="398ae-181">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="398ae-181">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

   -   <span data-ttu-id="398ae-182">選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="398ae-182">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  

8. <span data-ttu-id="398ae-183">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="398ae-183">Click **OK**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="398ae-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="398ae-184">See Also</span></span>  
<span data-ttu-id="398ae-185">[若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) </span><span class="sxs-lookup"><span data-stu-id="398ae-185">[Building Blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) </span></span>  
 [<span data-ttu-id="398ae-186">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="398ae-186">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)