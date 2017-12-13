---
title: "部署 A4SWIFT 結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, A4SWIFT
- deploying, A4SWIFT schemas
- A4SWIFT, deploying schemas
- schemas, deploying
ms.assetid: a6aed2cd-3578-442e-ab1e-8284cc5f7b72
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc89b26d0eee970268d5e9084cd0827d3100fd7b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="deploying-a4swift-schemas"></a><span data-ttu-id="07471-102">部署 A4SWIFT 結構描述</span><span class="sxs-lookup"><span data-stu-id="07471-102">Deploying A4SWIFT Schemas</span></span>
<span data-ttu-id="07471-103">您必須部署 SWIFT 訊息要交換的結構描述。</span><span class="sxs-lookup"><span data-stu-id="07471-103">You must deploy schemas for the SWIFT messages that you want to exchange.</span></span>  
  
 <span data-ttu-id="07471-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="07471-104">**Summary**</span></span>  
  
 <span data-ttu-id="07471-105">部署的下列結構描述：</span><span class="sxs-lookup"><span data-stu-id="07471-105">Deploy the following schemas:</span></span>  
  
-   <span data-ttu-id="07471-106">SWIFT 的基底 Types.xsd</span><span class="sxs-lookup"><span data-stu-id="07471-106">SWIFT Base Types.xsd</span></span>  
  
-   <span data-ttu-id="07471-107">SWIFT 的常見資料 Types.xsd</span><span class="sxs-lookup"><span data-stu-id="07471-107">SWIFT Common Data Types.xsd</span></span>  
  
-   <span data-ttu-id="07471-108">訊息類型，例如 MT103.xsd 特定結構描述</span><span class="sxs-lookup"><span data-stu-id="07471-108">Specific schema for a message type, for example, MT103.xsd</span></span>  
  
### <a name="to-create-a-strong-named-swift-project"></a><span data-ttu-id="07471-109">若要建立強式名稱的 SWIFT 專案</span><span class="sxs-lookup"><span data-stu-id="07471-109">To create a strong-named SWIFT project</span></span>  
  
1.  <span data-ttu-id="07471-110">在 Visual Studio 中，按一下 **檔案**，指向 **新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="07471-110">In Visual Studio, click **File**, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="07471-111">在 [新增專案] 對話方塊中**專案類型**窗格中，選取**BizTalk 專案**資料夾。</span><span class="sxs-lookup"><span data-stu-id="07471-111">In the New Project dialog box, in the **Project types** pane, select the **BizTalk Projects** folder.</span></span>  
  
3.  <span data-ttu-id="07471-112">在**範本**窗格中，選取**空白 BizTalk Server 專案**。</span><span class="sxs-lookup"><span data-stu-id="07471-112">In the **Templates** pane, select **Empty BizTalk Server Project**.</span></span>  
  
4.  <span data-ttu-id="07471-113">在**名稱**方塊中，輸入您要針對專案名稱的名稱。</span><span class="sxs-lookup"><span data-stu-id="07471-113">In the **Name** box, type the name you want for the project name.</span></span>  
  
5.  <span data-ttu-id="07471-114">在**方案**方塊中，選取**建立新方案**。</span><span class="sxs-lookup"><span data-stu-id="07471-114">In the **Solution** box, select **Create new Solution**.</span></span> <span data-ttu-id="07471-115">在**位置**方塊中，輸入您要加入至結構描述專案之專案的位置。</span><span class="sxs-lookup"><span data-stu-id="07471-115">In the **Location** box, enter the location of the project that you are adding the schema project to.</span></span>  
  
