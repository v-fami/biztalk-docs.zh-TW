---
title: 安裝適用於 SAP 的資料提供者的自訂 Rfc |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation, custom RFCs for the Data Provider for SAP
- installing, custom RFCs for the Data Provider for SAP
- installing custom RFCs, how to
ms.assetid: 7a99db70-fa5a-4c04-9dc7-b71613d4364e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f94bb4b6a6f094211654f5c3c0964bbf84d42f56
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989591"
---
# <a name="install-custom-rfcs-for-the-data-provider-for-sap"></a><span data-ttu-id="f409f-102">安裝適用於 SAP 的資料提供者的自訂 Rfc</span><span class="sxs-lookup"><span data-stu-id="f409f-102">Install Custom RFCs for the Data Provider for SAP</span></span>
<span data-ttu-id="f409f-103">如果您想要使用.NET Framework Data Provider for mySAP Business Suite 存取 SAP 系統，請安裝自訂的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="f409f-103">Install the custom RFCs if you want to use the .NET Framework Data Provider for mySAP Business Suite to access the SAP system.</span></span>

<span data-ttu-id="f409f-104">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要自訂 Rfc 來執行 SAP 系統的某些作業：</span><span class="sxs-lookup"><span data-stu-id="f409f-104">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires custom RFCs to perform some operations on the SAP system to:</span></span>
  
- <span data-ttu-id="f409f-105">執行選取的作業，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要 Z_EXTRACT_DATA_OO RFC。</span><span class="sxs-lookup"><span data-stu-id="f409f-105">Run the SELECT operation, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires Z_EXTRACT_DATA_OO RFC.</span></span>  
  
- <span data-ttu-id="f409f-106">執行 EXECQUERY 作業，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要 Z_EXECUTE_SAP_QUERY RFC。</span><span class="sxs-lookup"><span data-stu-id="f409f-106">Run the EXECQUERY operation, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires Z_EXECUTE_SAP_QUERY RFC.</span></span>  
  
<span data-ttu-id="f409f-107">若要執行這些 SAP 系統上的作業，您必須安裝這些自訂 Rfc，SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="f409f-107">To perform these operations on the SAP system, you must install these custom RFCs on the SAP system.</span></span> <span data-ttu-id="f409f-108">如果您選擇要安裝[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連同[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，安裝程式複製的 RFC 傳輸[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]的壓縮檔 (customRFC.zip) 系統上安裝配接器的位置。</span><span class="sxs-lookup"><span data-stu-id="f409f-108">If you chose to install the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] along with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], the Setup program copies the RFC transport for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] as a compressed file (customRFC.zip) on the system where you install the adapter.</span></span> <span data-ttu-id="f409f-109">Zip 檔案通常會安裝在*\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Microsoft.NET Framework Data Provider for mySAP Business Suite*。</span><span class="sxs-lookup"><span data-stu-id="f409f-109">The zip file is typically installed at *\<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Microsoft .NET Framework Data Provider for mySAP Business Suite*.</span></span> 
  
 <span data-ttu-id="f409f-110">Zip 檔案解壓縮之後，您會發現四個資料檔案，兩個遵循命名模式 K9 *。BI1 （例如，類似於 K900534。BI1) 和其他兩個模式 R9\*。BI1 （例如，類似於 R900534。BI1)。</span><span class="sxs-lookup"><span data-stu-id="f409f-110">After extracting the zip file, you will find four data files, two following the naming pattern K9*.BI1 (for example, similar to K900534.BI1), and the other two following the pattern R9\*.BI1 (for example, similar to R900534.BI1).</span></span>  
  

  
