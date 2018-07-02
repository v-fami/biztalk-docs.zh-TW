---
title: 連接到 Visual Studio 中使用 新增配接器中繼資料精靈中的 Oracle 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 726b3f82-887c-407a-bb9f-dcb9443155b0
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fe5ebb085055307730f65cd36fea29f68deeccf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996535"
---
# <a name="connect-to-oracle-database-in-visual-studio-using-add-adapter-metadata-wizard"></a><span data-ttu-id="f3ecd-102">連接到 Oracle 資料庫，在 Visual Studio 中使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="f3ecd-102">Connect to Oracle Database in Visual Studio using Add Adapter Metadata Wizard</span></span>
<span data-ttu-id="f3ecd-103">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也會公開為 BizTalk 配接器，因此，您可以使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生結構描述您想要使用配接器的 Oracle 資料庫上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-103">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is also exposed as a BizTalk adapter and, therefore, you can use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate schema for the operations you want to perform on the Oracle database using the adapter.</span></span>  

 <span data-ttu-id="f3ecd-104">本主題說明如何使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-104">This topic provides instructions on how to use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  

## <a name="connecting-to-an-oracle-database-using-the-add-adapter-metadata-wizard"></a><span data-ttu-id="f3ecd-105">連接到 Oracle 資料庫使用新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="f3ecd-105">Connecting to an Oracle Database Using the Add Adapter Metadata Wizard</span></span>  
 <span data-ttu-id="f3ecd-106">執行下列步驟來連接 Oracle 資料庫使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-106">Perform the following steps to connect to an Oracle database using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  

#### <a name="to-connect-to-an-oracle-database"></a><span data-ttu-id="f3ecd-107">若要連接到 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="f3ecd-107">To connect to an Oracle database</span></span>  

1. <span data-ttu-id="f3ecd-108">若要使用連接[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]BizTalk 解決方案中：</span><span class="sxs-lookup"><span data-stu-id="f3ecd-108">To connect using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in a BizTalk solution:</span></span>  

   1. <span data-ttu-id="f3ecd-109">以滑鼠右鍵按一下方案總管 中的專案，指向**新增**，然後按一下**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-109">Right-click the project in Solution Explorer, point to **Add**, and then click **Add Generated Items**.</span></span>  

   2. <span data-ttu-id="f3ecd-110">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f3ecd-110">In the **Add Generated Items** dialog box, do the following:</span></span>  


      |    <span data-ttu-id="f3ecd-111">使用</span><span class="sxs-lookup"><span data-stu-id="f3ecd-111">Use this</span></span>    |           <span data-ttu-id="f3ecd-112">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="f3ecd-112">To do this</span></span>            |
      |----------------|---------------------------------|
      | <span data-ttu-id="f3ecd-113">**類別**</span><span class="sxs-lookup"><span data-stu-id="f3ecd-113">**Categories**</span></span> |     <span data-ttu-id="f3ecd-114">按一下 **新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-114">Click **Add Adapter**.</span></span>      |
      | <span data-ttu-id="f3ecd-115">**範本**</span><span class="sxs-lookup"><span data-stu-id="f3ecd-115">**Templates**</span></span>  | <span data-ttu-id="f3ecd-116">按一下 **新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-116">Click **Add Adapter Metadata**.</span></span> |


   3. <span data-ttu-id="f3ecd-117">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-117">Click **Add**.</span></span> <span data-ttu-id="f3ecd-118">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-118">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  

   4. <span data-ttu-id="f3ecd-119">在 [新增配接器中繼資料精靈] 中，選取**Wcf-oracledb**。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-119">In the Add Adapter Metadata Wizard, select **WCF-OracleDB**.</span></span> <span data-ttu-id="f3ecd-120">選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-120">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  

      > [!IMPORTANT]
      >  <span data-ttu-id="f3ecd-121">如果您已經設定 biztalk Wcf-oracledb 連接埠，請選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-121">If you already have a WCF-OracleDB port configured in BizTalk, select the port from the **Port** list.</span></span>  

   5. <span data-ttu-id="f3ecd-122">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-122">Click **Next**.</span></span>  

2. <span data-ttu-id="f3ecd-123">從**選取的繫結**下拉式清單中，選取**oracleDBBinding**然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-123">From the **Select a binding** drop-down list, select **oracleDBBinding** and click **Configure**.</span></span>  

