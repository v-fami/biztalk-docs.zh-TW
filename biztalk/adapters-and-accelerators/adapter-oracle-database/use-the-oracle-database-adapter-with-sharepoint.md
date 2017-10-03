---
title: "搭配 SharePoint 使用 Oracle 資料庫配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 254204e5-3b5d-4e70-97ab-817660d1206a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cf5be42a008cadba648739037797160386a42fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="use-the-oracle-database-adapter-with-sharepoint"></a><span data-ttu-id="31500-102">搭配 SharePoint 使用 Oracle 資料庫配接器</span><span class="sxs-lookup"><span data-stu-id="31500-102">Use the Oracle Database Adapter with SharePoint</span></span>
<span data-ttu-id="31500-103">針對 WCF 配接器服務開發精靈[!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]可以讓 Microsoft BizTalk Adapter for Oracle 資料庫和 Microsoft BizTalk Adapter for Oracle E-business Suite 直接與 Microsoft SharePoint 中的外部資料來源使用。</span><span class="sxs-lookup"><span data-stu-id="31500-103">The WCF Adapter Service Development Wizard for [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] enables the Microsoft BizTalk Adapter for Oracle Database and the Microsoft BizTalk Adapter for Oracle E-Business Suite to be directly consumed as an external datasource in Microsoft SharePoint.</span></span> <span data-ttu-id="31500-104">新增服務開發精靈支援此功能會使用啟動**WCF 配接器服務**用來建立新 Visual C# 中的網站範本[!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="31500-104">The Add Service Development Wizard that supports this feature is launched with the **WCF Adapter Service** template for creating a new Visual C# Web Sites in [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="31500-105">範本隨附於[!INCLUDE[adapterpacknoversion_md](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="31500-105">The template is included with the [!INCLUDE[adapterpacknoversion_md](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="31500-106">您也必須安裝 Microsoft Windows Communication Foundation (WCF) 的企業營運 (LOB) 配接器 SDK。</span><span class="sxs-lookup"><span data-stu-id="31500-106">You must also install the Microsoft Windows Communication Foundation (WCF) Line of Business (LOB) Adapter SDK.</span></span>  
  
## <a name="sharepoint-operation-support"></a><span data-ttu-id="31500-107">SharePoint 作業支援</span><span class="sxs-lookup"><span data-stu-id="31500-107">SharePoint Operation Support</span></span>  
 <span data-ttu-id="31500-108">配接器服務開發精靈會產生 Oracle 配接器的特殊的服務合約與 Microsoft SharePoint 相容。</span><span class="sxs-lookup"><span data-stu-id="31500-108">The Adapter Service Development wizard generates a special service contract for the Oracle adapters that is compatible with Microsoft SharePoint.</span></span> <span data-ttu-id="31500-109">精靈會產生服務合約，其中包含與 Microsoft SharePoint 整合配接器的下列作業：</span><span class="sxs-lookup"><span data-stu-id="31500-109">The wizard will generate a service contract which includes the following operations for integrating the adapter with Microsoft SharePoint:</span></span>  
  
-   <span data-ttu-id="31500-110">**建立：** CreateItem_ 作業支援。</span><span class="sxs-lookup"><span data-stu-id="31500-110">**Create:** Supported by the CreateItem_ operation.</span></span>  
  
-   <span data-ttu-id="31500-111">**請閱讀：** ReadItem_ 作業支援。</span><span class="sxs-lookup"><span data-stu-id="31500-111">**Read:** Supported by the ReadItem_ operation.</span></span>  
  
-   <span data-ttu-id="31500-112">**更新：** UpdateItem_ 作業支援。</span><span class="sxs-lookup"><span data-stu-id="31500-112">**Update:** Supported by the UpdateItem_ operation.</span></span>  
  
-   <span data-ttu-id="31500-113">**Delete:** DeleteItem_ 作業支援。</span><span class="sxs-lookup"><span data-stu-id="31500-113">**Delete:** Supported by the DeleteItem_ operation.</span></span>  
  
-   <span data-ttu-id="31500-114">**查詢：** ReadList 作業支援。</span><span class="sxs-lookup"><span data-stu-id="31500-114">**Query:** Supported by the ReadList operation.</span></span>  
  