6.  <span data-ttu-id="07471-116">按一下**確定**開啟新的專案。</span><span class="sxs-lookup"><span data-stu-id="07471-116">Click **OK** to open the new project.</span></span>  
    [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="07471-117">[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]將新專案加入方案總管 中，並在指定的資料夾中建立的專案資料夾和檔案。</span><span class="sxs-lookup"><span data-stu-id="07471-117">[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] adds a new project to Solution Explorer, and creates the project folder and files in the folder specified.</span></span>  
  
7.  <span data-ttu-id="07471-118">啟動 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="07471-118">Start Visual Studio command prompt.</span></span>  
  
8.  <span data-ttu-id="07471-119">在 Visual Studio 命令提示字元中，瀏覽至  **\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT * *。</span><span class="sxs-lookup"><span data-stu-id="07471-119">At the Visual Studio command prompt, browse to **\<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT**.</span></span>  
  
9. <span data-ttu-id="07471-120">在命令提示字元中，輸入**sn – k key.snk**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="07471-120">At the command prompt, type **sn –k key.snk**, and then press ENTER.</span></span> <span data-ttu-id="07471-121">請指出金鑰組已寫入至 key.snk [命令提示字元] 視窗中會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="07471-121">Ensure that a message is displayed in the command-prompt window indicating that a key pair was written to key.snk.</span></span>  
  
10. <span data-ttu-id="07471-122">在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="07471-122">In Solution Explorer, right-click your project name, and then click **Properties**.</span></span>  
  
11. <span data-ttu-id="07471-123">在左窗格中**屬性頁**對話方塊中，按一下 **組件**。</span><span class="sxs-lookup"><span data-stu-id="07471-123">In the left pane of the **Property Pages** dialog box, click **Assembly**.</span></span>  
  
12. <span data-ttu-id="07471-124">在右窗格中**屬性頁**對話方塊中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07471-124">In the right pane of the **Property Pages** dialog box, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis () button.</span></span>  
  
13. <span data-ttu-id="07471-125">在**組件金鑰檔案**對話方塊中，瀏覽至  **\<*磁碟機*\>: \Program Files\Microsoft**[!INCLUDE[btaA4SWIFTNoVersionui](../../includes/btaa4swiftnoversionui-md.md)]，按一下**key.snk**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="07471-125">In the **Assembly Key File** dialog box, browse to **\<*drive*\>:\Program Files\Microsoft**[!INCLUDE[btaA4SWIFTNoVersionui](../../includes/btaa4swiftnoversionui-md.md)], click **key.snk**, and then click **Open**.</span></span>  
  
14. <span data-ttu-id="07471-126">在**屬性頁**對話方塊中，按一下 **確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="07471-126">In the **Property Pages** dialog box, click **OK** to save your changes.</span></span>  
  
### <a name="to-add-a-swift-schema"></a><span data-ttu-id="07471-127">若要加入 SWIFT 的結構描述</span><span class="sxs-lookup"><span data-stu-id="07471-127">To add a SWIFT schema</span></span>  
  
1.  <span data-ttu-id="07471-128">在 Visual Studio 的方案總管中開啟您的專案。</span><span class="sxs-lookup"><span data-stu-id="07471-128">In Solution Explorer of Visual Studio, open your project.</span></span>  
  
2.  <span data-ttu-id="07471-129">以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **現有項目**。</span><span class="sxs-lookup"><span data-stu-id="07471-129">Right-click your project, point to **Add**, and then click **Existing Item**.</span></span>  
  
3.  <span data-ttu-id="07471-130">在**加入現有項目**對話方塊:\\**Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT-SRG\<版本\>\Base 結構描述**。</span><span class="sxs-lookup"><span data-stu-id="07471-130">In the **Add Existing Item** dialog box, in the :\\**Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Schemas**.</span></span> <span data-ttu-id="07471-131">選取**SWIFT 基底 Types.xsd**和**SWIFT 常見資料 Types.xsd**結構描述，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="07471-131">Select the **SWIFT Base Types.xsd** and **SWIFT Common Data Types.xsd** schemas, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="07471-132">以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **加入現有項目**。</span><span class="sxs-lookup"><span data-stu-id="07471-132">Right-click your project, point to **Add**, and then click **Add Existing Item**.</span></span>  
  
5.  <span data-ttu-id="07471-133">在**加入現有項目**對話方塊中，於**查看**下拉式清單方塊中，移至**\<磁碟機\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT \<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category n\MTxxx**。</span><span class="sxs-lookup"><span data-stu-id="07471-133">In the **Add Existing Item** dialog box, in the **Look in** drop-down box, move to **\<drive\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category n\MTxxx**.</span></span> <span data-ttu-id="07471-134">選取訊息類型，結構描述執行個體**MT103.xsd**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="07471-134">Select a schema for a message type, for instance **MT103.xsd**, and then click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07471-135">方案總管 中所示，A4SWIFT 將加入您專案的結構描述。</span><span class="sxs-lookup"><span data-stu-id="07471-135">A4SWIFT adds the schema for your project, as shown in Solution Explorer.</span></span>  
  
6.  <span data-ttu-id="07471-136">在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**建置**。</span><span class="sxs-lookup"><span data-stu-id="07471-136">In Solution Explorer, right-click the project name, and then click **Build**.</span></span>  
  
7.  <span data-ttu-id="07471-137">在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**部署**。</span><span class="sxs-lookup"><span data-stu-id="07471-137">In Solution Explorer, right-click the project name, and then click **Deploy**.</span></span>