3. <span data-ttu-id="f3ecd-124">中**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-124">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Oracle database.</span></span>  

   1. <span data-ttu-id="f3ecd-125">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-125">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span> <span data-ttu-id="f3ecd-126">請確定指定使用者名稱和密碼以連接到 Oracle 資料庫時，您遵守下列考量：</span><span class="sxs-lookup"><span data-stu-id="f3ecd-126">Make sure you adhere to the following considerations when specifying the user name and password to connect to an Oracle database:</span></span>  

      - <span data-ttu-id="f3ecd-127">**使用者名稱**。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-127">**User name**.</span></span> <span data-ttu-id="f3ecd-128">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留開啟的 Oracle 資料庫上的連接時，您輸入使用者名稱值的大小寫。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-128">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the user name when it opens a connection on the Oracle database.</span></span> <span data-ttu-id="f3ecd-129">Oracle 資料庫上的使用者名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-129">User names on the Oracle database are case-sensitive.</span></span> <span data-ttu-id="f3ecd-130">您應該確定您提供 Oracle 使用者名稱，以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 Oracle 資料庫所預期的情況下。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-130">You should ensure that you provide Oracle user names to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in the case expected by your Oracle database.</span></span> <span data-ttu-id="f3ecd-131">一般而言，這表示在 SCOTT/TIGER 認證中的使用者名稱應該是大寫:"SCOTT"。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-131">Typically, this means that the user name in the SCOTT/TIGER credential should be upper case: "SCOTT".</span></span>  

      - <span data-ttu-id="f3ecd-132">**密碼**。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-132">**Password**.</span></span> <span data-ttu-id="f3ecd-133">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會保留在開啟的 Oracle 資料庫上的連接時，您輸入密碼的值的大小寫。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-133">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the password when it opens a connection on the Oracle database.</span></span> <span data-ttu-id="f3ecd-134">如需版本 10g 及更早版本，則 Oracle 系統上的密碼並不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-134">For release 10g and earlier, passwords on the Oracle system are not case-sensitive.</span></span>  

   2. <span data-ttu-id="f3ecd-135">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-135">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  

4. <span data-ttu-id="f3ecd-136">按一下  **URI 屬性**索引標籤，然後指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-136">Click the **URI Properties** tab, and specify values for the connection parameters.</span></span> <span data-ttu-id="f3ecd-137">如需有關連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-137">For more information about the connection URI for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  

5. <span data-ttu-id="f3ecd-138">按一下 **繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-138">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="f3ecd-139">例如，如果您想要以 POLLINGSTMT 作業為目標，您必須設定**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-139">For example, if you want to target the POLLINGSTMT operation, you must set the **PollingStatement** binding property.</span></span> <span data-ttu-id="f3ecd-140">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-140">For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>

   > [!NOTE]
   >  <span data-ttu-id="f3ecd-141">如果您要產生使用新增的配接器中繼資料精靈 的中繼資料，而且您選取現有的 Wcf-oracledb 傳送埠時，您需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-141">If you are generating metadata using Add Adapter Metadata Wizard and you selected an existing WCF-OracleDB send port, you need not specify the binding properties.</span></span> <span data-ttu-id="f3ecd-142">從傳送埠組態，會挑選繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-142">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="f3ecd-143">不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-143">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="f3ecd-144">在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-144">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="f3ecd-145">不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-145">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  

6. <span data-ttu-id="f3ecd-146">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-146">Click **OK**.</span></span>  

7. <span data-ttu-id="f3ecd-147">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-147">Click **Connect**.</span></span> <span data-ttu-id="f3ecd-148">建立連線之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-148">After the connection is established, the connection status is shown as **Connected**.</span></span>  

    <span data-ttu-id="f3ecd-149">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]立即建立連線之後。</span><span class="sxs-lookup"><span data-stu-id="f3ecd-149">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span>  

    <span data-ttu-id="f3ecd-150">![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-oracle-database/media/b5bdb08c-4326-408b-8c2a-aedae64925c8.gif "b5bdb08c-4326-408b-8c2a-aedae64925c8")</span><span class="sxs-lookup"><span data-stu-id="f3ecd-150">![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-oracle-database/media/b5bdb08c-4326-408b-8c2a-aedae64925c8.gif "b5bdb08c-4326-408b-8c2a-aedae64925c8")</span></span>  

## <a name="see-also"></a><span data-ttu-id="f3ecd-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3ecd-151">See Also</span></span>  
 <span data-ttu-id="f3ecd-152">[連接到 Oracle 資料庫，在 Visual Studio 中使用配接器加入服務參考](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-db-in-visual-studio-using-the-add-adapter-service.md) </span><span class="sxs-lookup"><span data-stu-id="f3ecd-152">[Connect to the Oracle Database in Visual Studio using the Add Adapter Service Reference](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-db-in-visual-studio-using-the-add-adapter-service.md) </span></span>  
 [<span data-ttu-id="f3ecd-153">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="f3ecd-153">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)