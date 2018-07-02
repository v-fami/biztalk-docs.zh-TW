---
title: 設定使用 wcf-custom 配接器和 Oracle E-business Suite 在 BizTalk 中的連接埠 |Microsoft Docs
description: 使用 Wcf-custom 配接器接收或傳送訊息從 BizTalk Server 中的 Oracle EBS
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 83d0bb00-934c-40cf-8833-354e7ce7e927
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee32e77a5c30107a481d11ed9364f6db1d666b36
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000999"
---
# <a name="configure-a-port-using-the-wcf-custom-adapter-and-oracle-e-business-suite"></a><span data-ttu-id="36786-103">設定連接埠使用 wcf-custom 配接器和 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="36786-103">Configure a port using the WCF-custom adapter and Oracle E-Business Suite</span></span>
<span data-ttu-id="36786-104">如何設定 Wcf-custom 傳送埠和接收連接埠，以執行傳出和傳入作業上使用 Oracle E-business Suite [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="36786-104">How to configure WCF-Custom send and receive ports to perform outbound and inbound operations on Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="36786-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="36786-105">Prerequisites</span></span>  
<span data-ttu-id="36786-106">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。</span><span class="sxs-lookup"><span data-stu-id="36786-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="36786-107">如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。</span><span class="sxs-lookup"><span data-stu-id="36786-107">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span>
  
## <a name="deploy-adapters-to-send-messages-to-oracle-ebs"></a><span data-ttu-id="36786-108">部署將訊息傳送至 Oracle EBS 配接器</span><span class="sxs-lookup"><span data-stu-id="36786-108">Deploy adapters to send messages to Oracle EBS</span></span>  
 <span data-ttu-id="36786-109">執行下列步驟來設定 Wcf-custom 傳送埠將訊息傳送至 Oracle E-business Suite 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="36786-109">Perform the following steps to configure a WCF-Custom send port for sending messages to Oracle E-Business Suite using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1. <span data-ttu-id="36786-110">開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="36786-110">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="36786-111">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="36786-111">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3. <span data-ttu-id="36786-112">展開您要在其下部署的應用程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="36786-112">Expand the application under which you want to deploy the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
4. <span data-ttu-id="36786-113">以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後指向您想要根據的模式之間的通訊設定的連接埠類型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="36786-113">Right-click **Send Ports**, point to **New**, and then point to the type of port you want to configure depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and Oracle E-Business Suite.</span></span>  
  
5. <span data-ttu-id="36786-114">在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="36786-114">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
6. <span data-ttu-id="36786-115">從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="36786-115">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
7. <span data-ttu-id="36786-116">在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="36786-116">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="36786-117">按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定 for Oracle E-business Suite 連線 URI。</span><span class="sxs-lookup"><span data-stu-id="36786-117">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for Oracle E-Business Suite.</span></span> <span data-ttu-id="36786-118">如需連線 URI 的詳細資訊，請參閱[建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="36786-118">For more information about the connection URI, see [Create the Oracle E-Business Suite Connection URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="36786-119">在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。</span><span class="sxs-lookup"><span data-stu-id="36786-119">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="36786-120">請參閱[訊息和 Oracle EBS 配接器的訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)) 的每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="36786-120">See [Messages and Message Schemas for Oracle EBS adapter](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)) for a list of actions for each operation.</span></span> <span data-ttu-id="36786-121">例如，叫用在介面資料表 (FA_BOOKS) 之資產的應用程式下的 Insert 作業的動作是：</span><span class="sxs-lookup"><span data-stu-id="36786-121">For example, the action to invoke the Insert operation on an interface table (FA_BOOKS) under the Asset application is:</span></span>  
  
      ```  
      InterfaceTables/Insert/OFA/FA/FA_BOOKS  
      ```  
  
   3. <span data-ttu-id="36786-122">按一下 **繫結**索引標籤上，以及從**繫結的型別**清單中，選取**oracleEBSBinding**。</span><span class="sxs-lookup"><span data-stu-id="36786-122">Click the **Binding** tab, and from the **Binding Type** list, select **oracleEBSBinding**.</span></span> <span data-ttu-id="36786-123">您可以指定不同的繫結屬性所公開[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="36786-123">You can specify the different binding properties exposed by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="36786-124">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="36786-124">For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
   4. <span data-ttu-id="36786-125">按一下 **認證**索引標籤，然後再執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="36786-125">Click the **Credentials** tab, and then do one of the following:</span></span>  
  
      -   <span data-ttu-id="36786-126">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="36786-126">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to Oracle E-Business Suite.</span></span>  
  
          |<span data-ttu-id="36786-127">使用</span><span class="sxs-lookup"><span data-stu-id="36786-127">Use this</span></span>|<span data-ttu-id="36786-128">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="36786-128">To do this</span></span>|  
          |--------------|----------------|  
          |<span data-ttu-id="36786-129">**使用 Oracle 資料庫的認證進行連接**</span><span class="sxs-lookup"><span data-stu-id="36786-129">**To connect using Oracle database credentials**</span></span>|<span data-ttu-id="36786-130">指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="36786-130">Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.</span></span>|  
          |<span data-ttu-id="36786-131">**使用 Oracle E-business Suite 認證進行連接**</span><span class="sxs-lookup"><span data-stu-id="36786-131">**To connect using Oracle E-Business Suite credentials**</span></span>|<span data-ttu-id="36786-132">指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="36786-132">Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes.</span></span> <span data-ttu-id="36786-133">在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="36786-133">In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.</span></span>|  
          |<span data-ttu-id="36786-134">**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**</span><span class="sxs-lookup"><span data-stu-id="36786-134">**To connect using Windows Authentication if ClientCredentialType is set to “Database”**</span></span>|<span data-ttu-id="36786-135">指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="36786-135">Specify a “/” for the **User name** text box and leave the **Password** text box blank.</span></span>|  
          |<span data-ttu-id="36786-136">**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**</span><span class="sxs-lookup"><span data-stu-id="36786-136">**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**</span></span>|<span data-ttu-id="36786-137">指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="36786-137">Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes.</span></span> <span data-ttu-id="36786-138">您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="36786-138">You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.</span></span>|  
  
      -   <span data-ttu-id="36786-139">選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="36786-139">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
   5. <span data-ttu-id="36786-140">若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="36786-140">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
8. <span data-ttu-id="36786-141">從**傳送處理常式**清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="36786-141">From the **Send handler** list, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="36786-142">如果您選擇**靜態單向傳送埠**在步驟 4 中，指定傳送管線。</span><span class="sxs-lookup"><span data-stu-id="36786-142">If you chose **Static One-Way Send Port** in step 4, specify a send pipeline.</span></span> <span data-ttu-id="36786-143">從**傳送管線**清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="36786-143">From the **Send pipeline** list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
10. <span data-ttu-id="36786-144">如果您選擇**靜態請求-回應連接埠**在步驟 4 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="36786-144">If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="36786-145">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="36786-145">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="36786-146">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="36786-146">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
11. <span data-ttu-id="36786-147">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="36786-147">Click **OK**.</span></span>  
  
## <a name="deploy-adapters-to-receive-messages-from-oracle-ebs"></a><span data-ttu-id="36786-148">部署配接器，以接收來自 Oracle EBS 的訊息</span><span class="sxs-lookup"><span data-stu-id="36786-148">Deploy adapters to receive messages from Oracle EBS</span></span> 
 <span data-ttu-id="36786-149">執行下列步驟來設定 Wcf-custom 接收埠，讓接收的訊息使用 Oracle E-business Suite[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="36786-149">Perform the following steps to configure a WCF-Custom receive port for receiving messages from Oracle E-Business Suite using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1. <span data-ttu-id="36786-150">開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="36786-150">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="36786-151">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="36786-151">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3. <span data-ttu-id="36786-152">展開您要在其下部署的應用程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="36786-152">Expand the application under which you want to deploy the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
4. <span data-ttu-id="36786-153">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**，取決於之間的通訊模式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="36786-153">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port**, depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and Oracle E-Business Suite.</span></span>  
  
5. <span data-ttu-id="36786-154">在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="36786-154">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6. <span data-ttu-id="36786-155">在 **接收位置**索引標籤上，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="36786-155">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="36786-156">**接收位置屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="36786-156">The **Receive Location Properties** dialog box appears.</span></span>  
  
7. <span data-ttu-id="36786-157">在 **接收位置屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="36786-157">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
   1.  <span data-ttu-id="36786-158">指定接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="36786-158">Specify a name for the receive location.</span></span>  
  
   2.  <span data-ttu-id="36786-159">從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="36786-159">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
8. <span data-ttu-id="36786-160">在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="36786-160">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="36786-161">按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定 for Oracle E-business Suite 連線 URI。</span><span class="sxs-lookup"><span data-stu-id="36786-161">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for Oracle E-Business Suite.</span></span> <span data-ttu-id="36786-162">如需連線 URI 的詳細資訊，請參閱[建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="36786-162">For more information about the connection URI, see [Create the Oracle E-Business Suite Connection URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="36786-163">按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**oracleEBSBinding**。</span><span class="sxs-lookup"><span data-stu-id="36786-163">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **oracleEBSBinding**.</span></span> <span data-ttu-id="36786-164">您可以指定不同的繫結屬性所公開[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="36786-164">You can specify the different binding properties exposed by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="36786-165">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="36786-165">For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
   3. <span data-ttu-id="36786-166">按一下 **行為**索引標籤以設定交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="36786-166">Click the **Behavior** tab to set the transaction isolation level.</span></span> <span data-ttu-id="36786-167">如需有關設定交易隔離等級的詳細資訊，請參閱 <<c0> [ 設定交易隔離等級和交易等待時間，與 E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)。</span><span class="sxs-lookup"><span data-stu-id="36786-167">For more information about setting transaction isolation level, see [Configure Transaction Isolation Level and Transaction Timeout with E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).</span></span>  
  
   4. <span data-ttu-id="36786-168">按一下 **其他人**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="36786-168">Click the **Others** tab, and do one of the following:</span></span>  
  
      -   <span data-ttu-id="36786-169">選取 **使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="36786-169">Select **User account** option, and specify the user name and password to connect to Oracle E-Business Suite.</span></span>  
  
          |<span data-ttu-id="36786-170">使用</span><span class="sxs-lookup"><span data-stu-id="36786-170">Use this</span></span>|<span data-ttu-id="36786-171">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="36786-171">To do this</span></span>|  
          |--------------|----------------|  
          |<span data-ttu-id="36786-172">**使用 Oracle 資料庫的認證進行連接**</span><span class="sxs-lookup"><span data-stu-id="36786-172">**To connect using Oracle database credentials**</span></span>|<span data-ttu-id="36786-173">指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="36786-173">Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.</span></span>|  
          |<span data-ttu-id="36786-174">**使用 Oracle E-business Suite 認證進行連接**</span><span class="sxs-lookup"><span data-stu-id="36786-174">**To connect using Oracle E-Business Suite credentials**</span></span>|<span data-ttu-id="36786-175">指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="36786-175">Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes.</span></span> <span data-ttu-id="36786-176">在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="36786-176">In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.</span></span>|  
          |<span data-ttu-id="36786-177">**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**</span><span class="sxs-lookup"><span data-stu-id="36786-177">**To connect using Windows Authentication if ClientCredentialType is set to “Database”**</span></span>|<span data-ttu-id="36786-178">指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="36786-178">Specify a “/” for the **User name** text box and leave the **Password** text box blank.</span></span>|  
          |<span data-ttu-id="36786-179">**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**</span><span class="sxs-lookup"><span data-stu-id="36786-179">**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**</span></span>|<span data-ttu-id="36786-180">指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="36786-180">Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes.</span></span> <span data-ttu-id="36786-181">您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="36786-181">You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.</span></span>|  
  
      -   <span data-ttu-id="36786-182">選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="36786-182">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
   5. <span data-ttu-id="36786-183">若要返回**接收位置屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="36786-183">To return to the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="36786-184">從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="36786-184">From the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="36786-185">如果您選擇**單向接收埠**在步驟 4 中，指定接收管線。</span><span class="sxs-lookup"><span data-stu-id="36786-185">If you chose **One-way Receive Port** in step 4, specify a receive pipeline.</span></span> <span data-ttu-id="36786-186">從**接收管線**清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="36786-186">From the **Receive pipeline** list, select the pipeline corresponding to XMLReceive.</span></span>  
  
11. <span data-ttu-id="36786-187">如果您選擇**要求回應接收埠**在步驟 4 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="36786-187">If you chose **Request Response Receive Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="36786-188">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="36786-188">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
    2.  <span data-ttu-id="36786-189">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="36786-189">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
12. <span data-ttu-id="36786-190">在 [**接收位置屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="36786-190">In the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
13. <span data-ttu-id="36786-191">在 [**接收埠屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="36786-191">In the **Receive Port Properties** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36786-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36786-192">See Also</span></span>  
 <span data-ttu-id="36786-193">[手動設定實體連接埠繫結至 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="36786-193">[Manually Configuring a Physical Port Binding to the Oracle E-Business Adapter](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md) </span></span>  
 [<span data-ttu-id="36786-194">連接到 Oracle E-business Suite 使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="36786-194">Connecting to Oracle E-Business Suite Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)