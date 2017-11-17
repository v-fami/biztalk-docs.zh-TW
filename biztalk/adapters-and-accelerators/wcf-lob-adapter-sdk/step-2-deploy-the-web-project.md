---
title: "步驟 2： 部署 Web 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb775a89-2e2d-43e5-94ae-f75c1756dbd7
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85cef88de4e8fa05bb50840002a0f344b1f0b350
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="step-2-deploy-the-web-project"></a><span data-ttu-id="960a4-102">步驟 2： 部署 Web 專案</span><span class="sxs-lookup"><span data-stu-id="960a4-102">Step 2: Deploy the Web Project</span></span>
<span data-ttu-id="960a4-103">![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="960a4-103">![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="960a4-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="960a4-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="960a4-105">在此步驟中，您將發行 Web 專案中產生[步驟 1： 建立 Web 專案中使用配接器服務開發精靈](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md)網際網路資訊服務 (IIS)。</span><span class="sxs-lookup"><span data-stu-id="960a4-105">In this step you will publish the Web project generated in [Step 1: Use the Adapter Service Development Wizard to Create the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md) to Internet Information Services (IIS).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="960a4-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="960a4-106">Prerequisites</span></span>  
 <span data-ttu-id="960a4-107">若要完成此步驟中，您應已完成[步驟 1： 建立 Web 專案中使用配接器服務開發精靈](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md)。</span><span class="sxs-lookup"><span data-stu-id="960a4-107">To complete this step, you should have completed [Step 1: Use the Adapter Service Development Wizard to Create the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md).</span></span> <span data-ttu-id="960a4-108">您的 Web 伺服器也必須安裝到啟用 HTTPS 通訊的 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="960a4-108">Your Web server must also have an SSL certificate installed to enable HTTPS communication.</span></span>  
  
## <a name="compile-and-deploy-the-web-project"></a><span data-ttu-id="960a4-109">編譯及部署 Web 專案</span><span class="sxs-lookup"><span data-stu-id="960a4-109">Compile and deploy the Web project</span></span>  
  
1.  <span data-ttu-id="960a4-110">在 Visual Studio 中，載入 EchoWeb 專案先前所建立。</span><span class="sxs-lookup"><span data-stu-id="960a4-110">In Visual Studio, load the EchoWeb project created previously.</span></span>  
  
2.  <span data-ttu-id="960a4-111">開啟 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="960a4-111">Open a Visual Studio command prompt.</span></span>  
  
3.  <span data-ttu-id="960a4-112">在命令提示字元中，從 [C:\tutorials\echoweb] 資料夾中，輸入下列命令，並再按 ENTER 鍵：</span><span class="sxs-lookup"><span data-stu-id="960a4-112">At the command prompt, from the C:\tutorials\echoweb folder, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="960a4-113">**sn /k EchoWebKey.snk**</span><span class="sxs-lookup"><span data-stu-id="960a4-113">**sn /k EchoWebKey.snk**</span></span>  
  
     <span data-ttu-id="960a4-114">確認訊息，**金鑰組寫入 EchoWebKey.snk**，會出現在命令列。</span><span class="sxs-lookup"><span data-stu-id="960a4-114">A confirmation message, **Key pair written to EchoWebKey.snk**, displays on the command line.</span></span>  
  
4.  <span data-ttu-id="960a4-115">關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="960a4-115">Close the command prompt.</span></span>  
  
5.  <span data-ttu-id="960a4-116">在**方案總管 中**，EchoWeb 專案上按一下滑鼠右鍵，然後選取**發行網站**。</span><span class="sxs-lookup"><span data-stu-id="960a4-116">In **Solution Explorer**, right click the EchoWeb project, and then select **Publish Web Site**.</span></span>  
  
6.  <span data-ttu-id="960a4-117">在**發行網站**對話方塊中，針對**目標位置**，輸入**http://machinename/EchoWeb**。</span><span class="sxs-lookup"><span data-stu-id="960a4-117">In the **Publish Web Site** dialog box, for **Target location**, enter **http://machinename/EchoWeb**.</span></span> <span data-ttu-id="960a4-118">選取**讓這個先行編譯的網站成為可更新**，**使用固定命名和單一網頁組件**，和**啟用強式命名的先行編譯的組件**。</span><span class="sxs-lookup"><span data-stu-id="960a4-118">Select **Allow this precompiled site to be updatable**, **Use fixed naming and single page assemblies**, and **Enable strong naming on precompiled assemblies**.</span></span> <span data-ttu-id="960a4-119">在**金鑰檔案位置**欄位中，按一下省略符號**（...）**按鈕、 選取先前建立的 EchoWebKey.snk 檔案，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="960a4-119">In the **Key file location** field, click the ellipsis **(…)** button, select the EchoWebKey.snk file created previously, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="960a4-120">若要確認已正確建立的網站，請啟動 Internet Explorer 中，輸入**"http://localhost/EchoWeb/EchoOutboundContract.svc"**網址列中，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="960a4-120">To verify that the Web site was correctly created, start Internet Explorer, enter  **"http://localhost/EchoWeb/EchoOutboundContract.svc"** in the address bar, and then press ENTER.</span></span> <span data-ttu-id="960a4-121">說明 EchoOutboundContractClient Web 頁面應該會出現。</span><span class="sxs-lookup"><span data-stu-id="960a4-121">A Web page that describes the EchoOutboundContractClient should appear.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="960a4-122">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="960a4-122">What did I just do?</span></span>  
 <span data-ttu-id="960a4-123">您剛才已發行您的 Web 專案到 IIS。</span><span class="sxs-lookup"><span data-stu-id="960a4-123">You have just published your Web project to IIS.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="960a4-124">後續步驟</span><span class="sxs-lookup"><span data-stu-id="960a4-124">Next Steps</span></span>  
 <span data-ttu-id="960a4-125">現在，您編譯並部署專案之後，您可以繼續進行[步驟 3： 建立應用程式定義檔](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)</span><span class="sxs-lookup"><span data-stu-id="960a4-125">Now that you have compiled and deployed the project, you can proceed to [Step 3: Create an Application Definition File](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="960a4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="960a4-126">See Also</span></span>  
 [<span data-ttu-id="960a4-127">教學課程 3：在 IIS 中裝載 Echo 配接器</span><span class="sxs-lookup"><span data-stu-id="960a4-127">Tutorial 3: Hosting the Echo Adapter in IIS</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)