---
title: 安裝適用於 SAP 的資料提供者的自訂 Rfc |Microsoft 文件
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
ms.openlocfilehash: 0aff501e5bf59d6ae22d9ad2a00e0e5ff5ad4605
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25966709"
---
# <a name="install-custom-rfcs-for-the-data-provider-for-sap"></a><span data-ttu-id="5f6cc-102">安裝適用於 SAP 的資料提供者的自訂 Rfc</span><span class="sxs-lookup"><span data-stu-id="5f6cc-102">Install Custom RFCs for the Data Provider for SAP</span></span>
<span data-ttu-id="5f6cc-103">如果您想要使用.NET Framework Data Provider for mySAP Business Suite 存取 SAP 系統，請安裝自訂的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-103">Install the custom RFCs if you want to use the .NET Framework Data Provider for mySAP Business Suite to access the SAP system.</span></span>

<span data-ttu-id="5f6cc-104">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要自訂 Rfc 至 SAP 系統上執行某些作業：</span><span class="sxs-lookup"><span data-stu-id="5f6cc-104">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires custom RFCs to perform some operations on the SAP system to:</span></span>
  
-   <span data-ttu-id="5f6cc-105">執行選取的作業，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要 Z_EXTRACT_DATA_OO RFC。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-105">Run the SELECT operation, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires Z_EXTRACT_DATA_OO RFC.</span></span>  
  
-   <span data-ttu-id="5f6cc-106">執行 EXECQUERY 作業，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要 Z_EXECUTE_SAP_QUERY RFC。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-106">Run the EXECQUERY operation, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires Z_EXECUTE_SAP_QUERY RFC.</span></span>  
  
<span data-ttu-id="5f6cc-107">若要執行這些 SAP 系統上的作業，您必須安裝這些自訂 Rfc，SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-107">To perform these operations on the SAP system, you must install these custom RFCs on the SAP system.</span></span> <span data-ttu-id="5f6cc-108">如果您選擇要安裝[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連同[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，安裝程式會將複製的 RFC 傳輸[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]為壓縮檔案 (customRFC.zip) 系統上安裝配接器的位置。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-108">If you chose to install the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] along with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], the Setup program copies the RFC transport for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] as a compressed file (customRFC.zip) on the system where you install the adapter.</span></span> <span data-ttu-id="5f6cc-109">Zip 檔案通常會安裝在*\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Microsoft.NET Framework Data Provider for mySAP Business Suite*。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-109">The zip file is typically installed at *\<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Microsoft .NET Framework Data Provider for mySAP Business Suite*.</span></span> 
  
 <span data-ttu-id="5f6cc-110">Zip 檔案解壓縮之後，您會發現四個資料檔案中，兩個下列命名模式 K9 *。BI1 （例如，類似於 K900534。BI1) 和其他兩種遵循模式 R9\*。BI1 （例如，類似於 R900534。BI1)。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-110">After extracting the zip file, you will find four data files, two following the naming pattern K9*.BI1 (for example, similar to K900534.BI1), and the other two following the pattern R9\*.BI1 (for example, similar to R900534.BI1).</span></span>  
  

  
1.  <span data-ttu-id="5f6cc-111">將解壓縮的檔案複製從配接器執行 SAP 應用程式伺服器的電腦。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-111">Copy the extracted files from the computer running the adapters to the SAP application server.</span></span>  
  
    1.  <span data-ttu-id="5f6cc-112">SAP 應用程式伺服器，您的開發系統的 SAP / 3 系統管理員身分登入。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-112">Log in as the SAP R/3 system administrator to the SAP application server of your development system.</span></span>  
  
    2.  <span data-ttu-id="5f6cc-113">將兩個傳輸檔案的命名模式 K9 \* 的複製。從 SAP 應用程式伺服器上執行下列目錄的配接器的電腦上安裝目錄 BI1:</span><span class="sxs-lookup"><span data-stu-id="5f6cc-113">Copy the two transport files with the naming pattern K9\*.BI1 from the installation directory on the computer running the adapters to the following directory on the SAP application server:</span></span>  
  
         `<drive>:\usr\sap\trans\cofiles`  
  
    3.  <span data-ttu-id="5f6cc-114">將兩個傳輸檔案的命名模式 R9 \* 的複製。從 SAP 應用程式伺服器上執行下列目錄的配接器的電腦上安裝目錄 BI1:</span><span class="sxs-lookup"><span data-stu-id="5f6cc-114">Copy the two transport files with the naming pattern R9\*.BI1 from the installation directory on the computer running the adapters to the following directory on the SAP application server:</span></span>  
  
         `<drive>:\usr\sap\trans\data`  
  