1. <span data-ttu-id="f409f-111">已解壓縮的檔案複製到 SAP 應用程式伺服器執行的配接器的電腦。</span><span class="sxs-lookup"><span data-stu-id="f409f-111">Copy the extracted files from the computer running the adapters to the SAP application server.</span></span>  
  
   1.  <span data-ttu-id="f409f-112">SAP 應用程式伺服器，您的開發系統的 SAP R/3 系統管理員身分登入。</span><span class="sxs-lookup"><span data-stu-id="f409f-112">Log in as the SAP R/3 system administrator to the SAP application server of your development system.</span></span>  
  
   2.  <span data-ttu-id="f409f-113">將兩個傳輸檔案，以命名樣式 K9 \* 複製。從 SAP 應用程式伺服器上執行到下列目錄的介面卡的電腦上安裝目錄 BI1:</span><span class="sxs-lookup"><span data-stu-id="f409f-113">Copy the two transport files with the naming pattern K9\*.BI1 from the installation directory on the computer running the adapters to the following directory on the SAP application server:</span></span>  
  
        `<drive>:\usr\sap\trans\cofiles`  
  
   3.  <span data-ttu-id="f409f-114">將兩個傳輸檔案，以命名樣式 R9 \* 複製。從 SAP 應用程式伺服器上執行到下列目錄的介面卡的電腦上安裝目錄 BI1:</span><span class="sxs-lookup"><span data-stu-id="f409f-114">Copy the two transport files with the naming pattern R9\*.BI1 from the installation directory on the computer running the adapters to the following directory on the SAP application server:</span></span>  
  
        `<drive>:\usr\sap\trans\data`  
  
2. <span data-ttu-id="f409f-115">載入的 SAP 應用程式伺服器上的傳輸緩衝區的傳輸。</span><span class="sxs-lookup"><span data-stu-id="f409f-115">Load the transport into the transport buffer on the SAP application server.</span></span>  
  
   1.  <span data-ttu-id="f409f-116">在命令提示字元中，瀏覽至 SAP 應用程式伺服器上的傳輸程式目錄：</span><span class="sxs-lookup"><span data-stu-id="f409f-116">At the command prompt, navigate to the transport program directory on the SAP application server:</span></span>  
  
        `<drive>:\usr\sap\trans\bin`  
  
   2.  <span data-ttu-id="f409f-117">若要載入的傳輸緩衝區的傳輸，執行下列命令，`\usr\sap\trans\bin`目錄和取代*sysid*與您的開發系統的系統識別碼：</span><span class="sxs-lookup"><span data-stu-id="f409f-117">To load the transport into the transport buffer, execute the following command at the `\usr\sap\trans\bin` directory and replace *sysid* with the system ID of your development system:</span></span>  
  
       ```  
       tp addtobuffer <TransportNumber> <sysid> pf=TP_DOMAIN_<sysid>.PFL  
       ```  
  
        <span data-ttu-id="f409f-118">其中， *TransportNumber*是實際傳輸數字 (例如 BI1K900534)。</span><span class="sxs-lookup"><span data-stu-id="f409f-118">where, *TransportNumber* is the actual transport number (for example BI1K900534).</span></span>  
  
   3.  <span data-ttu-id="f409f-119">之後`tp`命令完成時，您會看到類似下列報表：</span><span class="sxs-lookup"><span data-stu-id="f409f-119">After the `tp` command finishes, you will see a report similar to the following:</span></span>  
  
       ```  
       This is tp version 320.56.66 (release 620)  
       Addtobuffer successful for TransportNumber  
       tp finished with return code: 0  
       ```  
  
        <span data-ttu-id="f409f-120">傳回碼為"0"表示作業成功。</span><span class="sxs-lookup"><span data-stu-id="f409f-120">Return code "0" means that the operation succeeded.</span></span>  
  
        <span data-ttu-id="f409f-121">傳回碼為 0 或 4 是可接受的。</span><span class="sxs-lookup"><span data-stu-id="f409f-121">A return code of 0 or 4 is acceptable.</span></span> <span data-ttu-id="f409f-122">如果您收到的 8 個以上的傳回碼，請連絡 Microsoft 客戶服務及支援。</span><span class="sxs-lookup"><span data-stu-id="f409f-122">Contact Microsoft Customer Service and Support, if you receive a return code of 8 or above.</span></span>  
  
       > [!IMPORTANT]
       >  <span data-ttu-id="f409f-123">傳輸檔案的第二個集合，請重複步驟 (b) 和 (c)。</span><span class="sxs-lookup"><span data-stu-id="f409f-123">Repeat steps (b) and (c) for the second set of transport files.</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="f409f-124">輕鬆地，您就可以從 cofile 檔案名稱衍生實際傳輸數目。</span><span class="sxs-lookup"><span data-stu-id="f409f-124">You can easily derive the actual transport number from the cofile file name.</span></span> <span data-ttu-id="f409f-125">例如，名為 K900534 cofile。BI1 提供 BI1K900534 傳輸數目。</span><span class="sxs-lookup"><span data-stu-id="f409f-125">For example, a cofile named K900534.BI1 provides a transport number of BI1K900534.</span></span>  
  
