---
title: "連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting, to the Oracle database
- connection, to the Oracle database
ms.assetid: db2789d0-2d61-472b-ad0c-4ef0707e9c64
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b9ecd6867776b8adf918f901369f526bc0479bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service"></a><span data-ttu-id="84b16-102">連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務</span><span class="sxs-lookup"><span data-stu-id="84b16-102">Connect to Oracle Database in Visual Studio using the Consume Adapter Service</span></span>
<span data-ttu-id="84b16-103">使用配接器服務增益集安裝時安裝 WCF LOB 配接器 SDK。</span><span class="sxs-lookup"><span data-stu-id="84b16-103">The Consume Adapter Service Add-in is installed when you install WCF LOB Adapter SDK.</span></span> <span data-ttu-id="84b16-104">使用配接器服務在載入增益集安裝在電腦上的所有 WCF 自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="84b16-104">The Consume Adapter Service Add-in loads all the WCF-Custom bindings installed on the computer.</span></span> <span data-ttu-id="84b16-105">若要連接到使用 WCF 型 Oracle 資料庫[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 BizTalk 專案中，您必須使用**oracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="84b16-105">To connect to the Oracle database using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in a BizTalk project, you must use the **oracleDBBinding**.</span></span>  
  
 <span data-ttu-id="84b16-106">本主題說明如何使用配接器服務增益集使用。</span><span class="sxs-lookup"><span data-stu-id="84b16-106">This topic provides instructions on how to use the Consume Adapter Service Add-in.</span></span>  
  
## <a name="connecting-to-an-oracle-database-using-the-consume-adapter-service-add-in"></a><span data-ttu-id="84b16-107">連接到 Oracle 資料庫使用配接器服務增益集</span><span class="sxs-lookup"><span data-stu-id="84b16-107">Connecting to an Oracle Database Using the Consume Adapter Service Add-in</span></span>  
 <span data-ttu-id="84b16-108">執行下列步驟來連接 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="84b16-108">Perform the following steps to connect to an Oracle database using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
1.  <span data-ttu-id="84b16-109">若要使用連接[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]BizTalk 解決方案中：</span><span class="sxs-lookup"><span data-stu-id="84b16-109">To connect using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] in a BizTalk solution:</span></span>  
  
    1.  <span data-ttu-id="84b16-110">以滑鼠右鍵按一下方案總管] 中的專案，指向**新增**，然後按一下 [**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="84b16-110">Right-click the project in Solution Explorer, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
    2.  <span data-ttu-id="84b16-111">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="84b16-111">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
        |<span data-ttu-id="84b16-112">使用</span><span class="sxs-lookup"><span data-stu-id="84b16-112">Use this</span></span>|<span data-ttu-id="84b16-113">動作</span><span class="sxs-lookup"><span data-stu-id="84b16-113">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="84b16-114">**類別**</span><span class="sxs-lookup"><span data-stu-id="84b16-114">**Categories**</span></span>|<span data-ttu-id="84b16-115">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="84b16-115">Click **Consume Adapter Service**.</span></span>|  
        |<span data-ttu-id="84b16-116">**範本**</span><span class="sxs-lookup"><span data-stu-id="84b16-116">**Templates**</span></span>|<span data-ttu-id="84b16-117">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="84b16-117">Click **Consume Adapter Service**.</span></span>|  
  
    3.  <span data-ttu-id="84b16-118">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="84b16-118">Click **Add**.</span></span> <span data-ttu-id="84b16-119">[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="84b16-119">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] opens.</span></span>  
  
2.  <span data-ttu-id="84b16-120">從**選取繫結**下拉式清單中選取**oracleDBBinding**按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="84b16-120">From the **Select a binding** drop-down list, select **oracleDBBinding** and click **Configure**.</span></span>  
  
3.  <span data-ttu-id="84b16-121">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="84b16-121">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Oracle database.</span></span>  
  
    1.  <span data-ttu-id="84b16-122">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="84b16-122">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span> <span data-ttu-id="84b16-123">請確定您遵守下列項目指定的使用者名稱和密碼以連接到 Oracle 資料庫時：</span><span class="sxs-lookup"><span data-stu-id="84b16-123">Make sure you adhere to the following considerations when specifying the user name and password to connect to an Oracle database:</span></span>  
  
        -   <span data-ttu-id="84b16-124">**使用者名稱**。</span><span class="sxs-lookup"><span data-stu-id="84b16-124">**User name**.</span></span> <span data-ttu-id="84b16-125">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留在開啟的 Oracle 資料庫上的連接時，您輸入的使用者名稱值的大小寫。</span><span class="sxs-lookup"><span data-stu-id="84b16-125">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the user name when it opens a connection on the Oracle database.</span></span> <span data-ttu-id="84b16-126">Oracle 資料庫上的使用者名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="84b16-126">User names on the Oracle database are case-sensitive.</span></span> <span data-ttu-id="84b16-127">您應該確定您提供的 Oracle 使用者名稱，以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 Oracle 資料庫所預期的情況下。</span><span class="sxs-lookup"><span data-stu-id="84b16-127">You should ensure that you provide Oracle user names to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in the case expected by your Oracle database.</span></span> <span data-ttu-id="84b16-128">一般而言，這表示在 SCOTT/TIGER 認證中的使用者名稱應該是大寫才:"SCOTT"。</span><span class="sxs-lookup"><span data-stu-id="84b16-128">Typically, this means that the user name in the SCOTT/TIGER credential should be upper case: "SCOTT".</span></span>  
  
        -   <span data-ttu-id="84b16-129">**密碼**。</span><span class="sxs-lookup"><span data-stu-id="84b16-129">**Password**.</span></span> <span data-ttu-id="84b16-130">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留在開啟的 Oracle 資料庫上的連接時，您輸入的密碼值的大小寫。</span><span class="sxs-lookup"><span data-stu-id="84b16-130">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the password when it opens a connection on the Oracle database.</span></span> <span data-ttu-id="84b16-131">如需版本 10g 和更早版本，則 Oracle 系統上的密碼並不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="84b16-131">For release 10g and earlier, passwords on the Oracle system are not case-sensitive.</span></span>  
  
    2.  <span data-ttu-id="84b16-132">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="84b16-132">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
4.  <span data-ttu-id="84b16-133">按一下**URI 屬性**索引標籤，然後指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="84b16-133">Click the **URI Properties** tab, and specify values for the connection parameters.</span></span> <span data-ttu-id="84b16-134">如需有關連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="84b16-134">For more information about the connection URI for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
5.  <span data-ttu-id="84b16-135">按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="84b16-135">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="84b16-136">例如，如果您想要以 POLLINGSTMT 作業為目標，您必須設定**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="84b16-136">For example, if you want to target the POLLINGSTMT operation, you must set the **PollingStatement** binding property.</span></span> <span data-ttu-id="84b16-137">如需繫結屬性的詳細資訊，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="84b16-137">For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
6.  <span data-ttu-id="84b16-138">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="84b16-138">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="84b16-139">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="84b16-139">Click **Connect**.</span></span> <span data-ttu-id="84b16-140">建立連接之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="84b16-140">After the connection is established, the connection status is shown as **Connected**.</span></span>  
  
     <span data-ttu-id="84b16-141">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。</span><span class="sxs-lookup"><span data-stu-id="84b16-141">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span>  
  
     <span data-ttu-id="84b16-142">![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-oracle-database/media/b5bdb08c-4326-408b-8c2a-aedae64925c8.gif "b5bdb08c-4326-408b-8c2a-aedae64925c8")</span><span class="sxs-lookup"><span data-stu-id="84b16-142">![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-oracle-database/media/b5bdb08c-4326-408b-8c2a-aedae64925c8.gif "b5bdb08c-4326-408b-8c2a-aedae64925c8")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b16-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84b16-143">See Also</span></span>  
 <span data-ttu-id="84b16-144">[連接到 Oracle 資料庫，在 Visual Studio 中使用配接器加入服務參考](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-db-in-visual-studio-using-the-add-adapter-service.md) </span><span class="sxs-lookup"><span data-stu-id="84b16-144">[Connect to the Oracle Database in Visual Studio using the Add Adapter Service Reference](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-db-in-visual-studio-using-the-add-adapter-service.md) </span></span>  
 [<span data-ttu-id="84b16-145">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="84b16-145">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)