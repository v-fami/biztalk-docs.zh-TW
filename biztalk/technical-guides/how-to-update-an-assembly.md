---
title: "如何更新組件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f456c8f-247a-4d5c-b5af-41e88968779c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 163b06706652b1f65b9a76e3feea8911a2ca4c88
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-an-assembly"></a><span data-ttu-id="7b1eb-102">如何更新組件</span><span class="sxs-lookup"><span data-stu-id="7b1eb-102">How to Update an Assembly</span></span>
<span data-ttu-id="7b1eb-103">本主題說明如何更新組件和組件使用 Visual Studio 2010 部署的應用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-103">This topic describes how to update the version of an assembly and the application that an assembly is deployed to using Visual Studio 2010.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b1eb-104">如果您是以新版本來更新組件，就不需要重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-104">If you are updating an assembly with a new version, you do not need to restart the application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7b1eb-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="7b1eb-105">Prerequisites</span></span>  
 <span data-ttu-id="7b1eb-106">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-106">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="updating-an-assembly"></a><span data-ttu-id="7b1eb-107">更新組件</span><span class="sxs-lookup"><span data-stu-id="7b1eb-107">Updating an Assembly</span></span>  
  
#### <a name="to-increment-the-version-number-of-an-assembly"></a><span data-ttu-id="7b1eb-108">要遞增組件的版本號碼</span><span class="sxs-lookup"><span data-stu-id="7b1eb-108">To increment the version number of an assembly</span></span>  
  
1.  <span data-ttu-id="7b1eb-109">在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-109">In Solution Explorer, right-click the BizTalk project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="7b1eb-110">在**專案設計工具**，按一下 [**應用程式**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-110">In the **Project Designer**, click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="7b1eb-111">在右窗格中，按一下 **組件資訊**。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-111">In the right pane, click **Assembly Information**.</span></span>  
  
4.  <span data-ttu-id="7b1eb-112">在**組件資訊**對話方塊方塊中，指定的值**組件版本**增加組件版本號碼的欄位。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-112">In the **Assembly Information** dialog box, specify values for the **Assembly Version** field to increase the assembly version number.</span></span> <span data-ttu-id="7b1eb-113">您只應該增加主要或次要的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-113">You should increase only the major or minor version number.</span></span> <span data-ttu-id="7b1eb-114">主要版本號碼是序列中的第一個數字 (***n***.0.0.0); 的次要版本號碼是序列中的第二位數 (0。***n ***.0.0)。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-114">The major version number is the first digit in the sequence (***n***.0.0.0); the minor version number is the second digit in the sequence (0.***n***.0.0).</span></span> <span data-ttu-id="7b1eb-115">BizTalk Server 將無法辨識版本號碼變更為序列，例如 0.0 後面。*** n ***.0 或 0.0.0。***n***.</span><span class="sxs-lookup"><span data-stu-id="7b1eb-115">BizTalk Server will not recognize a version number change that is later in the sequence, such as 0.0.***n***.0 or 0.0.0.***n***.</span></span>  
  
5.  <span data-ttu-id="7b1eb-116">按一下**確定**關閉**組件資訊** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-116">Click **OK** to close the **Assembly Information** dialog box.</span></span>  
  
6.  <span data-ttu-id="7b1eb-117">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-117">Save the project.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7b1eb-118">使用「管線設計師」和「BizTalk 總管物件模型」，避免在遞增組件版本時發生結構描述衝突。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-118">Use the Pipeline Designer and BizTalk Explorer Object Model to avoid schema collisions when incrementing assembly versions.</span></span>  
  
#### <a name="to-change-the-application-that-an-assembly-is-deployed-to"></a><span data-ttu-id="7b1eb-119">若要變更組件部署到應用程式</span><span class="sxs-lookup"><span data-stu-id="7b1eb-119">To change the application that an assembly is deployed to</span></span>  
  
1.  <span data-ttu-id="7b1eb-120">在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-120">In Solution Explorer, right-click the BizTalk project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="7b1eb-121">在**專案設計工具**，按一下 [**部署**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-121">In the **Project Designer**, click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="7b1eb-122">在右窗格中，應用程式中指定名稱**應用程式名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-122">In the right pane, specify the application name in the **Application Name** field.</span></span>  
  
4.  <span data-ttu-id="7b1eb-123">請確認**安裝到全域組件快取**屬性設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-123">Ensure that the **Install to Global Assembly Cache** property is set to **True**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7b1eb-124">當您部署方案時，組件將會部署到新的應用程式中，並且安裝在 GAC 內。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-124">When you deploy the solution, the assemblies will be deployed into the new application and installed in the GAC.</span></span>