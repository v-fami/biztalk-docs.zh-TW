---
title: 如何設定強式名稱組件金鑰檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5778a8ec-f5f7-4ae1-a57e-99f6503f044c
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec807cf6b596f7e89f607ebeb56700c59134c211
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968804"
---
# <a name="how-to-configure-a-strong-name-assembly-key-file"></a><span data-ttu-id="8fb43-102">如何設定強式名稱組件金鑰檔案</span><span class="sxs-lookup"><span data-stu-id="8fb43-102">How to Configure a Strong Name Assembly Key File</span></span>
<span data-ttu-id="8fb43-103">在部署 BizTalk 解決方案的程序中，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 會先建置組件。</span><span class="sxs-lookup"><span data-stu-id="8fb43-103">In the process of deploying a BizTalk solution, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] first builds the assemblies.</span></span> <span data-ttu-id="8fb43-104">部署程序要求每個組件都應經過強式簽署。</span><span class="sxs-lookup"><span data-stu-id="8fb43-104">The deployment process requires that each assembly is strongly signed.</span></span> <span data-ttu-id="8fb43-105">您可以將專案與強式名稱組件金鑰檔案產生關聯，即可強式簽署組件。</span><span class="sxs-lookup"><span data-stu-id="8fb43-105">You can strongly sign your assemblies by associating the project with a strong name assembly key file.</span></span> <span data-ttu-id="8fb43-106">如果您還沒有，部署從解決方案之前[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，來產生強式名稱組件金鑰檔案，並將它指派給每個專案方案中使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="8fb43-106">If you haven't already done so, before deploying a solution from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], use the following procedure to generate a strong name assembly key file and assign it to each project in the solution.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8fb43-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="8fb43-107">Prerequisites</span></span>  
 <span data-ttu-id="8fb43-108">若要執行本主題中的程序，您必須登入帳戶的成員[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="8fb43-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrator's group.</span></span> <span data-ttu-id="8fb43-109">此外，您的帳戶必須有全域組件快取 (GAC) 的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="8fb43-109">In addition, your account must have Write permissions on the global assembly cache (GAC).</span></span> <span data-ttu-id="8fb43-110">本機電腦上的「系統管理員」帳戶具有這項權限。</span><span class="sxs-lookup"><span data-stu-id="8fb43-110">The Administrators account on the local computer has this permission.</span></span>  
  
### <a name="to-configure-a-strong-name-assembly-key-file"></a><span data-ttu-id="8fb43-111">若要設定強式名稱組件金鑰檔案</span><span class="sxs-lookup"><span data-stu-id="8fb43-111">To configure a strong name assembly key file</span></span>  
  
1.  <span data-ttu-id="8fb43-112">啟動**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="8fb43-112">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="8fb43-113">在命令提示字元中，切換到您想要儲存金鑰檔案的資料夾，再輸入下列命令，然後按下 ENTER：</span><span class="sxs-lookup"><span data-stu-id="8fb43-113">At the command prompt, from the folder where you want to store the key file, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="8fb43-114">**sn /k***file_name* **.snk** </span><span class="sxs-lookup"><span data-stu-id="8fb43-114">**sn /k**  *file_name* **.snk**</span></span>  
  
     <span data-ttu-id="8fb43-115">範例： **sn /k ErrorHandling.snk**</span><span class="sxs-lookup"><span data-stu-id="8fb43-115">Example: **sn /k ErrorHandling.snk**</span></span>  
  
     <span data-ttu-id="8fb43-116">確認訊息，**金鑰組寫入** \< *file_name*\>**.snk** `,`會出現在命令列。</span><span class="sxs-lookup"><span data-stu-id="8fb43-116">A confirmation message, **Key pair written to** \<*file_name*\>**.snk**`,` displays on the command line.</span></span>  
  
3.  <span data-ttu-id="8fb43-117">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下專案，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8fb43-117">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click the project and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="8fb43-118">按一下**簽署**索引標籤，選擇**瀏覽**中**選擇強式名稱金鑰檔**下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="8fb43-118">Click the **Signing** tab and choose **Browse** in the **Choose a strong name key file** drop down box.</span></span>  
  
5.  <span data-ttu-id="8fb43-119">瀏覽至金鑰檔，然後按一下它。</span><span class="sxs-lookup"><span data-stu-id="8fb43-119">Browse to the key file and click it.</span></span> <span data-ttu-id="8fb43-120">按一下**開啟**，然後關閉 專案屬性。</span><span class="sxs-lookup"><span data-stu-id="8fb43-120">Click **Open**, and then close the project properties.</span></span>  
  
6.  <span data-ttu-id="8fb43-121">針對您想要使用此強式名稱組件金鑰檔案部署方案中的每個專案重複步驟 3 到 6。</span><span class="sxs-lookup"><span data-stu-id="8fb43-121">Repeat steps 3 through 6 for each project in the solution that you want to deploy using this strong name assembly key file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb43-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="8fb43-122">See Also</span></span>  
 [<span data-ttu-id="8fb43-123">從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="8fb43-123">Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application</span></span>](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)