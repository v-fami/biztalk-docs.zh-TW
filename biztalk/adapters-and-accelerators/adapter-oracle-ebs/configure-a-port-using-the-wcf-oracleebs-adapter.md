---
title: 設定使用 Wcf-oracleebs 配接器在 BizTalk 中的連接埠 |Microsoft Docs
description: 使用 Wcf-oracleebs 配接器接收或傳送訊息從 BizTalk Server 中的 Oracle EBS
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b4c5c10-79a6-48d3-b4ee-dddf837f020b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dc78e6bd96f69bb92018af7a68007acfe47636d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988791"
---
# <a name="configure-a-port-using-the-wcf-oracleebs-adapter"></a><span data-ttu-id="490db-103">設定使用 Wcf-oracleebs 配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="490db-103">Configure a port using the WCF-OracleEBS adapter</span></span>
<span data-ttu-id="490db-104">How to configure Wcf-oracleebs 如何傳送和接收連接埠，以執行傳出和傳入作業上使用 Oracle E-business Suite [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="490db-104">How to configure WCF-OracleEBS send and receive ports to perform outbound and inbound operations on Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="490db-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="490db-105">Prerequisites</span></span>  
<span data-ttu-id="490db-106">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。</span><span class="sxs-lookup"><span data-stu-id="490db-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="490db-107">如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。</span><span class="sxs-lookup"><span data-stu-id="490db-107">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span>
  
## <a name="deploy-adapters-to-send-messages-to-oracle-ebs"></a><span data-ttu-id="490db-108">部署將訊息傳送至 Oracle EBS 配接器</span><span class="sxs-lookup"><span data-stu-id="490db-108">Deploy adapters to send messages to Oracle EBS</span></span> 
 <span data-ttu-id="490db-109">執行下列步驟來設定 Wcf-oracleebs 傳送埠將訊息傳送至 Oracle E-business Suite 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="490db-109">Perform the following steps to configure a WCF-OracleEBS send port for sending messages to Oracle E-Business Suite using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>    
 
1. <span data-ttu-id="490db-110">開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="490db-110">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="490db-111">新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="490db-111">Add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="490db-112">[將 Oracle E-business Suite 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)列出的步驟。</span><span class="sxs-lookup"><span data-stu-id="490db-112">[Adding the Oracle E-Business Suite Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md) lists the steps.</span></span>
  
3. <span data-ttu-id="490db-113">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="490db-113">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
4. <span data-ttu-id="490db-114">展開您要在其下部署的應用程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="490db-114">Expand the application under which you want to deploy the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
5. <span data-ttu-id="490db-115">以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後指向您想要根據的模式之間的通訊設定的連接埠類型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="490db-115">Right-click **Send Ports**, point to **New**, and then point to the type of port you want to configure depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and Oracle E-Business Suite.</span></span>  
  
6. <span data-ttu-id="490db-116">在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="490db-116">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
7. <span data-ttu-id="490db-117">從**型別**下拉式清單中，選取 Wcf-oracleebs，，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="490db-117">From the **Type** drop-down list, select WCF-OracleEBS, and then click **Configure**.</span></span>  
  
8. <span data-ttu-id="490db-118">在 [傳輸屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="490db-118">In the transport properties dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="490db-119">按一下 **一般**索引標籤上，按一下**設定**按鈕，並提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="490db-119">Click the **General** tab, click the **Configure** button and provide values for the connection parameters.</span></span> <span data-ttu-id="490db-120">如需連線 URI 的詳細資訊，請參閱[設定 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="490db-120">For more information about the connection URI, see [Configure the Connection URI for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).</span></span>  
  
   2. <span data-ttu-id="490db-121">在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。</span><span class="sxs-lookup"><span data-stu-id="490db-121">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="490db-122">請參閱[訊息和 Oracle EBS 配接器的訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)的每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="490db-122">See [Messages and Message Schemas for Oracle EBS adapter](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md) for a list of actions for each operation.</span></span> <span data-ttu-id="490db-123">例如，叫用在介面資料表 (FA_BOOKS) 之資產的應用程式下的 Insert 作業的動作是：</span><span class="sxs-lookup"><span data-stu-id="490db-123">For example, the action to invoke the Insert operation on an interface table (FA_BOOKS) under the Asset application is:</span></span>  
  
      ```  
      InterfaceTables/Insert/OFA/FA/FA_BOOKS  
      ```  
  
   3. <span data-ttu-id="490db-124">按一下 **繫結**索引標籤，然後指定所公開的繫結屬性的值[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="490db-124">Click the **Binding** tab and specify values for the binding properties exposed by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="490db-125">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="490db-125">For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="490db-126">繫結屬性會顯示根據您要設定傳送埠或接收埠。</span><span class="sxs-lookup"><span data-stu-id="490db-126">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="490db-127">比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。</span><span class="sxs-lookup"><span data-stu-id="490db-127">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  
  
   4. <span data-ttu-id="490db-128">按一下 **認證**索引標籤，然後再執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="490db-128">Click the **Credentials** tab, and then do one of the following:</span></span>  
  
      -   <span data-ttu-id="490db-129">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="490db-129">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to Oracle E-Business Suite.</span></span>  
  
          |<span data-ttu-id="490db-130">使用</span><span class="sxs-lookup"><span data-stu-id="490db-130">Use this</span></span>|<span data-ttu-id="490db-131">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="490db-131">To do this</span></span>|  
          |--------------|----------------|  
          |<span data-ttu-id="490db-132">**使用 Oracle 資料庫的認證進行連接**</span><span class="sxs-lookup"><span data-stu-id="490db-132">**To connect using Oracle database credentials**</span></span>|<span data-ttu-id="490db-133">指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="490db-133">Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.</span></span>|  
          |<span data-ttu-id="490db-134">**使用 Oracle E-business Suite 認證進行連接**</span><span class="sxs-lookup"><span data-stu-id="490db-134">**To connect using Oracle E-Business Suite credentials**</span></span>|<span data-ttu-id="490db-135">指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="490db-135">Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes.</span></span> <span data-ttu-id="490db-136">在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="490db-136">In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.</span></span>|  
          |<span data-ttu-id="490db-137">**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**</span><span class="sxs-lookup"><span data-stu-id="490db-137">**To connect using Windows Authentication if ClientCredentialType is set to “Database”**</span></span>|<span data-ttu-id="490db-138">指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="490db-138">Specify a “/” for the **User name** text box and leave the **Password** text box blank.</span></span>|  
          |<span data-ttu-id="490db-139">**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**</span><span class="sxs-lookup"><span data-stu-id="490db-139">**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**</span></span>|<span data-ttu-id="490db-140">指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="490db-140">Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes.</span></span> <span data-ttu-id="490db-141">您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="490db-141">You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.</span></span>|  
  
      -   <span data-ttu-id="490db-142">選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="490db-142">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
   5. <span data-ttu-id="490db-143">若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="490db-143">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="490db-144">從**傳送處理常式**清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="490db-144">From the **Send handler** list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="490db-145">如果您選擇**靜態單向傳送埠**在步驟 5 中，指定傳送管線。</span><span class="sxs-lookup"><span data-stu-id="490db-145">If you chose **Static One-Way Send Port** in step 5, specify a send pipeline.</span></span> <span data-ttu-id="490db-146">從**傳送管線**清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="490db-146">From the **Send pipeline** list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
11. <span data-ttu-id="490db-147">如果您選擇**靜態請求-回應連接埠**在步驟 4 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="490db-147">If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="490db-148">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="490db-148">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="490db-149">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="490db-149">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
12. <span data-ttu-id="490db-150">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="490db-150">Click **OK**.</span></span>  
  
## <a name="deploy-adapters-to-receive-messages-from-oracle-ebs"></a><span data-ttu-id="490db-151">部署配接器，以接收來自 Oracle EBS 的訊息</span><span class="sxs-lookup"><span data-stu-id="490db-151">Deploy adapters to receive messages from Oracle EBS</span></span>  
 <span data-ttu-id="490db-152">執行下列步驟來設定 Wcf-oracleebs 接收埠，讓接收的訊息使用 Oracle E-business Suite[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="490db-152">Perform the following steps to configure a WCF-OracleEBS receive port for receiving messages from Oracle E-Business Suite using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1. <span data-ttu-id="490db-153">開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="490db-153">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="490db-154">新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="490db-154">Add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="490db-155">如需相關指示，請參閱 < [Oracle E-business Suite 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="490db-155">For instructions, see [Adding the Oracle E-Business Suite Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3. <span data-ttu-id="490db-156">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="490db-156">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
4. <span data-ttu-id="490db-157">展開您要在其下部署的應用程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="490db-157">Expand the application under which you want to deploy the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
5. <span data-ttu-id="490db-158">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**，取決於之間的通訊模式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="490db-158">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port**, depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and Oracle E-Business Suite.</span></span>  
  
6. <span data-ttu-id="490db-159">在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="490db-159">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
7. <span data-ttu-id="490db-160">在 **接收位置**索引標籤上，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="490db-160">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="490db-161">**接收位置屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="490db-161">The **Receive Location Properties** dialog box appears.</span></span>  
  
8. <span data-ttu-id="490db-162">在 **接收位置屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="490db-162">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
   1.  <span data-ttu-id="490db-163">指定接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="490db-163">Specify a name for the receive location.</span></span>  
  
   2.  <span data-ttu-id="490db-164">從**型別**下拉式清單中，選取 Wcf-oracleebs，，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="490db-164">From the **Type** drop-down list, select WCF-OracleEBS, and then click **Configure**.</span></span>  
  
9. <span data-ttu-id="490db-165">在 [傳輸屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="490db-165">In the transport properties dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="490db-166">按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="490db-166">Click the **General** tab, click the **Configure** button, and provide values for the connection parameters.</span></span> <span data-ttu-id="490db-167">如需連線 URI 的詳細資訊，請參閱[設定 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="490db-167">For more information about the connection URI, see [Configure the Connection URI for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).</span></span>  
  
   2. <span data-ttu-id="490db-168">按一下 **繫結**索引標籤，然後指定的繫結所公開的屬性值[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="490db-168">Click the **Binding** tab and specify values for binding properties exposed by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="490db-169">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="490db-169">For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="490db-170">繫結屬性會顯示根據您要設定傳送埠或接收埠。</span><span class="sxs-lookup"><span data-stu-id="490db-170">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="490db-171">比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。</span><span class="sxs-lookup"><span data-stu-id="490db-171">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  
  
   3. <span data-ttu-id="490db-172">按一下 **行為**索引標籤以設定交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="490db-172">Click the **Behavior** tab to set the transaction isolation level.</span></span> <span data-ttu-id="490db-173">如需有關設定交易隔離等級的詳細資訊，請參閱 <<c0> [ 設定交易隔離等級和交易等待時間，使用 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)。</span><span class="sxs-lookup"><span data-stu-id="490db-173">For more information about setting transaction isolation level, see [Configure Transaction Isolation Level and Transaction Timeout with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).</span></span>  
  
   4. <span data-ttu-id="490db-174">按一下 **其他人**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="490db-174">Click the **Others** tab, and do one of the following:</span></span>  
  
      -   <span data-ttu-id="490db-175">選取 **使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="490db-175">Select **User account** option, and specify the user name and password to connect to Oracle E-Business Suite.</span></span>  
  
          |<span data-ttu-id="490db-176">使用</span><span class="sxs-lookup"><span data-stu-id="490db-176">Use this</span></span>|<span data-ttu-id="490db-177">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="490db-177">To do this</span></span>|  
          |--------------|----------------|  
          |<span data-ttu-id="490db-178">**使用 Oracle 資料庫的認證進行連接**</span><span class="sxs-lookup"><span data-stu-id="490db-178">**To connect using Oracle database credentials**</span></span>|<span data-ttu-id="490db-179">指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="490db-179">Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.</span></span>|  
          |<span data-ttu-id="490db-180">**使用 Oracle E-business Suite 認證進行連接**</span><span class="sxs-lookup"><span data-stu-id="490db-180">**To connect using Oracle E-Business Suite credentials**</span></span>|<span data-ttu-id="490db-181">指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="490db-181">Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes.</span></span> <span data-ttu-id="490db-182">在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="490db-182">In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.</span></span>|  
          |<span data-ttu-id="490db-183">**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**</span><span class="sxs-lookup"><span data-stu-id="490db-183">**To connect using Windows Authentication if ClientCredentialType is set to “Database”**</span></span>|<span data-ttu-id="490db-184">指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="490db-184">Specify a “/” for the **User name** text box and leave the **Password** text box blank.</span></span>|  
          |<span data-ttu-id="490db-185">**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**</span><span class="sxs-lookup"><span data-stu-id="490db-185">**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**</span></span>|<span data-ttu-id="490db-186">指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="490db-186">Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes.</span></span> <span data-ttu-id="490db-187">您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="490db-187">You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.</span></span>|  
  
      -   <span data-ttu-id="490db-188">選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="490db-188">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
   5. <span data-ttu-id="490db-189">若要返回**接收位置屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="490db-189">To return to the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
10. <span data-ttu-id="490db-190">從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="490db-190">From the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
11. <span data-ttu-id="490db-191">如果您選擇**單向接收埠**在步驟 5 中，指定接收管線。</span><span class="sxs-lookup"><span data-stu-id="490db-191">If you chose **One-way Receive Port** in step 5, specify a receive pipeline.</span></span> <span data-ttu-id="490db-192">從**接收管線**清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="490db-192">From the **Receive pipeline** list, select the pipeline corresponding to XMLReceive.</span></span>  
  
12. <span data-ttu-id="490db-193">如果您選擇**要求回應接收埠**在步驟 5 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="490db-193">If you chose **Request Response Receive Port** in step 5, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="490db-194">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="490db-194">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
    2.  <span data-ttu-id="490db-195">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="490db-195">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
13. <span data-ttu-id="490db-196">在 [**接收位置屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="490db-196">In the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
14. <span data-ttu-id="490db-197">在 [**接收埠屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="490db-197">In the **Receive Port Properties** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="490db-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="490db-198">See Also</span></span>  
 <span data-ttu-id="490db-199">[手動設定實體連接埠繫結至 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="490db-199">[Manually Configuring a Physical Port Binding to the Oracle E-Business Adapter](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md) </span></span>  
 [<span data-ttu-id="490db-200">連接到 Oracle E-business Suite 使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="490db-200">Connecting to Oracle E-Business Suite Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)