2.  <span data-ttu-id="5f6cc-115">載入的 SAP 應用程式伺服器上的傳輸緩衝區的傳輸。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-115">Load the transport into the transport buffer on the SAP application server.</span></span>  
  
    1.  <span data-ttu-id="5f6cc-116">在命令提示字元中，瀏覽至 SAP 應用程式伺服器上的傳輸程式目錄：</span><span class="sxs-lookup"><span data-stu-id="5f6cc-116">At the command prompt, navigate to the transport program directory on the SAP application server:</span></span>  
  
         `<drive>:\usr\sap\trans\bin`  
  
    2.  <span data-ttu-id="5f6cc-117">若要載入的傳輸緩衝區的傳輸，執行下列命令在`\usr\sap\trans\bin`目錄和取代*sysid*與您的開發系統的系統識別碼：</span><span class="sxs-lookup"><span data-stu-id="5f6cc-117">To load the transport into the transport buffer, execute the following command at the `\usr\sap\trans\bin` directory and replace *sysid* with the system ID of your development system:</span></span>  
  
        ```  
        tp addtobuffer <TransportNumber> <sysid> pf=TP_DOMAIN_<sysid>.PFL  
        ```  
  
         <span data-ttu-id="5f6cc-118">其中， *TransportNumber*是實際傳輸數目 (例如 BI1K900534)。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-118">where, *TransportNumber* is the actual transport number (for example BI1K900534).</span></span>  
  
    3.  <span data-ttu-id="5f6cc-119">之後`tp`命令完成時，您會看到類似下列報表：</span><span class="sxs-lookup"><span data-stu-id="5f6cc-119">After the `tp` command finishes, you will see a report similar to the following:</span></span>  
  
        ```  
        This is tp version 320.56.66 (release 620)  
        Addtobuffer successful for TransportNumber  
        tp finished with return code: 0  
        ```  
  
         <span data-ttu-id="5f6cc-120">傳回碼為"0"表示作業成功。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-120">Return code "0" means that the operation succeeded.</span></span>  
  
         <span data-ttu-id="5f6cc-121">是可接受的傳回碼為 0 或 4。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-121">A return code of 0 or 4 is acceptable.</span></span> <span data-ttu-id="5f6cc-122">如果您收到的 8 或更新版本的傳回碼，請連絡 Microsoft 客戶服務及支援。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-122">Contact Microsoft Customer Service and Support, if you receive a return code of 8 or above.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="5f6cc-123">傳輸檔案的第二個集合，重複步驟 (b) 和 (c)。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-123">Repeat steps (b) and (c) for the second set of transport files.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5f6cc-124">輕鬆地，您就可以從 cofile 檔案名稱衍生實際傳輸數目。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-124">You can easily derive the actual transport number from the cofile file name.</span></span> <span data-ttu-id="5f6cc-125">例如，名為 K900534 cofile。BI1 提供 BI1K900534 傳輸數。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-125">For example, a cofile named K900534.BI1 provides a transport number of BI1K900534.</span></span>  
  
