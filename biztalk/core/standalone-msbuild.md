---
title: "獨立式 MSBUILD |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21aa3693-3788-4874-b506-6f4584fb4fd5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 584d9d5fa8e0c0f6be64d3761fabe45cd08e5a26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="standalone-msbuild"></a><span data-ttu-id="60580-102">獨立式 MSBUILD</span><span class="sxs-lookup"><span data-stu-id="60580-102">Standalone MSBUILD</span></span>
<span data-ttu-id="60580-103">**專案建置**元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您建立[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]沒有方案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="60580-103">The **Project Build** component of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] allows you to build [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] solutions without [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="60580-104">若要安裝**專案建置**您在伺服器上，選取元件**專案建置元件**選項**其他軟體類別**在安裝期間。</span><span class="sxs-lookup"><span data-stu-id="60580-104">To install the **Project Build** component on your server, select the **Project Build Component** option in the **Additional Software category** during installation.</span></span> <span data-ttu-id="60580-105">您應該取消選取**開發者工具與 SDK**安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]沒有的電腦上[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="60580-105">You should unselect the **Developer Tools and SDK** as you are installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a computer without [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
 <span data-ttu-id="60580-106">如需 MSBUILD 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567)。</span><span class="sxs-lookup"><span data-stu-id="60580-106">For more information on MSBUILD, see [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).</span></span>  
  
## <a name="to-build-a-biztalk-project"></a><span data-ttu-id="60580-107">建置 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="60580-107">To build a BizTalk project</span></span>  
  
1.  <span data-ttu-id="60580-108">按一下 **[開始]**，並按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="60580-108">Click **Start**, and click **Run**.</span></span>  
  
2.  <span data-ttu-id="60580-109">型別**cmd**，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="60580-109">Type **cmd**, and press ENTER.</span></span>  
  
3.  <span data-ttu-id="60580-110">切換至專案目錄，然後執行 MSBUILD 命令以建置 BizTalk 方案。</span><span class="sxs-lookup"><span data-stu-id="60580-110">Switch to the project directory, and run a MSBUILD command to build the BizTalk solution.</span></span>  
  
    ```  
    msbuild unittesttest.sln /p:Configuration=Debug  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="60580-111">您可能需要設定 PATH 環境變數，以指向資料夾 msbuild.exe 所在 (\<*windows 安裝目錄*> \Microsoft.NET\Framework\v4)。</span><span class="sxs-lookup"><span data-stu-id="60580-111">You may need set the PATH environment variable to point to the folder in which msbuild.exe resides (\<*windows installation directory*>\Microsoft.NET\Framework\v4).</span></span>