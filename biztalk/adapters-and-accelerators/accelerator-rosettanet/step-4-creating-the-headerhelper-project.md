---
title: "步驟 4： 建立 HeaderHelper 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, helper projects
- private process tutorial, creating helper projects
ms.assetid: 82413537-032a-4368-8d77-d024a7c83b0b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a7a5dc4aa7c3acca26705449108bb75541099c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-creating-the-headerhelper-project"></a><span data-ttu-id="9c5b0-102">步驟 4： 建立 HeaderHelper 專案</span><span class="sxs-lookup"><span data-stu-id="9c5b0-102">Step 4: Creating the HeaderHelper Project</span></span>
<span data-ttu-id="9c5b0-103">在此步驟中，您將建立 [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] 類別庫。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-103">In this step, you create a [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] class library.</span></span> <span data-ttu-id="9c5b0-104">當私用程序協調流程接收到內送訊息時，HeaderHelper 類別庫會判斷是否需要轉換文件，並在需要轉換時，執行轉換。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-104">When a private process orchestration receives an incoming message, the HeaderHelper library determines whether a document conversion is required and if it is required, performs that conversion.</span></span> <span data-ttu-id="9c5b0-105">這讓您的協調流程能夠搭配使用不同版本的 RosettaNet 實作架構 (RNIF) 文件。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-105">This lets your orchestration work with different versions of RosettaNet Implementation Framework (RNIF) documents.</span></span> <span data-ttu-id="9c5b0-106">此外，在傳送 3A2 回應訊息時，HeaderHelper 類別庫會在傳送訊息前執行其他的文件轉換。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-106">Additionally, when a 3A2 response message is sent, the HeaderHelper library performs an additional document conversion before transmitting the message.</span></span>  
  
### <a name="to-create-the-headerhelper-project"></a><span data-ttu-id="9c5b0-107">若要建立 HeaderHelper 專案</span><span class="sxs-lookup"><span data-stu-id="9c5b0-107">To create the HeaderHelper project</span></span>  
  
1.  <span data-ttu-id="9c5b0-108">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，請在 [方案總管] 中，以滑鼠右鍵按一下 Contoso 方案，指向**新增**，然後按一下 **新專案**。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-108">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click the Contoso solution, point to **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="9c5b0-109">在 [加入新的專案] 對話方塊的 [專案類型] 窗格中選取**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-109">In the Add New Project dialog box, in the Project Types pane, select **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="9c5b0-110">在 [範本] 窗格中，選取**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-110">In the Templates pane, select the **Class Library** template.</span></span>  
  
4.  <span data-ttu-id="9c5b0-111">在**名稱**方塊中，輸入**HeaderHelper**，然後按一下 **確定**建立專案。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-111">In the **Name** box, type **HeaderHelper**, and then click **OK** to create the project.</span></span>  
  
5.  <span data-ttu-id="9c5b0-112">在 方案總管 中，以滑鼠右鍵按一下**Class1.cs**檔案**HeaderHelper**專案中，按一下 **重新命名**，型別**HeaderHelper.cs**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-112">In Solution Explorer, right click the **Class1.cs** file in the **HeaderHelper** project, click **Rename**, type **HeaderHelper.cs**, and then press **Enter**.</span></span>  
  
### <a name="to-create-the-helper-class"></a><span data-ttu-id="9c5b0-113">建立 Helper 類別</span><span class="sxs-lookup"><span data-stu-id="9c5b0-113">To create the Helper class</span></span>  
  
1.  <span data-ttu-id="9c5b0-114">在 [方案總管] 中，展開**HeaderHelper**專案，然後再連按兩下**HeaderHelper.cs**節點以開啟 HeaderHelper 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-114">In Solution Explorer, expand the **HeaderHelper** project, and then double-click the **HeaderHelper.cs** node to open the HeaderHelper source file.</span></span>  
  