3. <span data-ttu-id="f409f-126">匯入 SAP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="f409f-126">Import the transport into SAP.</span></span>  
  
   1.  <span data-ttu-id="f409f-127">執行下列命令在命令提示字元：</span><span class="sxs-lookup"><span data-stu-id="f409f-127">Execute the following command at the command prompt:</span></span>  
  
       ```  
       tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL  
       ```  
  
        <span data-ttu-id="f409f-128">取代*sysid*與您的開發系統的系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="f409f-128">Replace *sysid* with the system ID of your development system.</span></span> <span data-ttu-id="f409f-129">取代*clientnumber*與您的開發系統的用戶端編號。</span><span class="sxs-lookup"><span data-stu-id="f409f-129">Replace *clientnumber* with the client number of your development system.</span></span>  
  
        <span data-ttu-id="f409f-130">您可以使用 U2 參數來覆寫先前安裝的物件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f409f-130">You can use the U2 parameter to overwrite previously installed objects, as follows:</span></span>  
  
       ```  
       tp import <TransportNumber> <sysid> client=<clientnumber> U2  
       ```  
  
        <span data-ttu-id="f409f-131">中的多個</span><span class="sxs-lookup"><span data-stu-id="f409f-131">or</span></span>  
  
       ```  
       tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL U2  
       ```  
  
       > [!NOTE]
       >  <span data-ttu-id="f409f-132">輕鬆地，您就可以從 cofile 檔案名稱衍生實際傳輸數目。</span><span class="sxs-lookup"><span data-stu-id="f409f-132">You can easily derive the actual transport number from the cofile file name.</span></span> <span data-ttu-id="f409f-133">例如，名為 K900534 cofile。BI1 提供 BI1K900534 傳輸數目。</span><span class="sxs-lookup"><span data-stu-id="f409f-133">For example, a cofile named K900534.BI1 provides a transport number of BI1K900534.</span></span>  
  
   2.  <span data-ttu-id="f409f-134">之後`tp`命令完成時，您會看到類似下列報表：</span><span class="sxs-lookup"><span data-stu-id="f409f-134">After the `tp` command finishes, you will see a report similar to the following:</span></span>  
  
       ```  
       This is tp version 320.56.66 (release 620)  
       This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
       R3trans.exe finished (0000).  
       This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
       R3trans.exe finished (0000).  
       tp finished with return code: 0  
       ```  
  
        <span data-ttu-id="f409f-135">傳回碼為"0"表示作業成功。</span><span class="sxs-lookup"><span data-stu-id="f409f-135">Return code "0" means that the operation succeeded.</span></span>  
  
        <span data-ttu-id="f409f-136">傳回碼為 0 或 4 是可接受的。</span><span class="sxs-lookup"><span data-stu-id="f409f-136">A return code of 0 or 4 is acceptable.</span></span> <span data-ttu-id="f409f-137">如果您收到的 8 個以上的傳回碼，請連絡 Microsoft 客戶服務及支援。</span><span class="sxs-lookup"><span data-stu-id="f409f-137">Contact Microsoft Customer Service and Support if you receive a return code of 8 or above.</span></span>  
  
       > [!IMPORTANT]
       >  <span data-ttu-id="f409f-138">第二組傳輸檔案，請重複步驟 （a） 和 (b)。</span><span class="sxs-lookup"><span data-stu-id="f409f-138">Repeat steps (a) and (b) for the second set of transport files.</span></span>  
  