-   <span data-ttu-id="31500-115">**關聯：** Associate_ 作業支援。</span><span class="sxs-lookup"><span data-stu-id="31500-115">**Associate:** Supported by the Associate_ operation.</span></span>  
  
 <span data-ttu-id="31500-116">下列服務合約是做為範例使用 for Microsoft BizTalk Adapter for Oracle 資料庫產生的。</span><span class="sxs-lookup"><span data-stu-id="31500-116">The following service contract was generated using for the Microsoft BizTalk Adapter for Oracle Database as an example.</span></span> <span data-ttu-id="31500-117">配接器已設定為提供 EMP 資料表的存取權</span><span class="sxs-lookup"><span data-stu-id="31500-117">The adapter is configured to provide access to the EMP table</span></span>  
  
```  
[System.ServiceModel.ServiceContractAttribute()]  
public interface ISCOTT_EMP {  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] ReadList(System.Nullable<int> Limit);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void CreateItem(SCOTT_EMP_Record Input);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] ReadItem_EMPNO(System.Nullable<decimal> EMPNO);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void UpdateItem_EMPNO(SCOTT_EMP_Record Input);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void DeleteItem_EMPNO(System.Nullable<decimal> EMPNO);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] Associate_DEPTNO(System.Nullable<decimal> DEPTNO);  
}  
```  
  
## <a name="creating-a-new-web-site-to-host-the-microsoft-biztalk-adapter-for-oracle-database-in-iis"></a><span data-ttu-id="31500-118">建立新的網站裝載在 IIS 中的 Oracle 資料庫的 Microsoft BizTalk Adapter</span><span class="sxs-lookup"><span data-stu-id="31500-118">Creating a New Web Site to Host the Microsoft BizTalk Adapter for Oracle Database in IIS</span></span>  
 <span data-ttu-id="31500-119">下列步驟提供使用 WCF 配接器服務開發精靈來建立新的 WCF web 服務裝載 Microsoft BizTalk Adapter for Oracle 資料庫的範例。</span><span class="sxs-lookup"><span data-stu-id="31500-119">These steps provide an example using the WCF Adapter Service Development Wizard, to create a new WCF web service hosting the Microsoft BizTalk Adapter for Oracle Database.</span></span> <span data-ttu-id="31500-120">服務合約會包含與 Sharepoint 直接相容的作業。</span><span class="sxs-lookup"><span data-stu-id="31500-120">The service contract will include operations directly compatible with Sharepoint.</span></span> <span data-ttu-id="31500-121">因此，它可以做為外部資料來源直接取用。</span><span class="sxs-lookup"><span data-stu-id="31500-121">So that it can be directly consumed as an external datasource.</span></span> <span data-ttu-id="31500-122">配接器設定為驗證與 Oracle 資料庫使用**SCOTT**帳戶。</span><span class="sxs-lookup"><span data-stu-id="31500-122">The adapter is configured to authenticate with the Oracle database using the **SCOTT** account.</span></span> <span data-ttu-id="31500-123">如果**SCOTT**帳戶已被鎖定，您可以藉由以 SYSDBA 的登入 SQL Plus 解除鎖定帳戶。</span><span class="sxs-lookup"><span data-stu-id="31500-123">If the **SCOTT** account is locked, you can unlock the account by logging into SQL Plus as SYSDBA.</span></span>  
  
```  
<Oracle Installation Bin Directory>\Sqlplus.exe SYS AS SYSDBA  
```  
  
 <span data-ttu-id="31500-124">然後執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="31500-124">Then run the following command.</span></span>  
  
```  
SQL> ALTER USER scott ACCOUNT UNLOCK;  
```  
  
#### <a name="creating-the-new-web-site-project"></a><span data-ttu-id="31500-125">建立新的網站專案</span><span class="sxs-lookup"><span data-stu-id="31500-125">Creating the New Web Site Project</span></span>  
  
1.  <span data-ttu-id="31500-126">啟動**Microsoft [!INCLUDE[vs2012](../../includes/vs2012-md.md)]** 。</span><span class="sxs-lookup"><span data-stu-id="31500-126">Start **Microsoft [!INCLUDE[vs2012](../../includes/vs2012-md.md)]**.</span></span>  
  
