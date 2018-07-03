---
title: 第 2 課： 建立 SWIFTSchemas 專案的強式名稱 BizTalk 組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assemblies, creating strong-names
- strong-named assemblies
ms.assetid: 2aacbf38-8b1d-46ea-89ae-5207327bedc1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8e5b9ccc56b6b75ea574f956faac462e5b35dca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995519"
---
# <a name="lesson-2-creating-a-strong-named-biztalk-assembly-for-the-swiftschemas-project"></a><span data-ttu-id="1685d-102">第 2 課： 建立 SWIFTSchemas 專案的強式名稱 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="1685d-102">Lesson 2: Creating a Strong-Named BizTalk Assembly for the SWIFTSchemas Project</span></span>
<span data-ttu-id="1685d-103">在這一課，您會建立強式名稱的編譯和部署 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="1685d-103">In this lesson, you create a strong name upon which the BizTalk assemblies are compiled and deployed.</span></span> <span data-ttu-id="1685d-104">強式名稱組件提供數個安全性優點：</span><span class="sxs-lookup"><span data-stu-id="1685d-104">A strong-named assembly provides several security benefits:</span></span>  
  
- <span data-ttu-id="1685d-105">強式名稱可保證唯一性的組件，藉由指派數位簽章和唯一的金鑰組。</span><span class="sxs-lookup"><span data-stu-id="1685d-105">A strong name guarantees the uniqueness of the assembly by assigning a digital signature and a unique key pair.</span></span>  
  
- <span data-ttu-id="1685d-106">強式名稱可保護組件的歷程，藉由確定沒有其他人可以產生組件的後續版本。</span><span class="sxs-lookup"><span data-stu-id="1685d-106">A strong name protects the lineage of the assembly by ensuring that no one else can generate a subsequent version of the assembly.</span></span>  
  
- <span data-ttu-id="1685d-107">強式名稱提供強式整體性檢查，以保證組件的內容，在上次建置以來尚未變更。</span><span class="sxs-lookup"><span data-stu-id="1685d-107">A strong name provides a strong integrity check to guarantee that the contents of the assembly have not changed since the last build.</span></span>  
  
  <span data-ttu-id="1685d-108">您可以產生金鑰檔使用強式名稱工具 (sn.exe) 隨附[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]或[!INCLUDE[btsDotNetFramework](../../includes/btsdotnetframework-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1685d-108">You can generate a key file by using the strong name tool (sn.exe) that comes with [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] or the [!INCLUDE[btsDotNetFramework](../../includes/btsdotnetframework-md.md)].</span></span>  
  
### <a name="to-create-a-strong-named-biztalk-assembly"></a><span data-ttu-id="1685d-109">若要建立強式名稱 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="1685d-109">To create a strong-named BizTalk assembly</span></span>  
  
1. <span data-ttu-id="1685d-110">啟動 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="1685d-110">Start Visual Studio command prompt.</span></span>  
  
2. <span data-ttu-id="1685d-111">在 Visual Studio 命令提示字元中，瀏覽至\<*磁碟機*\>: \labs 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1685d-111">At the Visual Studio command prompt, browse to the \<*drive*\>:\labs folder.</span></span>  
  
3. <span data-ttu-id="1685d-112">在命令提示字元中，輸入**sn – k swift.snk**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="1685d-112">At the command prompt, type **sn –k swift.snk**, and then press ENTER.</span></span> <span data-ttu-id="1685d-113">請確定在 [輸出] 視窗中出現的成功訊息。</span><span class="sxs-lookup"><span data-stu-id="1685d-113">Ensure that a success message appears in the output window.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="1685d-114">如果未出現正確的訊息，請使用 Visual Studio 來疑難排解您的組件。</span><span class="sxs-lookup"><span data-stu-id="1685d-114">If the correct message does not appear, use Visual Studio to troubleshoot your assembly.</span></span>  
  
4. <span data-ttu-id="1685d-115">在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTSchemas**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="1685d-115">In Solution Explorer, right-click the **SWIFTSchemas** project, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="1685d-116">在 [SWIFTSchemas 屬性頁] 對話方塊中，確定**通用屬性**會展開，然後選取**組件**。</span><span class="sxs-lookup"><span data-stu-id="1685d-116">In the SWIFTSchemas Property Pages dialog box, ensure that **Common Properties** is expanded, and then select **Assembly**.</span></span>  
  
6. <span data-ttu-id="1685d-117">向下和右窗格中的組件屬性捲動**強式名稱**區段中，按一下右邊的方塊**組件金鑰檔案**。</span><span class="sxs-lookup"><span data-stu-id="1685d-117">Scroll down the assembly properties in the right pane, and in the **Strong name** section, click the box to the right of **Assembly Key File**.</span></span> <span data-ttu-id="1685d-118">按一下省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="1685d-118">Click the ellipsis button.</span></span>  
  
7. <span data-ttu-id="1685d-119">在 [組件金鑰檔案] 對話方塊中，瀏覽至 **\<*磁碟機*:\>\labs**。</span><span class="sxs-lookup"><span data-stu-id="1685d-119">In the Assembly Key File dialog box, browse to **\<*drive*:\>\labs**.</span></span>  
  
8. <span data-ttu-id="1685d-120">選取  **swift.snk**金鑰的檔案，為檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="1685d-120">Select the **swift.snk** file as the key file, and then click **Open**.</span></span>  
  
9. <span data-ttu-id="1685d-121">在 [SWIFTSchemas 屬性頁] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1685d-121">In the SWIFTSchemas Property Pages dialog box, click **OK**.</span></span>  
  
10. <span data-ttu-id="1685d-122">在上**檔案**功能表上，按一下**全部儲存**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="1685d-122">On the **File** menu, click **Save All** to save your changes.</span></span>  
  
    <span data-ttu-id="1685d-123">請繼續進行[第 3 課： 將 SWIFT 結構描述加入至專案](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-swift-schemas-to-a-project.md)。</span><span class="sxs-lookup"><span data-stu-id="1685d-123">Proceed to [Lesson 3: Adding SWIFT Schemas to a Project](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-swift-schemas-to-a-project.md).</span></span>