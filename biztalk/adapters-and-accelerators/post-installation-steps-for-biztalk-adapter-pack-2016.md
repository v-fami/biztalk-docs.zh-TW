---
title: BizTalk 配接器組件 2016 後安裝步驟 |Microsoft 文件
description: 步驟完成之後安裝 BAP 2016，包括新增配接器至 BizTalk 管理、 Oracle、 更新和註冊配接器繫結。
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8946bfe-92bb-470d-bec4-9bc3a07ce0d2
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17bd0a76cacb35563448f31f79c2275c79b92ab8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967396"
---
# <a name="post-installation-steps-for-biztalk-adapter-pack-2016"></a><span data-ttu-id="8d441-103">BizTalk 配接器組件 2016 後安裝步驟</span><span class="sxs-lookup"><span data-stu-id="8d441-103">Post installation steps for BizTalk Adapter Pack 2016</span></span>
<span data-ttu-id="8d441-104">安裝之後[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，一些安裝後步驟。</span><span class="sxs-lookup"><span data-stu-id="8d441-104">After you install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], there are some post-installation steps.</span></span> <span data-ttu-id="8d441-105">本主題列出這些步驟。</span><span class="sxs-lookup"><span data-stu-id="8d441-105">This topic lists these steps.</span></span>   

## <a name="add-the-adapter-to-biztalk-administration"></a><span data-ttu-id="8d441-106">新增配接器至 BizTalk 管理</span><span class="sxs-lookup"><span data-stu-id="8d441-106">Add the adapter to BizTalk Administration</span></span>
  
1.  <span data-ttu-id="8d441-107">開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8d441-107">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="8d441-108">展開**BizTalk 群組**，依序展開**平台設定**，然後選取**配接器**。</span><span class="sxs-lookup"><span data-stu-id="8d441-108">Expand the **BizTalk Group**, expand **Platform Settings**, and then select **Adapters**.</span></span>  
  
