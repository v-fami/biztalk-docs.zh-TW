---
title: "使用安裝指令碼的命名空間 」 元件範例安裝 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66046ef4-91a2-4fe7-93ad-3b8137294411
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3e3fc23d938fb9fc209124f7c9beff001d66771
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="install-the-namespace-component-sample-using-the-install-scripts"></a><span data-ttu-id="95257-102">安裝使用安裝指令碼的命名空間 」 元件範例</span><span class="sxs-lookup"><span data-stu-id="95257-102">Install the Namespace Component Sample Using the Install Scripts</span></span>
<span data-ttu-id="95257-103">本章節描述如何安裝 「 命名空間元件 」 範例隨附的 Windows Installer 檔案從[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="95257-103">This section describes how you can install the Namespace Component sample from the Windows Installer file provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="95257-104">**若要從安裝指令碼安裝命名空間 」 元件範例**</span><span class="sxs-lookup"><span data-stu-id="95257-104">**To install the Namespace Component sample from the install scripts**</span></span>  
  
1.  <span data-ttu-id="95257-105">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="95257-105">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="95257-106">在**執行**] 對話方塊中，輸入**cmd**，然後按 ENTER 開啟 [命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="95257-106">In the **Run** dialog box, type **cmd**, and then press ENTER to open a command prompt.</span></span>  
  
3.  <span data-ttu-id="95257-107">執行下列命令，取代*\<路徑\>*參數與您想要安裝的.cmd 檔案的完整路徑 （在此版本中的預設路徑是 \Source\Samples\Namepace\Install\Scripts\\):</span><span class="sxs-lookup"><span data-stu-id="95257-107">Run the following command, replacing the *\<path\>* parameter with the full path to the .cmd file you want to install (the default path in this release is \Source\Samples\Namepace\Install\Scripts\\):</span></span>  
  
    ```  
    <path>\Setup_bin.cmd  
    ```