3.  <span data-ttu-id="5f6cc-126">匯入 SAP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-126">Import the transport into SAP.</span></span>  
  
    1.  <span data-ttu-id="5f6cc-127">執行下列命令，在命令提示字元：</span><span class="sxs-lookup"><span data-stu-id="5f6cc-127">Execute the following command at the command prompt:</span></span>  
  
        ```  
        tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL  
        ```  
  
         <span data-ttu-id="5f6cc-128">取代*sysid*與您的開發系統的系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-128">Replace *sysid* with the system ID of your development system.</span></span> <span data-ttu-id="5f6cc-129">取代*clientnumber*與您的開發系統的用戶端數目。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-129">Replace *clientnumber* with the client number of your development system.</span></span>  
  
         <span data-ttu-id="5f6cc-130">您可以使用 U2 參數來覆寫先前安裝的物件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5f6cc-130">You can use the U2 parameter to overwrite previously installed objects, as follows:</span></span>  
  
        ```  
        tp import <TransportNumber> <sysid> client=<clientnumber> U2  
        ```  
  
         <span data-ttu-id="5f6cc-131">或</span><span class="sxs-lookup"><span data-stu-id="5f6cc-131">or</span></span>  
  
        ```  
        tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL U2  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="5f6cc-132">輕鬆地，您就可以從 cofile 檔案名稱衍生實際傳輸數目。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-132">You can easily derive the actual transport number from the cofile file name.</span></span> <span data-ttu-id="5f6cc-133">例如，名為 K900534 cofile。BI1 提供 BI1K900534 傳輸數。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-133">For example, a cofile named K900534.BI1 provides a transport number of BI1K900534.</span></span>  
  
    2.  <span data-ttu-id="5f6cc-134">之後`tp`命令完成時，您會看到類似下列報表：</span><span class="sxs-lookup"><span data-stu-id="5f6cc-134">After the `tp` command finishes, you will see a report similar to the following:</span></span>  
  
        ```  
        This is tp version 320.56.66 (release 620)  
        This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
        R3trans.exe finished (0000).  
        This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
        R3trans.exe finished (0000).  
        tp finished with return code: 0  
        ```  
  
         <span data-ttu-id="5f6cc-135">傳回碼為"0"表示作業成功。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-135">Return code "0" means that the operation succeeded.</span></span>  
  
         <span data-ttu-id="5f6cc-136">是可接受的傳回碼為 0 或 4。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-136">A return code of 0 or 4 is acceptable.</span></span> <span data-ttu-id="5f6cc-137">如果您收到的 8 或更新版本的傳回碼，請連絡 Microsoft 客戶服務及支援。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-137">Contact Microsoft Customer Service and Support if you receive a return code of 8 or above.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="5f6cc-138">傳輸檔案的第二個集合，重複步驟 （a） 和 (b)。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-138">Repeat steps (a) and (b) for the second set of transport files.</span></span>  
  
4.  <span data-ttu-id="5f6cc-139">檢查傳輸記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-139">Check the transport log.</span></span>  
  
5.  <span data-ttu-id="5f6cc-140">檢查 SAP GUI 傳輸使用交易 SE09 以確認沒有任何錯誤的組合管理 中的傳輸記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-140">Check the transport log in SAP GUI Transport Organizer using transaction SE09 to verify that there are no errors.</span></span>  
  
 <span data-ttu-id="5f6cc-141">設定使用者的授權</span><span class="sxs-lookup"><span data-stu-id="5f6cc-141">Setting User Authorization</span></span>  
 <span data-ttu-id="5f6cc-142">Z_EXTRACT_DATA_OO RFC 需要使用者具有特定授權物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-142">The Z_EXTRACT_DATA_OO RFC requires user IDs with specific authorization objects.</span></span> <span data-ttu-id="5f6cc-143">若要設定的最小限制的 RFC 執行使用 SAP GUI 授權系統管理工具：</span><span class="sxs-lookup"><span data-stu-id="5f6cc-143">Use the SAP GUI authorization administration tools to set the minimum restrictions on the execution of the RFC:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f6cc-144">您不需要設定 Z_EXECUTE_SAP_QUERY RFC 的授權。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-144">You do not need to set the authorization for the Z_EXECUTE_SAP_QUERY RFC.</span></span>  
  
-   <span data-ttu-id="5f6cc-145">Z_EXTRACT_DATA_OO 需要 S_TABU_DIS 和 Z_EIP_TABL。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-145">Z_EXTRACT_DATA_OO requires both S_TABU_DIS and Z_EIP_TABL.</span></span> <span data-ttu-id="5f6cc-146">下列的值提供 S_TABU_DIS，允許使用者檢視系統中的任何資料表的中繼資料的最小限制。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-146">The following values provide the minimum restrictions for S_TABU_DIS, which allow users to view metadata for any table in the system.</span></span>  
  
    -   <span data-ttu-id="5f6cc-147">ACTVT: 03</span><span class="sxs-lookup"><span data-stu-id="5f6cc-147">ACTVT: 03</span></span>  
  
    -   <span data-ttu-id="5f6cc-148">DICBERCLS: \*</span><span class="sxs-lookup"><span data-stu-id="5f6cc-148">DICBERCLS: \*</span></span>  
  
     <span data-ttu-id="5f6cc-149">您可以使用 DICBERCLS 授權類別所限制資料表的授權。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-149">You can use DICBERCLS to restrict authorization to tables by authorization class.</span></span>  
  
     <span data-ttu-id="5f6cc-150">若要檢視資料表的授權類別，您可以使用 TDDAT 資料表。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-150">You can use the TDDAT table to view the authorization class for tables.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5f6cc-151">若要防止交易所資料表維護資料表的變更，您應該只顯示權限授與在生產環境中 (ACTVT: 03 設定所允許的活動顯示)。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-151">To prevent changes to tables by table maintenance transactions, you should only grant display privileges in a production environment (ACTVT: 03 sets the permissible activity to display).</span></span>  
  
     <span data-ttu-id="5f6cc-152">Z_EIP_TABL 最小值為：</span><span class="sxs-lookup"><span data-stu-id="5f6cc-152">The minimum values for Z_EIP_TABL are:</span></span>  
  
    -   <span data-ttu-id="5f6cc-153">ACTVT: 03</span><span class="sxs-lookup"><span data-stu-id="5f6cc-153">ACTVT: 03</span></span>  
  
    -   <span data-ttu-id="5f6cc-154">資料表: \*</span><span class="sxs-lookup"><span data-stu-id="5f6cc-154">TABLE: \*</span></span>  
  
     <span data-ttu-id="5f6cc-155">您可以使用資料表來明確定義的授權的資料表。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-155">You can use TABLE to explicitly define the authorized tables.</span></span> <span data-ttu-id="5f6cc-156">也請注意，S_TABU_DIS 也用於其他的交易。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-156">Note, too, that S_TABU_DIS is also used in other transactions.</span></span>  
  
##### <a name="to-set-user-authorization"></a><span data-ttu-id="5f6cc-157">若要設定使用者的授權</span><span class="sxs-lookup"><span data-stu-id="5f6cc-157">To set user authorization</span></span>  
  
1.  <span data-ttu-id="5f6cc-158">啟動 SAP GUI。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-158">Start the SAP GUI.</span></span> <span data-ttu-id="5f6cc-159">移至 T-程式碼類型`pfcg`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-159">Go to T-code, type `pfcg`, and press ENTER.</span></span>  
  
2.  <span data-ttu-id="5f6cc-160">在**角色**文字方塊中，輸入您想要建立，例如，角色名稱`ZTEST`，然後按一下 **角色**。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-160">In the **Role** text box, enter a role name you want to create, for example, `ZTEST`, and then click **Role**.</span></span>  
  
3.  <span data-ttu-id="5f6cc-161">在**Create Role**頁面上，按一下**授權** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-161">In the **Create Role** page, click the **Authorizations** tab.</span></span>  
  
     <span data-ttu-id="5f6cc-162">如果提示您儲存角色，請按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-162">If prompted to save the role, click **Yes**.</span></span>  
  
4.  <span data-ttu-id="5f6cc-163">在**變更角色**頁面上，按一下**變更授權資料** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-163">In the **Change Roles** page, click the **Change Authorization Data** button.</span></span>  
  
5.  <span data-ttu-id="5f6cc-164">如果系統提示您選取的範本**選擇範本**對話方塊中，按一下 **不選取範本**。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-164">If you are prompted to select a template from the **Choose Template** dialog box, click **Do not select templates**.</span></span>  
  
6.  <span data-ttu-id="5f6cc-165">在**變更角色： 授權**頁面上，按一下**手動** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-165">In the **Change role: Authorizations** page, click the **Manually** button.</span></span>  
  
7.  <span data-ttu-id="5f6cc-166">在**手動選取的授權**方塊中，輸入授權物件名稱`Z_EIP_TABL`按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-166">In the **Manual selection of authorizations** box, enter the name of the authorization object `Z_EIP_TABL` and press ENTER.</span></span>  
  
8.  <span data-ttu-id="5f6cc-167">在**變更角色： 授權**頁面上，展開節點，直到您看到的文字方塊**活動**和**資料表名稱**。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-167">In the **Change role: Authorizations** page, expand the nodes until you see the text boxes for **Activity** and **Table Name**.</span></span> <span data-ttu-id="5f6cc-168">如**活動**文字中，輸入值`03`。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-168">For the **Activity** text box, enter the value `03`.</span></span> <span data-ttu-id="5f6cc-169">如**資料表名稱**文字中，輸入值`*`。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-169">For the **Table Name** text box, enter the value `*`.</span></span>  
  
9. <span data-ttu-id="5f6cc-170">按一下**儲存**按鈕以產生設定檔。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-170">Click the **Save** button to generate the profile.</span></span>  
  
10. <span data-ttu-id="5f6cc-171">請返回**變更角色**頁面上，按一下 [**使用者**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-171">Go back to the **Change Roles** page and click the **User** tab.</span></span>  
  
11. <span data-ttu-id="5f6cc-172">在**使用者**索引標籤上，輸入使用者名稱中的指派角色的使用者 ID**使用者識別碼**資料行，然後按一下**使用者比較** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-172">In the **User** tab, assign a user ID for the role by entering the user name in the **User ID** column, and click the **User comparison** button.</span></span>  
  
12. <span data-ttu-id="5f6cc-173">在**比較角色使用者的主要記錄**，按一下 **完成比較**更新主要資料錄。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-173">In the **Compare Role User Master Record**, click **Complete comparison** to update the master record.</span></span> <span data-ttu-id="5f6cc-174">當系統提示您儲存角色，按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-174">When prompted to save the role, click **Yes**.</span></span>  
  
13. <span data-ttu-id="5f6cc-175">儲存並結束。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-175">Save and exit.</span></span>  
  
<span data-ttu-id="5f6cc-176">確認自訂 RFC 的安裝</span><span class="sxs-lookup"><span data-stu-id="5f6cc-176">Verifying Custom RFC Installation</span></span>  
 <span data-ttu-id="5f6cc-177">安裝自訂 Rfc 之後，您可以確認 Rfc 是否已正確安裝。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-177">After you install the custom RFCs, you can verify whether the RFCs installed correctly.</span></span>  
  
-   <span data-ttu-id="5f6cc-178">如 Z_EXECUTE_SAP_QUERY RFC，您可以預先定義的查詢中使用來執行 SAP 系統[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-178">For Z_EXECUTE_SAP_QUERY RFC, you can do so by executing a pre-defined query in SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
-   <span data-ttu-id="5f6cc-179">如 Z_EXTRACT_DATA_OO RFC，您可以藉由執行下列測試，以確認 RFC 運作，且您的系統中可供使用。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-179">For Z_EXTRACT_DATA_OO RFC, you can do so by performing the following tests to confirm that the RFC operates and is ready for use in your system.</span></span>  
  
##### <a name="to-test-the-installation-of-zextractdataoo"></a><span data-ttu-id="5f6cc-180">若要測試的 Z_EXTRACT_DATA_OO 安裝</span><span class="sxs-lookup"><span data-stu-id="5f6cc-180">To test the installation of Z_EXTRACT_DATA_OO</span></span>  
  
1.  <span data-ttu-id="5f6cc-181">在 SAP GUI 授權系統管理工具 中執行 SE37，函式模組 Z_EXTRACT_DATA_OO，，然後在按下的測試模式中執行 RFC `F8`。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-181">In the SAP GUI authorization administration tools, execute SE37, function module Z_EXTRACT_DATA_OO, and then run the RFC in test mode by pressing `F8`.</span></span> <span data-ttu-id="5f6cc-182">填入參數，如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-182">Populate the parameters as follows.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="5f6cc-183">IN_METADATA_ONLY</span><span class="sxs-lookup"><span data-stu-id="5f6cc-183">IN_METADATA_ONLY</span></span>||  
    |<span data-ttu-id="5f6cc-184">IN_METADATA_LANGUAGE</span><span class="sxs-lookup"><span data-stu-id="5f6cc-184">IN_METADATA_LANGUAGE</span></span>|<span data-ttu-id="5f6cc-185">EN</span><span class="sxs-lookup"><span data-stu-id="5f6cc-185">EN</span></span>|  
    |<span data-ttu-id="5f6cc-186">IN_FROM_TABLE</span><span class="sxs-lookup"><span data-stu-id="5f6cc-186">IN_FROM_TABLE</span></span>|<span data-ttu-id="5f6cc-187">T000</span><span class="sxs-lookup"><span data-stu-id="5f6cc-187">T000</span></span>|  
    |<span data-ttu-id="5f6cc-188">IN_OUTPUT_MODE</span><span class="sxs-lookup"><span data-stu-id="5f6cc-188">IN_OUTPUT_MODE</span></span>|<span data-ttu-id="5f6cc-189">S</span><span class="sxs-lookup"><span data-stu-id="5f6cc-189">S</span></span>|  
    |<span data-ttu-id="5f6cc-190">IN_OUTPUT_FILENAME</span><span class="sxs-lookup"><span data-stu-id="5f6cc-190">IN_OUTPUT_FILENAME</span></span>||  
    |<span data-ttu-id="5f6cc-191">IN_USE_FIELD_EXITS</span><span class="sxs-lookup"><span data-stu-id="5f6cc-191">IN_USE_FIELD_EXITS</span></span>|<span data-ttu-id="5f6cc-192">X</span><span class="sxs-lookup"><span data-stu-id="5f6cc-192">X</span></span>|  
    |<span data-ttu-id="5f6cc-193">IN_SET_ROWCOUNT</span><span class="sxs-lookup"><span data-stu-id="5f6cc-193">IN_SET_ROWCOUNT</span></span>|<span data-ttu-id="5f6cc-194">0</span><span class="sxs-lookup"><span data-stu-id="5f6cc-194">0</span></span>|  
    |<span data-ttu-id="5f6cc-195">IN_DELIMITER</span><span class="sxs-lookup"><span data-stu-id="5f6cc-195">IN_DELIMITER</span></span>||  
    |<span data-ttu-id="5f6cc-196">IN_PACKET_SIZE</span><span class="sxs-lookup"><span data-stu-id="5f6cc-196">IN_PACKET_SIZE</span></span>|<span data-ttu-id="5f6cc-197">50,000</span><span class="sxs-lookup"><span data-stu-id="5f6cc-197">50,000</span></span>|  
    |<span data-ttu-id="5f6cc-198">IN_MAX_WRITE_ATTEMPTS</span><span class="sxs-lookup"><span data-stu-id="5f6cc-198">IN_MAX_WRITE_ATTEMPTS</span></span>|<span data-ttu-id="5f6cc-199">4</span><span class="sxs-lookup"><span data-stu-id="5f6cc-199">4</span></span>|  
    |<span data-ttu-id="5f6cc-200">IN_RETRY_DELAY</span><span class="sxs-lookup"><span data-stu-id="5f6cc-200">IN_RETRY_DELAY</span></span>|<span data-ttu-id="5f6cc-201">30</span><span class="sxs-lookup"><span data-stu-id="5f6cc-201">30</span></span>|  
    |<span data-ttu-id="5f6cc-202">IN_SQL_DATES_ON</span><span class="sxs-lookup"><span data-stu-id="5f6cc-202">IN_SQL_DATES_ON</span></span>||  
  
2.  <span data-ttu-id="5f6cc-203">按一下**Execute**或按`F8`。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-203">Click **Execute** or press `F8`.</span></span>  
  
3.  <span data-ttu-id="5f6cc-204">在 [結果] 窗格中，請檢查下列項目。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-204">In the results pane, check the following.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="5f6cc-205">OUT_TABLEHEADER</span><span class="sxs-lookup"><span data-stu-id="5f6cc-205">OUT_TABLEHEADER</span></span>|<span data-ttu-id="5f6cc-206">\<T000 一般的中繼資料\></span><span class="sxs-lookup"><span data-stu-id="5f6cc-206">\<T000 general metadata\></span></span>|  
    |<span data-ttu-id="5f6cc-207">OUT_TECHNICALSETTINGS</span><span class="sxs-lookup"><span data-stu-id="5f6cc-207">OUT_TECHNICALSETTINGS</span></span>|<span data-ttu-id="5f6cc-208">\<T000 技術的資料庫層級中繼資料\></span><span class="sxs-lookup"><span data-stu-id="5f6cc-208">\<T000 technical database level metadata\></span></span>|  
    |<span data-ttu-id="5f6cc-209">OUT_RECORDLENGTH</span><span class="sxs-lookup"><span data-stu-id="5f6cc-209">OUT_RECORDLENGTH</span></span>|<span data-ttu-id="5f6cc-210">\<取決於 SAP 版本\></span><span class="sxs-lookup"><span data-stu-id="5f6cc-210">\<depends on SAP version\></span></span>|  
    |<span data-ttu-id="5f6cc-211">OUT_RECORDCOUNT</span><span class="sxs-lookup"><span data-stu-id="5f6cc-211">OUT_RECORDCOUNT</span></span>|<span data-ttu-id="5f6cc-212">\<在您的系統上 T000 SE16 確認用戶端數目\></span><span class="sxs-lookup"><span data-stu-id="5f6cc-212">\<confirm the number of clients in your system with SE16 on T000\></span></span>|  
    |<span data-ttu-id="5f6cc-213">OUT_ZDATATABLE</span><span class="sxs-lookup"><span data-stu-id="5f6cc-213">OUT_ZDATATABLE</span></span>|<span data-ttu-id="5f6cc-214">\<確認此結果與使用 SE 16 T000 上的資料來源\></span><span class="sxs-lookup"><span data-stu-id="5f6cc-214">\<confirm this result with the source data using SE 16 on T000\></span></span>|  
    |<span data-ttu-id="5f6cc-215">OUT_RETURN_TAB</span><span class="sxs-lookup"><span data-stu-id="5f6cc-215">OUT_RETURN_TAB</span></span>|<span data-ttu-id="5f6cc-216">S 001 Success</span><span class="sxs-lookup"><span data-stu-id="5f6cc-216">S 001 Success</span></span>|  
  
## <a name="remove-the-rfc-for-the-data-provider-for-sap"></a><span data-ttu-id="5f6cc-217">移除資料提供者適用於 SAP RFC</span><span class="sxs-lookup"><span data-stu-id="5f6cc-217">Remove the RFC for the Data Provider for SAP</span></span>  
  
1.  <span data-ttu-id="5f6cc-218">在 SAP GUI 物件導覽 (SE80)，尋找與 ZMSBI 開發類別的所有物件。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-218">In the SAP GUI Object Navigator (SE80), find all the objects with the ZMSBI development class.</span></span>  
  
2.  <span data-ttu-id="5f6cc-219">從下列字典物件資料夾中刪除與 ZMSBI 開發類別的所有物件：</span><span class="sxs-lookup"><span data-stu-id="5f6cc-219">Delete all objects with the ZMSBI development class from the following Dictionary Objects folders:</span></span>  
  
    -   <span data-ttu-id="5f6cc-220">結構</span><span class="sxs-lookup"><span data-stu-id="5f6cc-220">Structures</span></span>  
  
    -   <span data-ttu-id="5f6cc-221">函式群組</span><span class="sxs-lookup"><span data-stu-id="5f6cc-221">Function Groups</span></span>  
  
    -   <span data-ttu-id="5f6cc-222">授權的物件</span><span class="sxs-lookup"><span data-stu-id="5f6cc-222">Authorized Object</span></span>  
  
3.  <span data-ttu-id="5f6cc-223">引發傳輸，並將它移轉透過 RFC （開發、 測試和生產系統，例如） 的安裝位置的每個系統。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-223">Raise a transport, and migrate it through each system where you installed an RFC (development, test, and production systems, for example).</span></span>  
  
     <span data-ttu-id="5f6cc-224">如需進一步協助，請連絡您 SAP 為基礎的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="5f6cc-224">For further assistance, contact your SAP Basis Administrator.</span></span>  
     
## <a name="next"></a><span data-ttu-id="5f6cc-225">下一個</span><span class="sxs-lookup"><span data-stu-id="5f6cc-225">Next</span></span>
[<span data-ttu-id="5f6cc-226">了解 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="5f6cc-226">Understand BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)  
[<span data-ttu-id="5f6cc-227">SAP 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="5f6cc-227">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)