3.  <span data-ttu-id="8d441-109">以滑鼠右鍵按一下**配接器**，選取**新增**，然後選取**配接器**。</span><span class="sxs-lookup"><span data-stu-id="8d441-109">Right-click **Adapters**, select **New**, and select **Adapter**.</span></span>  
  
     <span data-ttu-id="8d441-110">![新增配接器](../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span><span class="sxs-lookup"><span data-stu-id="8d441-110">![Add an adapter](../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span></span>  
  
4.  <span data-ttu-id="8d441-111">在**配接器屬性**，從下拉式清單中，選取配接器，例如**WCF SAP**，然後輸入名稱，例如**WCF SAP**。</span><span class="sxs-lookup"><span data-stu-id="8d441-111">In the **Adapter Properties**, select an adapter from the drop-down list, such as **WCF-SAP**, and then enter a name, such as **WCF-SAP**.</span></span>  
  
     <span data-ttu-id="8d441-112">![新增 SAP 配接器至 BizTalk](../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")</span><span class="sxs-lookup"><span data-stu-id="8d441-112">![Add SAP Adapter to BizTalk](../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")</span></span>  
  
5.  <span data-ttu-id="8d441-113">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="8d441-113">Select **OK**.</span></span>  

## <a name="use-a-newer-oracledataaccessdll-version"></a><span data-ttu-id="8d441-114">使用較新版的 Oracle.DataAccess.dll</span><span class="sxs-lookup"><span data-stu-id="8d441-114">Use a newer Oracle.DataAccess.dll version</span></span>  

<span data-ttu-id="8d441-115">當您設定要使用 Wcf-oracledb 配接器，或使用 Visual Studio 使用產生的配接器的連接埠時，會顯示訊息，配接器需要 Oracle.DataAccess.dll 2.111.7.0 版本。</span><span class="sxs-lookup"><span data-stu-id="8d441-115">When you configure a port to use the WCF-OracleDB adapter or use Visual Studio to consume a generated adapter, a message displays that the adapter needs Oracle.DataAccess.dll version 2.111.7.0.</span></span> <span data-ttu-id="8d441-116">若要解決此訊息，請安裝支援的 Oracle.DataAccess.dll 版本 (請參閱[支援版本清單](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx))，然後更新`bindingRedirect`OracleDB 組態檔，請使用下列步驟中的項目：</span><span class="sxs-lookup"><span data-stu-id="8d441-116">To resolve this message, install a supported Oracle.DataAccess.dll version (see [supported version list](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)), and then update the `bindingRedirect` element in the OracleDB configuration file using the following steps:</span></span>  
  
1.  <span data-ttu-id="8d441-117">在 BizTalk 伺服器上，請移至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="8d441-117">On the BizTalk Server, go to the following folders:</span></span>  
  
     <span data-ttu-id="8d441-118">*磁碟機*: \Program Files\Microsoft BizTalk Adapter Pack (x64) \bin</span><span class="sxs-lookup"><span data-stu-id="8d441-118">*drive*:\Program Files\Microsoft BizTalk Adapter Pack(x64)\bin</span></span>  
  
     <span data-ttu-id="8d441-119">*磁碟機*: \Program 檔案 (x86) \Microsoft BizTalk Adapter Pack\bin</span><span class="sxs-lookup"><span data-stu-id="8d441-119">*drive*:\Program Files (x86)\Microsoft BizTalk Adapter Pack\bin</span></span>  
  
2.  <span data-ttu-id="8d441-120">開啟 Microsoft.Adapters.OracleDB.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="8d441-120">Open the Microsoft.Adapters.OracleDB.config file.</span></span>  
  
3.  <span data-ttu-id="8d441-121">尋找下列區段，，然後再複製/貼上下列：</span><span class="sxs-lookup"><span data-stu-id="8d441-121">Find the following section, and then copy/paste the following:</span></span>  
  
    ```  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
              <dependentAssembly>  
                        <assemblyIdentity name="Oracle.DataAccess" publicKeyToken="89b483f429c47342" culture="neutral" />  
                        <bindingRedirect oldVersion="2.111.7.00" newVersion="2.112.1.00"/>  
              </dependentAssembly>  
    </assemblyBinding>  
  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8d441-122">在此範例中，我們設定*newVersion* 2.112.1.00 至。</span><span class="sxs-lookup"><span data-stu-id="8d441-122">In this example, we set *newVersion* to 2.112.1.00.</span></span> <span data-ttu-id="8d441-123">此值設為已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="8d441-123">Set this value to the version you have installed.</span></span>  
  
> [!IMPORTANT]
> - <span data-ttu-id="8d441-124">如果此群組中有多個 BizTalk 伺服器，請在群組中的所有 BizTalk 伺服器上進行這項變更。</span><span class="sxs-lookup"><span data-stu-id="8d441-124">If there are multiple BizTalk Servers in this group, make this change on all the BizTalk servers in the group.</span></span>  
> - <span data-ttu-id="8d441-125">*NewVersion*值需要更新 Oracle.DataAccess.dll 檔案的電腦上安裝的版本為基礎。</span><span class="sxs-lookup"><span data-stu-id="8d441-125">The *newVersion* value needs to be updated based on the version of the Oracle.DataAccess.dll file installed on the computer.</span></span>  <span data-ttu-id="8d441-126">Oracle.DataAccess.dll 隨附於您從 Oracle 安裝 Oracle 用戶端。</span><span class="sxs-lookup"><span data-stu-id="8d441-126">Oracle.DataAccess.dll is included with the Oracle Client you install from Oracle.</span></span>  <span data-ttu-id="8d441-127">您只必須安裝 Oracle 用戶端版本， [BizTalk 配接器組件支援](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8d441-127">You must only install an Oracle Client version that is [supported by the BizTalk Adapter Pack](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx).</span></span>  
  
## <a name="create-sql-server-database-objects-sap-adapter-only"></a><span data-ttu-id="8d441-128">建立 SQL Server 資料庫物件 （只 SAP 配接器）</span><span class="sxs-lookup"><span data-stu-id="8d441-128">Create SQL Server Database objects (SAP adapter only)</span></span>  
 <span data-ttu-id="8d441-129">若要啟動 tRFCs SAP 系統中，執行*SapAdapter-DbScript-Install.sql* SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="8d441-129">To invoke tRFCs in an SAP system, run the *SapAdapter-DbScript-Install.sql* SQL script.</span></span> <span data-ttu-id="8d441-130">此指令碼會隨[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，並在 SQL Server 中建立資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="8d441-130">This script is installed with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, and creates database objects in SQL Server.</span></span> <span data-ttu-id="8d441-131">指令碼通常會安裝在*\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]* 。</span><span class="sxs-lookup"><span data-stu-id="8d441-131">The script is typically installed at *\<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]*.</span></span> <span data-ttu-id="8d441-132">只要您輸入該資料庫名稱來叫用 tRFCs 使用配接器時，您可以針對任何 SQL Server 資料庫，執行此指令碼。</span><span class="sxs-lookup"><span data-stu-id="8d441-132">You can run this script against any SQL Server database, as long as you enter that database name while using the adapter to invoke tRFCs.</span></span>
  
## <a name="register-the-adapter-bindings"></a><span data-ttu-id="8d441-133">註冊配接器繫結</span><span class="sxs-lookup"><span data-stu-id="8d441-133">Register the adapter bindings</span></span>
<span data-ttu-id="8d441-134">期間[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，安裝精靈可能無法註冊配接器繫結或.NET Framework Data Provider for mySAP Business Suite。</span><span class="sxs-lookup"><span data-stu-id="8d441-134">During the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, the setup wizard may fail to register the adapter bindings or the .NET Framework Data Provider for mySAP Business Suite.</span></span> <span data-ttu-id="8d441-135">然後配接器安裝進行安裝。</span><span class="sxs-lookup"><span data-stu-id="8d441-135">And the setup proceeds with the adapter installation.</span></span> <span data-ttu-id="8d441-136">這可能因 Windows Communication Foundation (WCF) 安裝，[!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)]安裝或已損毀的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="8d441-136">This may be caused by the Windows Communication Foundation (WCF) installation, the [!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="8d441-137">完成下列步驟*只*如果安裝精靈無法註冊在 machine.config 檔案中的配接器繫結或.NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="8d441-137">Complete the following steps *only* if the setup wizard fails to register the adapter bindings, or .NET Framework Data Providers in the machine.config file.</span></span>  
  
1.  <span data-ttu-id="8d441-138">移至電腦上的 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="8d441-138">Go to the machine.config file on the computer.</span></span> <span data-ttu-id="8d441-139">例如，32 位元平台上，machine.config 位在*\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG*。</span><span class="sxs-lookup"><span data-stu-id="8d441-139">For example, on a 32-bit platform, the machine.config is available under *\<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG*.</span></span>  
  
2.  <span data-ttu-id="8d441-140">開啟檔案，使用文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="8d441-140">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="8d441-141">註冊配接器繫結：</span><span class="sxs-lookup"><span data-stu-id="8d441-141">Register the adapter bindings:</span></span>  
  
    1.  <span data-ttu-id="8d441-142">搜尋`system.serviceModel`項目，並將其下的面一行加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-142">Search for the `system.serviceModel` element, and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
          <endpoint binding="oracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="8d441-143">搜尋`bindingElementExtensions`system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="8d441-143">Search for the `bindingElementExtensions` element under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="8d441-144">尋找遺漏的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="8d441-144">Look for the missing adapter binding.</span></span> <span data-ttu-id="8d441-145">新增下列各節下的`bindingElementExtensions`節點，根據遺失的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="8d441-145">Add the following sections under the `bindingElementExtensions` node, depending on the missing adapter binding.</span></span> <span data-ttu-id="8d441-146">如果安裝精靈無法註冊任何，您必須註冊的所有繫結。</span><span class="sxs-lookup"><span data-stu-id="8d441-146">You must register all the bindings if the setup wizard fails to register any.</span></span>  
  
         <span data-ttu-id="8d441-147">如[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-147">For the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], add:</span></span>  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="8d441-148">如[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-148">For the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], add:</span></span>  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="8d441-149">如[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-149">For the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="8d441-150">如[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-150">For the [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], add:</span></span>  
  
        ```  
        <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="8d441-151">如[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-151">For the [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="8d441-152">搜尋`bindingExtensions`system.serviceModel\extensions 底下的項目。</span><span class="sxs-lookup"><span data-stu-id="8d441-152">Search for the `bindingExtensions` element under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="8d441-153">尋找遺漏的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="8d441-153">Look for the missing adapter binding.</span></span> <span data-ttu-id="8d441-154">新增下列各節下的`bindingExtensions`節點，根據遺失的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="8d441-154">Add the following sections under the `bindingExtensions` node, depending on the missing adapter binding.</span></span> <span data-ttu-id="8d441-155">如果安裝精靈無法註冊任何，您必須註冊的所有繫結。</span><span class="sxs-lookup"><span data-stu-id="8d441-155">You must register all the bindings if the setup wizard fails to register any.</span></span>  
  
         <span data-ttu-id="8d441-156">如[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-156">For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], add:</span></span>  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="8d441-157">如[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-157">For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], add:</span></span>  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="8d441-158">如[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-158">For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], add:</span></span>  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="8d441-159">如[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-159">For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], add:</span></span>  
  
        ```  
        <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS,Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="8d441-160">如[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-160">For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8d441-161">若要取得的公開金鑰值，請參閱**判斷公開金鑰和版本**（在本主題中）。</span><span class="sxs-lookup"><span data-stu-id="8d441-161">To get the public key value, see **Determine the public key and version** (in this topic).</span></span>  
  
4.  <span data-ttu-id="8d441-162">註冊.NET Framework 資料提供者：</span><span class="sxs-lookup"><span data-stu-id="8d441-162">Register the .NET Framework data providers:</span></span>  
  
    1.  <span data-ttu-id="8d441-163">搜尋`DbProviderFactories`system.data 節點下的項目。</span><span class="sxs-lookup"><span data-stu-id="8d441-163">Search for the `DbProviderFactories` element under the system.data node.</span></span>  
  
    2.  <span data-ttu-id="8d441-164">尋找遺漏的.NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="8d441-164">Look for the missing .NET Framework Data Providers.</span></span> <span data-ttu-id="8d441-165">新增下列各節下的`DbProviderFactories`節點，根據遺失的提供者。</span><span class="sxs-lookup"><span data-stu-id="8d441-165">Add the following sections under the `DbProviderFactories` node, depending on the missing provider.</span></span> <span data-ttu-id="8d441-166">如果安裝精靈無法註冊任何，您必須註冊所有提供者。</span><span class="sxs-lookup"><span data-stu-id="8d441-166">You must register all the providers if the setup wizard fails to register any.</span></span>  
  
         <span data-ttu-id="8d441-167">如[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-167">For the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], add:</span></span>  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
            description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="8d441-168">如[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]，加入：</span><span class="sxs-lookup"><span data-stu-id="8d441-168">For the [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], add:</span></span>  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  <span data-ttu-id="8d441-169">關閉並儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="8d441-169">Save and close the machine.config file.</span></span>  
  
## <a name="determine-the-public-key-and-version"></a><span data-ttu-id="8d441-170">判斷公開金鑰和版本</span><span class="sxs-lookup"><span data-stu-id="8d441-170">Determine the public key and version</span></span>  
 <span data-ttu-id="8d441-171">完成下列步驟來判斷公開金鑰和配接器或.NET Framework Data Provider 的版本。</span><span class="sxs-lookup"><span data-stu-id="8d441-171">Complete the following steps to determine the public key and version for an adapter or the .NET Framework Data Provider.</span></span>  
  
1.  <span data-ttu-id="8d441-172">請移至 Windows 目錄中，通常*C:\WINDOWS\assembly*。</span><span class="sxs-lookup"><span data-stu-id="8d441-172">Go to the Windows directory, typically *C:\WINDOWS\assembly*.</span></span>  
  
2.  <span data-ttu-id="8d441-173">以滑鼠右鍵按一下，您想要的公開金鑰，然後選取 DLL**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8d441-173">Right-click the DLL for which you want the public key, and then select **Properties**.</span></span> <span data-ttu-id="8d441-174">下表列出每個配接器和提供者 Dll 的名稱：</span><span class="sxs-lookup"><span data-stu-id="8d441-174">The following table lists the name of the DLLs for each adapter and provider:</span></span>  
  
    |<span data-ttu-id="8d441-175">配接器/.NET Framework Data Provider</span><span class="sxs-lookup"><span data-stu-id="8d441-175">Adapter/.NET Framework Data Provider</span></span>|<span data-ttu-id="8d441-176">DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="8d441-176">Name of the DLL</span></span>|  
    |---|---|  
    |[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]|<span data-ttu-id="8d441-177">Microsoft.Adapters.SAP</span><span class="sxs-lookup"><span data-stu-id="8d441-177">Microsoft.Adapters.SAP</span></span>|  
    |[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]|<span data-ttu-id="8d441-178">Microsoft.Adapters.Siebel</span><span class="sxs-lookup"><span data-stu-id="8d441-178">Microsoft.Adapters.Siebel</span></span>|  
    |[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]|<span data-ttu-id="8d441-179">Microsoft.Adapters.OracleDB</span><span class="sxs-lookup"><span data-stu-id="8d441-179">Microsoft.Adapters.OracleDB</span></span>|  
    |[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]|<span data-ttu-id="8d441-180">Microsoft.Adapters.OracleEBS</span><span class="sxs-lookup"><span data-stu-id="8d441-180">Microsoft.Adapters.OracleEBS</span></span>|  
    |[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]|<span data-ttu-id="8d441-181">Microsoft.Adapters.Sql.dll</span><span class="sxs-lookup"><span data-stu-id="8d441-181">Microsoft.Adapters.Sql.dll</span></span>|  
    |[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]|<span data-ttu-id="8d441-182">Microsoft.Data.SAPClient</span><span class="sxs-lookup"><span data-stu-id="8d441-182">Microsoft.Data.SAPClient</span></span>|  
    |[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]|<span data-ttu-id="8d441-183">Microsoft.Data.SiebelClient</span><span class="sxs-lookup"><span data-stu-id="8d441-183">Microsoft.Data.SiebelClient</span></span>|  
  
3.  <span data-ttu-id="8d441-184">在**一般**索引標籤上，**公開金鑰語彙基元**值是 DLL 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="8d441-184">On the **General** tab, the **Public Key Token** value is the public key for the DLL.</span></span> <span data-ttu-id="8d441-185">**版本**值是 DLL 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="8d441-185">The **Version** value is the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="8d441-186">複製的公開金鑰，然後選取**取消**。</span><span class="sxs-lookup"><span data-stu-id="8d441-186">Copy the public key, and then select **Cancel**.</span></span>  
  
## <a name="install-the-custom-rfcs"></a><span data-ttu-id="8d441-187">安裝自訂的 Rfc</span><span class="sxs-lookup"><span data-stu-id="8d441-187">Install the custom RFCs</span></span>  
<span data-ttu-id="8d441-188">只有需要*如果*您想要使用[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8d441-188">Required only *if* you want to use the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="8d441-189">請參閱[安裝自訂 Rfc](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)中[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="8d441-189">See [Install Custom RFCs](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md) in the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] documentation.</span></span> 
  
> [!IMPORTANT]
>  <span data-ttu-id="8d441-190">如果您使用較早版本所提供的自訂 Rfc 的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，則您必須將它們升級為此版本提供的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="8d441-190">If you are using an earlier version of the custom RFCs provided with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], then you must upgrade them to the RFCs provided with this release.</span></span> <span data-ttu-id="8d441-191">移除早 Rfc，並再安裝此版本所隨附的 Rfc 這麼做。</span><span class="sxs-lookup"><span data-stu-id="8d441-191">Do this by removing the earlier RFCs, and then installing the RFCs included with this release.</span></span>  

## <a name="install-the-enterprise-applications"></a><span data-ttu-id="8d441-192">安裝企業應用程式</span><span class="sxs-lookup"><span data-stu-id="8d441-192">Install the enterprise applications</span></span>  
<span data-ttu-id="8d441-193">這些步驟與安裝不同的企業部署 LOB 系統的指引，我們建議您針對使用企業系統所提供的安裝指南。</span><span class="sxs-lookup"><span data-stu-id="8d441-193">For the steps and guidance to install the different enterprise LOB systems, we recommend you use the installation guides provided by the enterprise system.</span></span> <span data-ttu-id="8d441-194">如果有的話，也參照特定的組態變更，及其配接器文件。</span><span class="sxs-lookup"><span data-stu-id="8d441-194">Also refer to its adapter documentation for specific configuration changes, if any.</span></span>   

## <a name="installation-and-post-installation-checklist"></a><span data-ttu-id="8d441-195">安裝及安裝後的檢查清單</span><span class="sxs-lookup"><span data-stu-id="8d441-195">Installation and post-installation checklist</span></span>  
  
-   <span data-ttu-id="8d441-196">請確定您已安裝所有[軟體必要條件](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md)使用正確的安裝選項。</span><span class="sxs-lookup"><span data-stu-id="8d441-196">Make sure you installed all the [software prerequisites](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md) with the correct installation option.</span></span>
  
-   <span data-ttu-id="8d441-197">請確定您已安裝在電腦上安裝企業 LOB 應用程式的支援的版本[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8d441-197">Make sure you have the supported version of the enterprise LOB applications installed on your computer where you installed the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="8d441-198">請參閱[支援的特定業務 (LOB) 系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8d441-198">See [Supported Line-of-Business (LOB) systems](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx).</span></span>  
  
-   <span data-ttu-id="8d441-199">若要安裝的企業 LOB 系統，您想要連接的介面卡，請確定您已安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]使用**自訂**安裝選項。</span><span class="sxs-lookup"><span data-stu-id="8d441-199">To install only the adapter for the enterprise LOB system you want to connect, make sure you installed the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] using the **Custom** installation option.</span></span> <span data-ttu-id="8d441-200">請確定您未使用**完成**安裝選項。</span><span class="sxs-lookup"><span data-stu-id="8d441-200">Make sure you did not use the **Complete** installation option.</span></span> <span data-ttu-id="8d441-201">請參閱[安裝 BizTalk Adapter Pack](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="8d441-201">See [Installing the BizTalk Adapter Pack](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md).</span></span>  
  
-   <span data-ttu-id="8d441-202">如果您想要進行 tRFC 呼叫 SAP 系統使用[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，請確定您在 SQL Server 資料庫中建立必要的資料表。</span><span class="sxs-lookup"><span data-stu-id="8d441-202">If you want to make tRFC calls to the SAP system using the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], make sure you create the required tables in a SQL Server database.</span></span> <span data-ttu-id="8d441-203">請參閱**建立 SQL Server 資料庫物件**（在本主題中）。</span><span class="sxs-lookup"><span data-stu-id="8d441-203">See **Create SQL Server Database objects** (in this topic).</span></span>
  
-   <span data-ttu-id="8d441-204">執行時[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝精靈中，您可能會收到錯誤訊息，表示安裝程式無法註冊繫結。</span><span class="sxs-lookup"><span data-stu-id="8d441-204">While running the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] setup wizard, you may get an error message that states the setup failed to register the bindings.</span></span> <span data-ttu-id="8d441-205">如果是的話，手動註冊它們。</span><span class="sxs-lookup"><span data-stu-id="8d441-205">If so, register them manually.</span></span> <span data-ttu-id="8d441-206">請參閱**註冊配接器繫結**（在本主題中）。</span><span class="sxs-lookup"><span data-stu-id="8d441-206">See **Register the adapter bindings** (in this topic).</span></span>  
  
-   <span data-ttu-id="8d441-207">如果您選擇要安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]一部分[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝，請確定您已安裝自訂 Rfc SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="8d441-207">If you chose to install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)] as part of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, make sure you install the custom RFCs on the SAP system.</span></span> <span data-ttu-id="8d441-208">請參閱[安裝自訂 Rfc](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="8d441-208">See [Install Custom RFCs](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>

## <a name="more-good-info"></a><span data-ttu-id="8d441-209">良好的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="8d441-209">More good info</span></span>
[<span data-ttu-id="8d441-210">變更或移除 BizTalk Adapter Pack</span><span class="sxs-lookup"><span data-stu-id="8d441-210">Change or remove the BizTalk Adapter Pack</span></span>](../adapters-and-accelerators/update-or-uninstall-the-biztalk-adapter-pack-2016.md)  
[<span data-ttu-id="8d441-211">BizTalk Adapter Pack 常見問題集</span><span class="sxs-lookup"><span data-stu-id="8d441-211">BizTalk Adapter Pack FAQ</span></span>](../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)