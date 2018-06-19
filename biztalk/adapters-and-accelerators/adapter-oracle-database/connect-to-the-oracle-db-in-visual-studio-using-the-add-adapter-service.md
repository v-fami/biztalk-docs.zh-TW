---
title: 連接到 Oracle 資料庫，在 Visual Studio 中使用配接器加入服務參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93e56c1f-adee-4976-bc39-bb9b8102145e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12c815fbfe2b723a0dd4e4646fd7b69a7e30b01f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215062"
---
# <a name="connect-to-the-oracle-database-in-visual-studio-using-the-add-adapter-service-reference"></a><span data-ttu-id="55b63-102">連接到 Oracle 資料庫，在 Visual Studio 中使用配接器加入服務參考</span><span class="sxs-lookup"><span data-stu-id="55b63-102">Connect to the Oracle Database in Visual Studio using the Add Adapter Service Reference</span></span>
<span data-ttu-id="55b63-103">若要連接到 Oracle 資料庫使用[!INCLUDE[adapteroracle_short_md](../../includes/adapteroracle-short-md.md)]在.NET 程式設計方案，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="55b63-103">To connect to the Oracle database using the [!INCLUDE[adapteroracle_short_md](../../includes/adapteroracle-short-md.md)] in a .NET programming solution, you must use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span> <span data-ttu-id="55b63-104">本主題說明如何使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="55b63-104">This topic provides instructions on how to use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="connect-using-the-add-adapter-service-reference-plug-in"></a><span data-ttu-id="55b63-105">使用加入的配接器服務參考外掛程式連接</span><span class="sxs-lookup"><span data-stu-id="55b63-105">Connect using the Add Adapter Service Reference Plug-in</span></span>  
<span data-ttu-id="55b63-106">完成下列步驟來連接 Oracle 資料庫使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="55b63-106">Complete the following steps to connect to an Oracle database using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>   

  
1.  <span data-ttu-id="55b63-107">若要使用連接[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]程式設計方案中：</span><span class="sxs-lookup"><span data-stu-id="55b63-107">To connect using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] in a programming solution:</span></span>  
  
    1.  <span data-ttu-id="55b63-108">建立使用 Visual Studio 專案。</span><span class="sxs-lookup"><span data-stu-id="55b63-108">Create a project using Visual Studio.</span></span>  
  
    2.  <span data-ttu-id="55b63-109">以滑鼠右鍵按一下方案總管 中的專案，然後按一下**新增配接器服務參考**。</span><span class="sxs-lookup"><span data-stu-id="55b63-109">Right-click the project in Solution Explorer, and then click **Add Adapter Service Reference**.</span></span> <span data-ttu-id="55b63-110">此時會開啟 新增配接器服務參考外掛程式。</span><span class="sxs-lookup"><span data-stu-id="55b63-110">The Add Adapter Service Reference Plug-in opens.</span></span>  
  
2.  <span data-ttu-id="55b63-111">從**選取繫結**下拉式清單中選取**oracleDBBinding**按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="55b63-111">From the **Select a binding** drop-down list, select **oracleDBBinding** and click **Configure**.</span></span>  
  
3.  <span data-ttu-id="55b63-112">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="55b63-112">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Oracle database.</span></span>  
  
    1.  <span data-ttu-id="55b63-113">若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="55b63-113">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span> <span data-ttu-id="55b63-114">請確定您遵守下列項目指定的使用者名稱和密碼以連接到 Oracle 資料庫時：</span><span class="sxs-lookup"><span data-stu-id="55b63-114">Make sure you adhere to the following considerations when specifying the user name and password to connect to an Oracle database:</span></span>  
  
        -   <span data-ttu-id="55b63-115">**使用者名稱**。</span><span class="sxs-lookup"><span data-stu-id="55b63-115">**User name**.</span></span> <span data-ttu-id="55b63-116">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留在開啟的 Oracle 資料庫上的連接時，您輸入的使用者名稱值的大小寫。</span><span class="sxs-lookup"><span data-stu-id="55b63-116">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the user name when it opens a connection on the Oracle database.</span></span> <span data-ttu-id="55b63-117">Oracle 資料庫上的使用者名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="55b63-117">User names on the Oracle database are case-sensitive.</span></span> <span data-ttu-id="55b63-118">您應該確定您提供的 Oracle 使用者名稱，以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 Oracle 資料庫所預期的情況下。</span><span class="sxs-lookup"><span data-stu-id="55b63-118">You should ensure that you provide Oracle user names to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in the case expected by your Oracle database.</span></span> <span data-ttu-id="55b63-119">一般而言，這表示在 SCOTT/TIGER 認證中的使用者名稱應該是大寫才:"SCOTT"。</span><span class="sxs-lookup"><span data-stu-id="55b63-119">Typically, this means that the user name in the SCOTT/TIGER credential should be upper case: "SCOTT".</span></span>  
  
        -   <span data-ttu-id="55b63-120">**密碼**。</span><span class="sxs-lookup"><span data-stu-id="55b63-120">**Password**.</span></span> <span data-ttu-id="55b63-121">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留在開啟的 Oracle 資料庫上的連接時，您輸入的密碼值的大小寫。</span><span class="sxs-lookup"><span data-stu-id="55b63-121">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the password when it opens a connection on the Oracle database.</span></span> <span data-ttu-id="55b63-122">如需版本 10g 和更早版本，則 Oracle 系統上的密碼並不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="55b63-122">For release 10g and earlier, passwords on the Oracle system are not case-sensitive.</span></span>  
  
    2.  <span data-ttu-id="55b63-123">若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。</span><span class="sxs-lookup"><span data-stu-id="55b63-123">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
4.  <span data-ttu-id="55b63-124">按一下**URI 屬性**索引標籤，然後指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="55b63-124">Click the **URI Properties** tab, and specify values for the connection parameters.</span></span> <span data-ttu-id="55b63-125">如需有關連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="55b63-125">For more information about the connection URI for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
5.  <span data-ttu-id="55b63-126">按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="55b63-126">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="55b63-127">例如，如果您想要以 POLLINGSTMT 作業為目標，您必須設定**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="55b63-127">For example, if you want to target the POLLINGSTMT operation, you must set the **PollingStatement** binding property.</span></span> <span data-ttu-id="55b63-128">如需繫結屬性的詳細資訊，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="55b63-128">For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>
  
6.  <span data-ttu-id="55b63-129">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="55b63-129">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="55b63-130">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="55b63-130">Click **Connect**.</span></span> <span data-ttu-id="55b63-131">建立連接之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="55b63-131">After the connection is established, the connection status is shown as **Connected**.</span></span>  
  
     <span data-ttu-id="55b63-132">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。</span><span class="sxs-lookup"><span data-stu-id="55b63-132">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span>  
  
     <span data-ttu-id="55b63-133">![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-oracle-database/media/b5bdb08c-4326-408b-8c2a-aedae64925c8.gif "b5bdb08c-4326-408b-8c2a-aedae64925c8")</span><span class="sxs-lookup"><span data-stu-id="55b63-133">![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-oracle-database/media/b5bdb08c-4326-408b-8c2a-aedae64925c8.gif "b5bdb08c-4326-408b-8c2a-aedae64925c8")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b63-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55b63-134">See Also</span></span>  
 <span data-ttu-id="55b63-135">[連接到 Visual Studio 中的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="55b63-135">[Connect to Oracle Database in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md) </span></span>  
 [<span data-ttu-id="55b63-136">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="55b63-136">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)