2.  <span data-ttu-id="31500-127">在[!INCLUDE[vs2010](../../includes/vs2010-md.md)]上**檔案**功能表上，選取**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="31500-127">In [!INCLUDE[vs2010](../../includes/vs2010-md.md)], on the **File** menu, select **New** and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="31500-128">在**新專案**對話方塊方塊中，展開 **其他語言**按一下**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="31500-128">In the **New Project** dialog box, expand **Other Languages** and click **Visual C#**.</span></span> <span data-ttu-id="31500-129">尋找**WCF 配接器服務**在範本清單中，按一下以選取它。</span><span class="sxs-lookup"><span data-stu-id="31500-129">Find the **WCF Adapter Service** in the template list and click it to select it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31500-130">**WCF 配接器服務**並沒有提供範本如果[!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)]未安裝。</span><span class="sxs-lookup"><span data-stu-id="31500-130">The **WCF Adapter Service** template is not available if the [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)] is not installed.</span></span> <span data-ttu-id="31500-131">在 x64 上的系統，同時安裝 x86 和 x64 版本[!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="31500-131">On x64 systems, install both the x86 and x64 versions of the [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)].</span></span>  
  
4.  <span data-ttu-id="31500-132">指定**ScottEMP**為名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="31500-132">Specify **ScottEMP** for the name, and then click **OK**.</span></span> <span data-ttu-id="31500-133">**WCF 配接器服務開發精靈**啟動。</span><span class="sxs-lookup"><span data-stu-id="31500-133">The **WCF Adapter Service Development Wizard** starts.</span></span>  
  
5.  <span data-ttu-id="31500-134">在**簡介**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="31500-134">On the **Introduction** page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="31500-135">在**選擇作業**頁面上，指定**oracleDBBinding**繫結。</span><span class="sxs-lookup"><span data-stu-id="31500-135">On the **Choose Operations** page, specify the **oracleDBBinding** binding.</span></span>  
  
7.  <span data-ttu-id="31500-136">按一下**設定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-136">Click the **Configure** button.</span></span> <span data-ttu-id="31500-137">**設定配接器** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="31500-137">The **Configure Adapter** dialog is displayed.</span></span>  
  
8.  <span data-ttu-id="31500-138">在**安全性**索引標籤上，選取**Username**中**用戶端認證類型**下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="31500-138">On the **Security** tab, select **Username** in the **Client credential type** dropdown list box.</span></span>  
  
9. <span data-ttu-id="31500-139">輸入**SCOTT**使用者名稱並 SCOTT 帳戶輸入正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="31500-139">Enter **SCOTT** for the User name and enter the correct password for the SCOTT account.</span></span> <span data-ttu-id="31500-140">SCOTT 帳戶的預設密碼是**tiger**。</span><span class="sxs-lookup"><span data-stu-id="31500-140">The default password for the SCOTT account is **tiger**.</span></span>  
  
10. <span data-ttu-id="31500-141">按一下**URI 屬性**索引標籤上，輸入在 Oracle 伺服器的 IP 位址或主機名稱**ServerAddress**方塊。</span><span class="sxs-lookup"><span data-stu-id="31500-141">Click the **URI Properties** tab, enter the IP address or host name for your Oracle server in the **ServerAddress** box.</span></span>  
  
11. <span data-ttu-id="31500-142">輸入正確 Oracle 資料庫中的服務執行個體名稱**ServiceName**方塊。</span><span class="sxs-lookup"><span data-stu-id="31500-142">Enter the correct Oracle database service instance name in the **ServiceName** box.</span></span> <span data-ttu-id="31500-143">您可以從 「 Oracle Enterprise Manager 複製的執行個體名稱資訊。</span><span class="sxs-lookup"><span data-stu-id="31500-143">You can copy the instance name information from Oracle Enterprise Manager.</span></span>  
  
12. <span data-ttu-id="31500-144">按**確定**按鈕**設定配接器**對話方塊</span><span class="sxs-lookup"><span data-stu-id="31500-144">Press the **OK** button on the **Configure Adapter** dialog</span></span>  
  
13. <span data-ttu-id="31500-145">在**選擇作業**頁面的精靈中，按一下**連接**按鈕，請稍候片刻建立 Oracle 資料庫的類別。</span><span class="sxs-lookup"><span data-stu-id="31500-145">On the **Choose Operations** page of the wizard, click the **Connect** button and wait a few moments for the categories to be built for the Oracle database.</span></span>  
  