4. <span data-ttu-id="f409f-139">檢查傳輸記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f409f-139">Check the transport log.</span></span>  
  
5. <span data-ttu-id="f409f-140">檢查 SAP GUI 傳輸使用交易 SE09 以確認沒有任何錯誤的組合管理 中的傳輸記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f409f-140">Check the transport log in SAP GUI Transport Organizer using transaction SE09 to verify that there are no errors.</span></span>  
  
   <span data-ttu-id="f409f-141">設定使用者的授權</span><span class="sxs-lookup"><span data-stu-id="f409f-141">Setting User Authorization</span></span>  
   <span data-ttu-id="f409f-142">Z_EXTRACT_DATA_OO RFC 需要具有特定授權物件的使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="f409f-142">The Z_EXTRACT_DATA_OO RFC requires user IDs with specific authorization objects.</span></span> <span data-ttu-id="f409f-143">使用 SAP GUI 授權系統管理工具的 RFC 執行上設定的最小的限制：</span><span class="sxs-lookup"><span data-stu-id="f409f-143">Use the SAP GUI authorization administration tools to set the minimum restrictions on the execution of the RFC:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f409f-144">您不需要設定 Z_EXECUTE_SAP_QUERY RFC 的授權。</span><span class="sxs-lookup"><span data-stu-id="f409f-144">You do not need to set the authorization for the Z_EXECUTE_SAP_QUERY RFC.</span></span>  
  
- <span data-ttu-id="f409f-145">Z_EXTRACT_DATA_OO 需要 S_TABU_DIS 和 Z_EIP_TABL。</span><span class="sxs-lookup"><span data-stu-id="f409f-145">Z_EXTRACT_DATA_OO requires both S_TABU_DIS and Z_EIP_TABL.</span></span> <span data-ttu-id="f409f-146">下列的值提供 S_TABU_DIS，允許使用者檢視系統中的任何資料表的中繼資料的最小限制。</span><span class="sxs-lookup"><span data-stu-id="f409f-146">The following values provide the minimum restrictions for S_TABU_DIS, which allow users to view metadata for any table in the system.</span></span>  
  
  - <span data-ttu-id="f409f-147">ACTVT: 03</span><span class="sxs-lookup"><span data-stu-id="f409f-147">ACTVT: 03</span></span>  
  
  - <span data-ttu-id="f409f-148">DICBERCLS: \*</span><span class="sxs-lookup"><span data-stu-id="f409f-148">DICBERCLS: \*</span></span>  
  
    <span data-ttu-id="f409f-149">您可以使用 DICBERCLS 授權類別所限制資料表的授權。</span><span class="sxs-lookup"><span data-stu-id="f409f-149">You can use DICBERCLS to restrict authorization to tables by authorization class.</span></span>  
  
    <span data-ttu-id="f409f-150">若要檢視資料表的授權類別，您可以使用 TDDAT 資料表。</span><span class="sxs-lookup"><span data-stu-id="f409f-150">You can use the TDDAT table to view the authorization class for tables.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="f409f-151">若要防止資料表維護交易資料表的變更，您應該只授與在生產環境中的顯示權限 (ACTVT: 03 設定允許的活動，以顯示)。</span><span class="sxs-lookup"><span data-stu-id="f409f-151">To prevent changes to tables by table maintenance transactions, you should only grant display privileges in a production environment (ACTVT: 03 sets the permissible activity to display).</span></span>  
  
   <span data-ttu-id="f409f-152">Z_EIP_TABL 最小值為：</span><span class="sxs-lookup"><span data-stu-id="f409f-152">The minimum values for Z_EIP_TABL are:</span></span>  
  
  - <span data-ttu-id="f409f-153">ACTVT: 03</span><span class="sxs-lookup"><span data-stu-id="f409f-153">ACTVT: 03</span></span>  
  
  - <span data-ttu-id="f409f-154">資料表: \*</span><span class="sxs-lookup"><span data-stu-id="f409f-154">TABLE: \*</span></span>  
  
    <span data-ttu-id="f409f-155">您可以使用資料表來明確定義授權的資料表。</span><span class="sxs-lookup"><span data-stu-id="f409f-155">You can use TABLE to explicitly define the authorized tables.</span></span> <span data-ttu-id="f409f-156">也請注意，S_TABU_DIS 也用於其他交易。</span><span class="sxs-lookup"><span data-stu-id="f409f-156">Note, too, that S_TABU_DIS is also used in other transactions.</span></span>  
  
