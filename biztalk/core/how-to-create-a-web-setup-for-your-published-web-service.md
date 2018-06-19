---
title: 如何建立 Web 安裝程式已發行的 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, Web services
- Web services, deploying
- Web services, installing
- Web services, .msi file
- .msi files, Web services
ms.assetid: 77c86242-1d27-4d99-ae00-fe2614bc13ef
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87c5ec4fe61c8649fe951460917cfde8788f2e57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249678"
---
# <a name="how-to-create-a-web-setup-for-your-published-web-service"></a><span data-ttu-id="f07c3-102">如何為所發佈的 Web 服務建立 Web 安裝</span><span class="sxs-lookup"><span data-stu-id="f07c3-102">How to Create a Web Setup for Your Published Web Service</span></span>
<span data-ttu-id="f07c3-103">您可以建立安裝套件，以便在實際執行環境中安裝您的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="f07c3-103">You can create an installation package to facilitate setting up your Web service in a production environment.</span></span> <span data-ttu-id="f07c3-104">這個作業會建立 .MSI 檔案。</span><span class="sxs-lookup"><span data-stu-id="f07c3-104">This produces an .MSI file.</span></span>  
  
### <a name="to-create-an-installation-package-to-produce-an-msi-file-using-visual-studio"></a><span data-ttu-id="f07c3-105">若要建立要產生的安裝套件。使用 Visual Studio 的 MSI 檔案</span><span class="sxs-lookup"><span data-stu-id="f07c3-105">To create an installation package to produce an .MSI file using Visual Studio</span></span>  
  
1.  <span data-ttu-id="f07c3-106">開啟您已發佈的 ASP.NET Web 服務專案。</span><span class="sxs-lookup"><span data-stu-id="f07c3-106">Open your published ASP.NET Web service project.</span></span>  
  
2.  <span data-ttu-id="f07c3-107">在 方案總管 中，以滑鼠右鍵按一下方案節點，按一下**新增**，然後按一下 **新專案**。</span><span class="sxs-lookup"><span data-stu-id="f07c3-107">In Solution Explorer, right-click the solution node, click **Add**, and then click **New Project**.</span></span>  
  
3.  <span data-ttu-id="f07c3-108">在**加入新的專案**對話方塊中，於**專案類型**區域中，展開 **其他專案類型**，依序展開**安裝和部署專案**，然後選取**Visual Studio 安裝程式**。</span><span class="sxs-lookup"><span data-stu-id="f07c3-108">In the **Add New Project** dialog box, in the **Project Types** area, expand **Other Project Types**, expand **Setup and Deployment Projects**, and then select **Visual Studio Installer**.</span></span> <span data-ttu-id="f07c3-109">在**範本**區域中，選取**Web 安裝專案**。</span><span class="sxs-lookup"><span data-stu-id="f07c3-109">In the **Templates** area, select **Web Setup Project**.</span></span>  
  
4.  <span data-ttu-id="f07c3-110">在**名稱** 文字方塊中，輸入 Web 安裝專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="f07c3-110">In the **Name** text box, type a name for the Web Setup Project.</span></span> <span data-ttu-id="f07c3-111">您可以使用相同的名稱做為 ASP.NET Web 服務專案並加入"_Setup"做為尾碼，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f07c3-111">You can use the same name as the ASP.NET Web Service project and add "_Setup" as a suffix and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="f07c3-112">在 方案總管 中，以滑鼠右鍵按一下新建立的 Web 安裝專案節點，並指向**檢視**，然後按一下 **檔案系統**。</span><span class="sxs-lookup"><span data-stu-id="f07c3-112">In Solution Explorer, right-click the newly created Web setup project node, and point to **View**, and then click **File System**.</span></span>  
  
6.  <span data-ttu-id="f07c3-113">在**檔案系統**視窗中，以滑鼠右鍵按一下**Web 應用程式資料夾**節點並指向**新增**，然後按一下 **專案輸出**。</span><span class="sxs-lookup"><span data-stu-id="f07c3-113">In the **File System** window, right-click the **Web Application Folder** node and point to **Add**, then click **Project Output**.</span></span>  
  
7.  <span data-ttu-id="f07c3-114">在**加入專案輸出群組**對話方塊中，選取**主要輸出**和**內容檔**從 ASP.NET Web 服務專案，然後按一下**確定**.</span><span class="sxs-lookup"><span data-stu-id="f07c3-114">In the **Add Project Output Group** dialog box, select **Primary Output** and **Content Files** from the ASP.NET Web Service project and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="f07c3-115">在 [方案總管] 中，展開**偵測到的相依性**Web 安裝專案下的節點。</span><span class="sxs-lookup"><span data-stu-id="f07c3-115">In Solution Explorer, expand the **Detected Dependencies** node under the Web setup project.</span></span>  
  
9. <span data-ttu-id="f07c3-116">選取所有相依性。</span><span class="sxs-lookup"><span data-stu-id="f07c3-116">Select all dependencies.</span></span> <span data-ttu-id="f07c3-117">在**屬性**視窗中，將**排除**屬性**True**。</span><span class="sxs-lookup"><span data-stu-id="f07c3-117">In the **Properties** window, set the **Exclude** property to **True**.</span></span>  
  
10. <span data-ttu-id="f07c3-118">建置您的 Web 安裝專案。</span><span class="sxs-lookup"><span data-stu-id="f07c3-118">Build your Web setup project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f07c3-119">如需建立 Web 安裝專案的詳細資訊，請參閱 「 如何建立或加入 Web 安裝專案"中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]協助處[http://go.microsoft.com/fwlink/?LinkId=62268](http://go.microsoft.com/fwlink/?LinkId=62268)。</span><span class="sxs-lookup"><span data-stu-id="f07c3-119">For more information about creating Web setup projects, see "How to Create or Add a Web Setup Project" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection at [http://go.microsoft.com/fwlink/?LinkId=62268](http://go.microsoft.com/fwlink/?LinkId=62268).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f07c3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f07c3-120">See Also</span></span>  
 [<span data-ttu-id="f07c3-121">部署在非 Visual Studio 電腦上的已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="f07c3-121">Deploying Published Web Services on a Non-Visual Studio Computer</span></span>](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)