2.  <span data-ttu-id="9c5b0-115">在原始程式檔中輸入下列程式碼，覆寫所有的現有程式碼：</span><span class="sxs-lookup"><span data-stu-id="9c5b0-115">Type the following code into the source file, overwriting all the existing code:</span></span>  
  
    ```  
    using System;  
    using System.Xml;  
  
    namespace ContosoPriceAndAvailability  
    {  
        public class Helper  
        {  
            static public XmlDocument NormalizeHeader( XmlDocument curPip )  
            {  
                string strInput = curPip.OuterXml;  
                try  
                {  
                    XmlDocument xDoc = new XmlDocument();  
  
                    strInput = strInput.Replace("<!DOCTYPE Pip3A2PriceAndAvailabilityQuery SYSTEM \"3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd\"[]>",String.Empty);  
                    strInput = strInput.Replace("<Pip3A2PriceAndAvailabilityQuery>","<Pip3A2PriceAndAvailabilityQuery xmlns=\"http://schemas.microsoft.com/biztalk/btarn/2004/3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd\">");  
                    strInput = strInput.Replace("xml:",String.Empty);  
                    strInput = strInput.Replace("b:",String.Empty);  
                    strInput = strInput.Replace("lang:",String.Empty);  
                    strInput = strInput.Replace("ns1:",String.Empty);  
  
                    xDoc.LoadXml(strInput);  
  
                    return xDoc;  
                }  
                catch(Exception ex)  
                {  
                    System.Diagnostics.Debug.Write( ex.Message );  
                    throw ex;  
                }  
            }  
  
            static public string ReturnSCWithDocType( XmlDocument xmlDoc )  
            {  
                try  
                {  
                    string sResponse = xmlDoc.InnerXml;  
                    sResponse=sResponse.Replace("ns0:",String.Empty);  
                    xmlDoc.LoadXml(sResponse);  
                    xmlDoc.DocumentElement.RemoveAllAttributes();  
                    sResponse = xmlDoc.InnerXml;  
  
                    sResponse = sResponse.Insert(0,"<!DOCTYPE Pip3A2PriceAndAvailabilityResponse SYSTEM \"3A2PriceAndAvailabilityResponseMessageGuideline_v1_3.dtd\">");  
                    sResponse = sResponse.Replace("ns0:",String.Empty);  
                    sResponse = sResponse.Replace("b:",String.Empty);  
                    sResponse = sResponse.Replace("lang:",String.Empty);  
                    sResponse = sResponse.Replace("ns1:",String.Empty);  
  
                    return sResponse;  
                }  
                catch(Exception ex)  
                {  
                    throw ex;  
                }  
            }  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="9c5b0-116">按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-116">On the **File** menu, click **Save All**.</span></span>  
  
### <a name="to-create-a-strong-named-assembly-for-the-headerhelper-project"></a><span data-ttu-id="9c5b0-117">為 HeaderHelper 專案建立強式名稱組件</span><span class="sxs-lookup"><span data-stu-id="9c5b0-117">To create a strong named assembly for the HeaderHelper project</span></span>  
  
1.  <span data-ttu-id="9c5b0-118">在 [方案總管] 中，以滑鼠右鍵按一下**HeaderHelper**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-118">In Solution Explorer, right-click the **HeaderHelper** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="9c5b0-119">在 [HeaderHelper 屬性頁] 對話方塊中，選取**簽署**從 HeaderHelp 屬性窗格的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-119">In the HeaderHelper Property Pages dialog box, select **Signing** in the left pane of the HeaderHelp properties pane.</span></span>  
  
3.  <span data-ttu-id="9c5b0-120">在右窗格中，按一下 **簽署組件**。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-120">In the right pane, click **Sign the Assembly**.</span></span>  
  
4.  <span data-ttu-id="9c5b0-121">按一下**選擇強式名稱金鑰檔**文字方塊中，然後選取**\<瀏覽 >**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-121">Click the **Choose a strong name key file** text box, and then select **\<Browse>** from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="9c5b0-122">在 [選取檔案] 對話方塊中，移至 Contoso 組件的位置，然後按兩下**FabConPriceAvail.snk**。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-122">In the Select File dialog box, move to the location of your Contoso assembly, and double-click **FabConPriceAvail.snk**.</span></span>  
  
6.  <span data-ttu-id="9c5b0-123">按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-123">On the **File** menu, click **Save All**.</span></span>  
  
7.  <span data-ttu-id="9c5b0-124">在 [方案總管] 中，展開**HeaderHelper**專案中，展開 [**屬性**] 節點，然後再按兩下**AssemblyInfo.cs**節點以開啟 AssemblyInfo.cs原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-124">In Solution Explorer, expand the **HeaderHelper** project, expand the **Properties** node, and then double-click the **AssemblyInfo.cs** node to open the AssemblyInfo.cs source file.</span></span>  
  
8.  <span data-ttu-id="9c5b0-125">在 AssemblyInfo.cs 原始程式檔中，於 AssemblyCulture 屬性的下一行輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="9c5b0-125">In the AssemblyInfo.cs source file, type the following code on the line after the AssemblyCulture attribute:</span></span>  
  
    ```  
    [assembly: AssemblyKeyFile("../../../FabConPriceAvail.snk")]  
    ```  
  
9. <span data-ttu-id="9c5b0-126">按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-126">On the **File** menu, click **Save All**.</span></span>  
  
### <a name="to-build-and-deploy-the-headerhelper-project"></a><span data-ttu-id="9c5b0-127">建置與部署 HeaderHelper 專案</span><span class="sxs-lookup"><span data-stu-id="9c5b0-127">To build and deploy the HeaderHelper project</span></span>  
  
1.  <span data-ttu-id="9c5b0-128">在 [方案總管] 中，以滑鼠右鍵按一下**HeaderHelper**專案，然後再按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-128">In Solution Explorer, right-click the **HeaderHelper** project, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="9c5b0-129">啟動**Visual Studio 2012 的命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-129">Start **Visual Studio 2012 Command Prompt**.</span></span>  
  
3.  <span data-ttu-id="9c5b0-130">在命令提示字元中，移至的位置**HeaderHelper**專案輸出目錄 （\Bin\Debug 資料夾）。</span><span class="sxs-lookup"><span data-stu-id="9c5b0-130">At the command prompt, move to the location of the **HeaderHelper** project output directory (the \Bin\Debug folder).</span></span>  
  
4.  <span data-ttu-id="9c5b0-131">在命令提示字元中，輸入**gacutil /if HeaderHelper.dll**按**Enter**安裝**HeaderHelper**組件**全域組件快取**.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-131">At the command prompt, type **gacutil /if HeaderHelper.dll** and press **Enter** to install the **HeaderHelper** assembly into the **Global Assembly Cache**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c5b0-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c5b0-132">See Also</span></span>  
 [<span data-ttu-id="9c5b0-133">步驟 5： 修改 Contoso 私用程序協調流程</span><span class="sxs-lookup"><span data-stu-id="9c5b0-133">Step 5: Modifying the Contoso Private Process Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-5-modifying-the-contoso-private-process-orchestration.md)