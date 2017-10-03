---
title: "使用安裝指令碼動態解析範例安裝 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 644b6403-9883-4256-80d5-37881a87ed0e
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95145af75916001895c03bd0b2665894a43083cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-dynamic-resolution-sample-using-the-install-scripts"></a><span data-ttu-id="c23c1-102">安裝使用安裝指令碼動態解析範例</span><span class="sxs-lookup"><span data-stu-id="c23c1-102">Install the Dynamic Resolution Sample Using the Install Scripts</span></span>
<span data-ttu-id="c23c1-103">本章節描述如何安裝動態解析 」 範例隨附的安裝指令碼從[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c23c1-103">This section describes how you can install the Dynamic Resolution sample from the install scripts provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="c23c1-104">**若要安裝的安裝指令碼動態解析範例**</span><span class="sxs-lookup"><span data-stu-id="c23c1-104">**To install the Dynamic Resolution sample from the install scripts**</span></span>  
  
1.  <span data-ttu-id="c23c1-105">如果您想要執行使用 FTP 的單向傳訊範例，請建立下列 FTP 站台：</span><span class="sxs-lookup"><span data-stu-id="c23c1-105">If you want to execute one-way messaging examples that use FTP, create the following FTP site:</span></span>  
  
    -   <span data-ttu-id="c23c1-106">FTP 虛擬目錄名稱： Out</span><span class="sxs-lookup"><span data-stu-id="c23c1-106">FTP Virtual Directory name: Out</span></span>  
  
    -   <span data-ttu-id="c23c1-107">位置： \Source\Samples\DynamicResolution\Test\FTP\Out</span><span class="sxs-lookup"><span data-stu-id="c23c1-107">Location: \Source\Samples\DynamicResolution\Test\FTP\Out</span></span>  
  
    -   <span data-ttu-id="c23c1-108">權限： 讀取和寫入</span><span class="sxs-lookup"><span data-stu-id="c23c1-108">Permissions: Read and Write</span></span>  
  
    -   <span data-ttu-id="c23c1-109">確定 BizTalk 應用程式使用者群組具有這個位置的完整存取權限</span><span class="sxs-lookup"><span data-stu-id="c23c1-109">Ensure the BizTalk Application Users group has full access permission for this location</span></span>  
  
2.  <span data-ttu-id="c23c1-110">如果您想要執行使用 MQSeries 的雙向傳訊範例，請建立下列使用 WebSphere Explorer:</span><span class="sxs-lookup"><span data-stu-id="c23c1-110">If you want to execute two-way messaging examples that use MQSeries, use WebSphere Explorer to create the following:</span></span>  
  
    -   <span data-ttu-id="c23c1-111">具有名稱 ESB 佇列管理員。DEP 來管理。Sample.QueueManager</span><span class="sxs-lookup"><span data-stu-id="c23c1-111">A queue manager with the name ESB.DEP.Sample.QueueManager</span></span>  
  
    -   <span data-ttu-id="c23c1-112">名為測試佇列。OUT ESB 內。DEP 來管理。Sample.QueueManager</span><span class="sxs-lookup"><span data-stu-id="c23c1-112">A queue named TEST.OUT within the ESB.DEP.Sample.QueueManager</span></span>  
  
3.  <span data-ttu-id="c23c1-113">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="c23c1-113">On the **Start** menu, click **Run**.</span></span>  
  
4.  <span data-ttu-id="c23c1-114">在**執行** 對話方塊中，輸入**cmd**，然後按 ENTER 開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="c23c1-114">In the **Run** dialog box, type **cmd**, and then press ENTER to open the command prompt.</span></span>  
  
5.  <span data-ttu-id="c23c1-115">執行下列命令，取代\<路徑 > 參數與您想要安裝的.cmd 檔案的完整路徑 (在此版本中的預設路徑是 \Source\Samples\DynamicResolution\Install\Scripts\\):</span><span class="sxs-lookup"><span data-stu-id="c23c1-115">Run the following command, replacing the \<path> parameter with the full path to the .cmd file you want to install (the default path in this release is \Source\Samples\DynamicResolution\Install\Scripts\\):</span></span>  
  
    ```  
    <path>\Setup_bin.cmd  
    ```