##### <a name="to-set-user-authorization"></a><span data-ttu-id="f409f-157">若要設定使用者的授權</span><span class="sxs-lookup"><span data-stu-id="f409f-157">To set user authorization</span></span>  
  
1.  <span data-ttu-id="f409f-158">啟動 SAP GUI。</span><span class="sxs-lookup"><span data-stu-id="f409f-158">Start the SAP GUI.</span></span> <span data-ttu-id="f409f-159">移至 T-程式碼類型`pfcg`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="f409f-159">Go to T-code, type `pfcg`, and press ENTER.</span></span>  
  
2.  <span data-ttu-id="f409f-160">在 **角色**文字中，輸入您想要建立此項目，例如，角色名稱`ZTEST`，然後按一下 **角色**。</span><span class="sxs-lookup"><span data-stu-id="f409f-160">In the **Role** text box, enter a role name you want to create, for example, `ZTEST`, and then click **Role**.</span></span>  
  
3.  <span data-ttu-id="f409f-161">在 [ **Create Role**頁面上，按一下**授權**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f409f-161">In the **Create Role** page, click the **Authorizations** tab.</span></span>  
  
     <span data-ttu-id="f409f-162">如果出現提示，儲存角色，請按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="f409f-162">If prompted to save the role, click **Yes**.</span></span>  
  
4.  <span data-ttu-id="f409f-163">在 [**變更角色**頁面上，按一下**變更授權資料**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f409f-163">In the **Change Roles** page, click the **Change Authorization Data** button.</span></span>  
  
5.  <span data-ttu-id="f409f-164">如果系統提示您選取的範本**選擇範本** 對話方塊中，按一下**請勿選取範本**。</span><span class="sxs-lookup"><span data-stu-id="f409f-164">If you are prompted to select a template from the **Choose Template** dialog box, click **Do not select templates**.</span></span>  
  
6.  <span data-ttu-id="f409f-165">在 [**變更角色： 授權**頁面上，按一下**手動**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f409f-165">In the **Change role: Authorizations** page, click the **Manually** button.</span></span>  
  
7.  <span data-ttu-id="f409f-166">在 **手動選取的授權**方塊中，輸入授權物件的名稱`Z_EIP_TABL`按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f409f-166">In the **Manual selection of authorizations** box, enter the name of the authorization object `Z_EIP_TABL` and press ENTER.</span></span>  
  
8.  <span data-ttu-id="f409f-167">在 **變更角色： 授權**頁面上，展開節點，直到您看到的文字方塊**活動**並**資料表名稱**。</span><span class="sxs-lookup"><span data-stu-id="f409f-167">In the **Change role: Authorizations** page, expand the nodes until you see the text boxes for **Activity** and **Table Name**.</span></span> <span data-ttu-id="f409f-168">針對**活動**文字方塊中，輸入值`03`。</span><span class="sxs-lookup"><span data-stu-id="f409f-168">For the **Activity** text box, enter the value `03`.</span></span> <span data-ttu-id="f409f-169">針對**資料表名稱**文字方塊中，輸入值`*`。</span><span class="sxs-lookup"><span data-stu-id="f409f-169">For the **Table Name** text box, enter the value `*`.</span></span>  
  
9. <span data-ttu-id="f409f-170">按一下 **儲存**按鈕，以產生設定檔。</span><span class="sxs-lookup"><span data-stu-id="f409f-170">Click the **Save** button to generate the profile.</span></span>  
  
10. <span data-ttu-id="f409f-171">請返回**變更角色**頁面，然後按一下**使用者** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f409f-171">Go back to the **Change Roles** page and click the **User** tab.</span></span>  
  
11. <span data-ttu-id="f409f-172">在 **使用者**索引標籤上，輸入使用者名稱中的指派角色的使用者識別碼**使用者識別碼**資料行，然後按一下 **使用者比較** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f409f-172">In the **User** tab, assign a user ID for the role by entering the user name in the **User ID** column, and click the **User comparison** button.</span></span>  
  
12. <span data-ttu-id="f409f-173">在 **比較角色使用者的主要記錄**，按一下**完成比較**更新主要資料錄。</span><span class="sxs-lookup"><span data-stu-id="f409f-173">In the **Compare Role User Master Record**, click **Complete comparison** to update the master record.</span></span> <span data-ttu-id="f409f-174">出現提示時，儲存角色，按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="f409f-174">When prompted to save the role, click **Yes**.</span></span>  
  
13. <span data-ttu-id="f409f-175">儲存並結束。</span><span class="sxs-lookup"><span data-stu-id="f409f-175">Save and exit.</span></span>  
  
<span data-ttu-id="f409f-176">確認自訂 RFC 的安裝</span><span class="sxs-lookup"><span data-stu-id="f409f-176">Verifying Custom RFC Installation</span></span>  
 <span data-ttu-id="f409f-177">安裝自訂的 Rfc 之後，您可以確認 Rfc 是否已正確安裝。</span><span class="sxs-lookup"><span data-stu-id="f409f-177">After you install the custom RFCs, you can verify whether the RFCs installed correctly.</span></span>  
  
- <span data-ttu-id="f409f-178">Z_EXECUTE_SAP_QUERY RFC，您可以執行這項作業執行的預先定義的查詢中 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f409f-178">For Z_EXECUTE_SAP_QUERY RFC, you can do so by executing a pre-defined query in SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
- <span data-ttu-id="f409f-179">Z_EXTRACT_DATA_OO RFC，您可以執行這項作業執行下列測試，確認 RFC 運作，並在您的系統可供使用。</span><span class="sxs-lookup"><span data-stu-id="f409f-179">For Z_EXTRACT_DATA_OO RFC, you can do so by performing the following tests to confirm that the RFC operates and is ready for use in your system.</span></span>  
  
##### <a name="to-test-the-installation-of-zextractdataoo"></a><span data-ttu-id="f409f-180">若要測試的 Z_EXTRACT_DATA_OO 安裝</span><span class="sxs-lookup"><span data-stu-id="f409f-180">To test the installation of Z_EXTRACT_DATA_OO</span></span>  
  
1.  <span data-ttu-id="f409f-181">在 SAP GUI 授權系統管理工具中，執行 SE37，函式模組 Z_EXTRACT_DATA_OO，，然後在按下的測試模式中執行 RFC `F8`。</span><span class="sxs-lookup"><span data-stu-id="f409f-181">In the SAP GUI authorization administration tools, execute SE37, function module Z_EXTRACT_DATA_OO, and then run the RFC in test mode by pressing `F8`.</span></span> <span data-ttu-id="f409f-182">會填入參數，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f409f-182">Populate the parameters as follows.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="f409f-183">IN_METADATA_ONLY</span><span class="sxs-lookup"><span data-stu-id="f409f-183">IN_METADATA_ONLY</span></span>||  
    |<span data-ttu-id="f409f-184">IN_METADATA_LANGUAGE</span><span class="sxs-lookup"><span data-stu-id="f409f-184">IN_METADATA_LANGUAGE</span></span>|<span data-ttu-id="f409f-185">EN</span><span class="sxs-lookup"><span data-stu-id="f409f-185">EN</span></span>|  
    |<span data-ttu-id="f409f-186">IN_FROM_TABLE</span><span class="sxs-lookup"><span data-stu-id="f409f-186">IN_FROM_TABLE</span></span>|<span data-ttu-id="f409f-187">T000</span><span class="sxs-lookup"><span data-stu-id="f409f-187">T000</span></span>|  
    |<span data-ttu-id="f409f-188">IN_OUTPUT_MODE</span><span class="sxs-lookup"><span data-stu-id="f409f-188">IN_OUTPUT_MODE</span></span>|<span data-ttu-id="f409f-189">S</span><span class="sxs-lookup"><span data-stu-id="f409f-189">S</span></span>|  
    |<span data-ttu-id="f409f-190">IN_OUTPUT_FILENAME</span><span class="sxs-lookup"><span data-stu-id="f409f-190">IN_OUTPUT_FILENAME</span></span>||  
    |<span data-ttu-id="f409f-191">IN_USE_FIELD_EXITS</span><span class="sxs-lookup"><span data-stu-id="f409f-191">IN_USE_FIELD_EXITS</span></span>|<span data-ttu-id="f409f-192">X</span><span class="sxs-lookup"><span data-stu-id="f409f-192">X</span></span>|  
    |<span data-ttu-id="f409f-193">IN_SET_ROWCOUNT</span><span class="sxs-lookup"><span data-stu-id="f409f-193">IN_SET_ROWCOUNT</span></span>|<span data-ttu-id="f409f-194">0</span><span class="sxs-lookup"><span data-stu-id="f409f-194">0</span></span>|  
    |<span data-ttu-id="f409f-195">IN_DELIMITER</span><span class="sxs-lookup"><span data-stu-id="f409f-195">IN_DELIMITER</span></span>||  
    |<span data-ttu-id="f409f-196">IN_PACKET_SIZE</span><span class="sxs-lookup"><span data-stu-id="f409f-196">IN_PACKET_SIZE</span></span>|<span data-ttu-id="f409f-197">50,000</span><span class="sxs-lookup"><span data-stu-id="f409f-197">50,000</span></span>|  
    |<span data-ttu-id="f409f-198">IN_MAX_WRITE_ATTEMPTS</span><span class="sxs-lookup"><span data-stu-id="f409f-198">IN_MAX_WRITE_ATTEMPTS</span></span>|<span data-ttu-id="f409f-199">4</span><span class="sxs-lookup"><span data-stu-id="f409f-199">4</span></span>|  
    |<span data-ttu-id="f409f-200">IN_RETRY_DELAY</span><span class="sxs-lookup"><span data-stu-id="f409f-200">IN_RETRY_DELAY</span></span>|<span data-ttu-id="f409f-201">30</span><span class="sxs-lookup"><span data-stu-id="f409f-201">30</span></span>|  
    |<span data-ttu-id="f409f-202">IN_SQL_DATES_ON</span><span class="sxs-lookup"><span data-stu-id="f409f-202">IN_SQL_DATES_ON</span></span>||  
  
2.  <span data-ttu-id="f409f-203">按一下  **Execute**或按`F8`。</span><span class="sxs-lookup"><span data-stu-id="f409f-203">Click **Execute** or press `F8`.</span></span>  
  
3.  <span data-ttu-id="f409f-204">在 [結果] 窗格中，請檢查下列項目。</span><span class="sxs-lookup"><span data-stu-id="f409f-204">In the results pane, check the following.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="f409f-205">OUT_TABLEHEADER</span><span class="sxs-lookup"><span data-stu-id="f409f-205">OUT_TABLEHEADER</span></span>|<span data-ttu-id="f409f-206">\<T000 一般的中繼資料\></span><span class="sxs-lookup"><span data-stu-id="f409f-206">\<T000 general metadata\></span></span>|  
    |<span data-ttu-id="f409f-207">OUT_TECHNICALSETTINGS</span><span class="sxs-lookup"><span data-stu-id="f409f-207">OUT_TECHNICALSETTINGS</span></span>|<span data-ttu-id="f409f-208">\<T000 技術的資料庫層級的中繼資料\></span><span class="sxs-lookup"><span data-stu-id="f409f-208">\<T000 technical database level metadata\></span></span>|  
    |<span data-ttu-id="f409f-209">OUT_RECORDLENGTH</span><span class="sxs-lookup"><span data-stu-id="f409f-209">OUT_RECORDLENGTH</span></span>|<span data-ttu-id="f409f-210">\<取決於 SAP 版本\></span><span class="sxs-lookup"><span data-stu-id="f409f-210">\<depends on SAP version\></span></span>|  
    |<span data-ttu-id="f409f-211">OUT_RECORDCOUNT</span><span class="sxs-lookup"><span data-stu-id="f409f-211">OUT_RECORDCOUNT</span></span>|<span data-ttu-id="f409f-212">\<在您的系統上 T000 SE16 確認用戶端數目\></span><span class="sxs-lookup"><span data-stu-id="f409f-212">\<confirm the number of clients in your system with SE16 on T000\></span></span>|  
    |<span data-ttu-id="f409f-213">OUT_ZDATATABLE</span><span class="sxs-lookup"><span data-stu-id="f409f-213">OUT_ZDATATABLE</span></span>|<span data-ttu-id="f409f-214">\<確認這個結果與使用 SE 16 T000 上的資料來源\></span><span class="sxs-lookup"><span data-stu-id="f409f-214">\<confirm this result with the source data using SE 16 on T000\></span></span>|  
    |<span data-ttu-id="f409f-215">OUT_RETURN_TAB</span><span class="sxs-lookup"><span data-stu-id="f409f-215">OUT_RETURN_TAB</span></span>|<span data-ttu-id="f409f-216">S 001 成功</span><span class="sxs-lookup"><span data-stu-id="f409f-216">S 001 Success</span></span>|  
  
## <a name="remove-the-rfc-for-the-data-provider-for-sap"></a><span data-ttu-id="f409f-217">移除適用於 SAP 的資料提供者的 RFC</span><span class="sxs-lookup"><span data-stu-id="f409f-217">Remove the RFC for the Data Provider for SAP</span></span>  
  
1.  <span data-ttu-id="f409f-218">在 SAP GUI 物件導覽 (SE80)，尋找與 ZMSBI 開發類別的所有物件。</span><span class="sxs-lookup"><span data-stu-id="f409f-218">In the SAP GUI Object Navigator (SE80), find all the objects with the ZMSBI development class.</span></span>  
  
2.  <span data-ttu-id="f409f-219">從下列的字典物件資料夾中刪除與 ZMSBI 開發類別的所有物件：</span><span class="sxs-lookup"><span data-stu-id="f409f-219">Delete all objects with the ZMSBI development class from the following Dictionary Objects folders:</span></span>  
  
    -   <span data-ttu-id="f409f-220">結構</span><span class="sxs-lookup"><span data-stu-id="f409f-220">Structures</span></span>  
  
    -   <span data-ttu-id="f409f-221">函式群組</span><span class="sxs-lookup"><span data-stu-id="f409f-221">Function Groups</span></span>  
  
    -   <span data-ttu-id="f409f-222">已獲授權的物件</span><span class="sxs-lookup"><span data-stu-id="f409f-222">Authorized Object</span></span>  
  
3.  <span data-ttu-id="f409f-223">引發的傳輸，並將它移轉透過每個系統的 RFC （開發、 測試和生產系統，例如） 的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="f409f-223">Raise a transport, and migrate it through each system where you installed an RFC (development, test, and production systems, for example).</span></span>  
  
     <span data-ttu-id="f409f-224">如需進一步協助，請連絡您的 SAP 基礎系統管理員。</span><span class="sxs-lookup"><span data-stu-id="f409f-224">For further assistance, contact your SAP Basis Administrator.</span></span>  
     
## <a name="next"></a><span data-ttu-id="f409f-225">下一個</span><span class="sxs-lookup"><span data-stu-id="f409f-225">Next</span></span>
[<span data-ttu-id="f409f-226">了解 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="f409f-226">Understand BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)  
[<span data-ttu-id="f409f-227">SAP 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="f409f-227">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)