14. <span data-ttu-id="31500-146">類別中加入後**選取類別目錄**清單中，向下捲動至**SCOTT**並將其展開。</span><span class="sxs-lookup"><span data-stu-id="31500-146">Once the categories are added in the **Select a category** list, scroll down to **SCOTT** and expand it.</span></span> <span data-ttu-id="31500-147">然後展開**資料表**按一下**EMP**表格項目。</span><span class="sxs-lookup"><span data-stu-id="31500-147">Then expand **Table** and click the **EMP** table entry.</span></span>  
  
15. <span data-ttu-id="31500-148">在**可用的類別和作業**清單，選取清單中的所有作業，然後按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-148">In the **Available categories and operations** list, select all the operations in the list and click the **Add** button.</span></span> <span data-ttu-id="31500-149">所有作業會都加入至**都加入的類別和作業**清單。</span><span class="sxs-lookup"><span data-stu-id="31500-149">All the operations are added to the **Added categories and operations** list.</span></span>  
  
16. <span data-ttu-id="31500-150">在**選擇作業**頁面上，按一下**下一步** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-150">On the **Choose Operations** page, click the **Next** button.</span></span>  
  
17. <span data-ttu-id="31500-151">在**設定服務與端點行為**頁面上，設定**UseServiceCertificate**服務行為**false**此範例中。</span><span class="sxs-lookup"><span data-stu-id="31500-151">On the **Configure Service and Endpoint Behaviors** page, set the **UseServiceCertificate** Service behavior to **false** for this example.</span></span> <span data-ttu-id="31500-152">然後按一下 [**下一步**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-152">Then click the **Next** button.</span></span>  
  
18. <span data-ttu-id="31500-153">在**設定服務端點繫結和位址**頁面上，按一下**套用** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-153">On the **Configure Service Endpoint Binding and Address** page, click the **Apply** button.</span></span> <span data-ttu-id="31500-154">然後按一下 [**下一步**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-154">Then click the **Next** button.</span></span>  
  
19. <span data-ttu-id="31500-155">在**摘要**頁面上，按一下**完成** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-155">On the **Summary** page, click the **Finish** button.</span></span>  
  
20. <span data-ttu-id="31500-156">按一下**建置**功能表選項，然後按**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="31500-156">Click the **Build** menu option and then click **Build Solution**.</span></span> <span data-ttu-id="31500-157">確認專案建置成功且未發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="31500-157">Verify the project build was successful with no errors.</span></span>  
  
## <a name="publishing-the-new-service-to-iis"></a><span data-ttu-id="31500-158">新的服務發行至 IIS</span><span class="sxs-lookup"><span data-stu-id="31500-158">Publishing the New Service to IIS</span></span>  
 <span data-ttu-id="31500-159">此範例中您將會發行至本機 IIS web 伺服器的配接器主機服務。</span><span class="sxs-lookup"><span data-stu-id="31500-159">For this example you will publish the adapter host service to the local IIS web server.</span></span>  
  
1.  <span data-ttu-id="31500-160">在 方案總管的[!INCLUDE[vs2010](../../includes/vs2010-md.md)]，以滑鼠右鍵按一下**ScottEmp**專案，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="31500-160">In Solution Explorer for [!INCLUDE[vs2010](../../includes/vs2010-md.md)], right click the **ScottEmp** project and click **Properties**.</span></span> <span data-ttu-id="31500-161">專案設計工具索引標籤會顯示。</span><span class="sxs-lookup"><span data-stu-id="31500-161">The Project Designer tabs are displayed.</span></span>  
  
2.  <span data-ttu-id="31500-162">按一下**Web**索引標籤，然後按一下 **使用本機 IIS Web 伺服器**選項。</span><span class="sxs-lookup"><span data-stu-id="31500-162">Click the **Web** tab, then click the **Use Local IIS Web server** option.</span></span>  
  
3.  <span data-ttu-id="31500-163">按一下**建立虛擬目錄** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-163">Click the **Create Virtual Directory** button.</span></span>  
  
4.  <span data-ttu-id="31500-164">開啟網頁瀏覽器服務位址**http://localhost/ScottEmp/ISCOTT_EMP.svc**。</span><span class="sxs-lookup"><span data-stu-id="31500-164">Open a web browser to the service address **http://localhost/ScottEmp/ISCOTT_EMP.svc**.</span></span> <span data-ttu-id="31500-165">您應該會收到 「 您已建立服務 」 的訊息，指出配接器裝載於 IIS。</span><span class="sxs-lookup"><span data-stu-id="31500-165">You should receive a message stating “You have created a service” indicating the adapter is hosted in IIS.</span></span>  
  
## <a name="adding-the-external-data-source-to-a-sharepoint-site-using-sharepoint-designer"></a><span data-ttu-id="31500-166">將外部資料來源加入至 SharePoint 網站使用 SharePoint Designer</span><span class="sxs-lookup"><span data-stu-id="31500-166">Adding the External Data Source to a SharePoint Site using SharePoint Designer</span></span>  
 <span data-ttu-id="31500-167">本章節描述如何將 WCF 服務做為外部資料來源新增至新的網站使用 SharePoint Designer。</span><span class="sxs-lookup"><span data-stu-id="31500-167">This section describes how to add the WCF Service as an external data source to a new Web Site using SharePoint Designer.</span></span>  
  
#### <a name="adding-the-external-data-source"></a><span data-ttu-id="31500-168">加入外部資料來源</span><span class="sxs-lookup"><span data-stu-id="31500-168">Adding the External Data source</span></span>  
  
1.  <span data-ttu-id="31500-169">開啟 SharePoint Designer 並建立新的網站。</span><span class="sxs-lookup"><span data-stu-id="31500-169">Open SharePoint Designer and create a new Web Site.</span></span>  
  
2.  <span data-ttu-id="31500-170">在 SharePoint Designer 中，依序展開**瀏覽**按一下**外部內容類型**中**站台物件**清單。</span><span class="sxs-lookup"><span data-stu-id="31500-170">In SharePoint Designer, expand **Navigation** and click **External Content types** in the **Site Objects** list.</span></span>  
  
3.  <span data-ttu-id="31500-171">按一下**外部內容類型**功能表按鈕，以建立新的外部內容類型。</span><span class="sxs-lookup"><span data-stu-id="31500-171">Click the **External Content Type** menu button to create a new external content type.</span></span>  
  
4.  <span data-ttu-id="31500-172">按一下旁邊的文字**名稱**編輯新的外部內容類型名稱。</span><span class="sxs-lookup"><span data-stu-id="31500-172">Click the text beside **Name** to edit the name of the new external content type.</span></span> <span data-ttu-id="31500-173">輸入**OracleEMP**的名稱。</span><span class="sxs-lookup"><span data-stu-id="31500-173">Enter **OracleEMP** for the name.</span></span>  
  
5.  <span data-ttu-id="31500-174">按一下 [文字] 連結旁邊**外部系統**其中提到：**探索外部資料來源和作業，請按一下這裡。**。</span><span class="sxs-lookup"><span data-stu-id="31500-174">Click the text link beside **External System** which says **Click here to discover external data sources and operations.**.</span></span> <span data-ttu-id="31500-175">這會開啟作業設計工具的 OracleEMP 外部內容類型。</span><span class="sxs-lookup"><span data-stu-id="31500-175">This opens the Operation Designer for the OracleEMP external content type.</span></span>  
  
6.  <span data-ttu-id="31500-176">按一下**加入連接**探索螢幕上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-176">Click the **Add Connection** button on the discovery screen.</span></span>  
  
7.  <span data-ttu-id="31500-177">在 [外部資料來源類型選取項目] 對話方塊中，選擇 [ **WCF 服務**按一下**確定**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-177">In the External Data Source Type Selection dialog, choose **WCF Service** and click the **OK** button.</span></span>  
  
8.  <span data-ttu-id="31500-178">在 WCF 連接對話方塊中，在**服務中繼資料 URL**  方塊中輸入**https://localhost/ScottEmp/ISCOTT_EMP.svc?wsdl**</span><span class="sxs-lookup"><span data-stu-id="31500-178">In the WCF Connection dialog, in the **Service Metadata URL** box enter **https://localhost/ScottEmp/ISCOTT_EMP.svc?wsdl**</span></span>  
  
9. <span data-ttu-id="31500-179">在**Service 端點 URL**  方塊中輸入**https://localhost/ScottEmp/ISCOTT_EMP.svc**</span><span class="sxs-lookup"><span data-stu-id="31500-179">In the **Service Endpoint URL** box enter **https://localhost/ScottEmp/ISCOTT_EMP.svc**</span></span>  
  
10. <span data-ttu-id="31500-180">按一下**確定**按鈕以關閉 [WCF 連接] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="31500-180">Click the **OK** button to close the WCF Connection dialog.</span></span>  
  
11. <span data-ttu-id="31500-181">一旦已填入的資料來源資訊，請展開**https://localhost/ScottEmp/ISCOTT_EMP.svc**資料來源，然後展開**Web 方法**。</span><span class="sxs-lookup"><span data-stu-id="31500-181">Once the Data Source information is populated, expand the **https://localhost/ScottEmp/ISCOTT_EMP.svc** data source and expand **Web Methods**.</span></span>  
  
12. <span data-ttu-id="31500-182">以滑鼠右鍵按一下**ReadList** Web 方法，然後按一下**新讀取清單作業**。</span><span class="sxs-lookup"><span data-stu-id="31500-182">Right click the **ReadList** Web Method and click **New Read List Operation**.</span></span> <span data-ttu-id="31500-183">在讀取清單組態對話方塊就會啟動。</span><span class="sxs-lookup"><span data-stu-id="31500-183">The Read List configuration dialog is launched.</span></span>  
  
13. <span data-ttu-id="31500-184">在讀取清單對話方塊中按一下**傳回參數**按一下**EMPNO**中資料來源項目。</span><span class="sxs-lookup"><span data-stu-id="31500-184">In the Read List dialog click **Return Parameters** and click **EMPNO** in the Data Source Elements.</span></span> <span data-ttu-id="31500-185">按一下**對應至識別碼**。</span><span class="sxs-lookup"><span data-stu-id="31500-185">Click the **Map to identifier**.</span></span>  
  
14. <span data-ttu-id="31500-186">按一下**完成**在讀取清單 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="31500-186">Click **Finish** in the Read List dialog.</span></span>  
  
15. <span data-ttu-id="31500-187">儲存新的外部資料來源輸入**Ctrl + s**。</span><span class="sxs-lookup"><span data-stu-id="31500-187">Save the new external data source by typing **Ctrl+s**.</span></span>  
  
#### <a name="testing-the-external-data-source-connection"></a><span data-ttu-id="31500-188">測試外部資料來源連接</span><span class="sxs-lookup"><span data-stu-id="31500-188">Testing the External Data Source Connection</span></span>  
  
1.  <span data-ttu-id="31500-189">在新的網站上，按一下**建立清單和表單** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-189">In the new web site, click the **Create Lists and Forms** button.</span></span> <span data-ttu-id="31500-190">建立清單和表單 OracleEMP 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="31500-190">The Create List and Form for OracleEMP dialog appears.</span></span>  
  
2.  <span data-ttu-id="31500-191">輸入**OracleEMP_List**清單名稱，然後按一下**確定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-191">Enter **OracleEMP_List** for the List Name and click the **OK** button.</span></span>  
  
3.  <span data-ttu-id="31500-192">清單是一旦建立之後，按一下**摘要檢視**功能表上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-192">Once the list is create, click the **Summary View** button on the menu.</span></span>  
  
4.  <span data-ttu-id="31500-193">按一下**OracleEMP_List**外部清單底下。</span><span class="sxs-lookup"><span data-stu-id="31500-193">Click **OracleEMP_List** under External Lists.</span></span>  
  
5.  <span data-ttu-id="31500-194">按一下**瀏覽器中的預覽**測試配接器的 ReadList 操作功能表上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="31500-194">Click the **Preview in Browser** button on the menu to test the ReadList operation of the adapter.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="31500-195">疑難排解</span><span class="sxs-lookup"><span data-stu-id="31500-195">Troubleshooting</span></span>  
  
-   <span data-ttu-id="31500-196">64 位元電腦上您必須確定也會安裝 32 位元的 Oracle 用戶端元件。</span><span class="sxs-lookup"><span data-stu-id="31500-196">On 64-bit machines you must make sure that 32-bit Oracle client components are also installed.</span></span> <span data-ttu-id="31500-197">這是因為[!INCLUDE[vs2010](../../includes/vs2010-md.md)]，而它的精靈將執行以 32 位元處理序在開發期間需要 32 位元元件的存取權。</span><span class="sxs-lookup"><span data-stu-id="31500-197">This is because [!INCLUDE[vs2010](../../includes/vs2010-md.md)] and it’s wizards will be running as a 32-bit process requiring access to 32-bit components during development.</span></span>