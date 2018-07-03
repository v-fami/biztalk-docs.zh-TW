---
title: 如何顯示管理組件的監視 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7c4d2b3-9c01-40f5-b983-bf29a3a5cacc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d561c7b49c47d59f7affccaaee582e26db500c09
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010271"
---
# <a name="how-to-display-monitors-for-a-management-pack"></a><span data-ttu-id="d537e-102">如何顯示管理組件的監視</span><span class="sxs-lookup"><span data-stu-id="d537e-102">How to Display Monitors for a Management Pack</span></span>
<span data-ttu-id="d537e-103">若要顯示的輸出清單的管理組件的監視和覆寫命令殼層，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="d537e-103">To display a list of outputs for a management pack's monitors and overrides using the Command Shell, use the following procedure.</span></span>  
  
### <a name="to-display-monitors-for-a-management-pack"></a><span data-ttu-id="d537e-104">若要顯示管理組件的監視</span><span class="sxs-lookup"><span data-stu-id="d537e-104">To display monitors for a management pack</span></span>  
  
1. <span data-ttu-id="d537e-105">在 管理伺服器中，按一下**程式**，然後按一下  **System Center。**</span><span class="sxs-lookup"><span data-stu-id="d537e-105">In your management server, click **Programs**, and then click **System Center.**</span></span>  
  
2. <span data-ttu-id="d537e-106">按一下 **命令殼層**。</span><span class="sxs-lookup"><span data-stu-id="d537e-106">Click **Command Shell**.</span></span>  
  
3. <span data-ttu-id="d537e-107">在命令殼層中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="d537e-107">In the Command Shell, type the following command:</span></span>   
   `get-scommanagementpack –DisplayName “DisplayName” | get-scommonitor | export.csv filename`  
  
4. <span data-ttu-id="d537e-108">建立.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="d537e-108">A .csv file is created.</span></span> <span data-ttu-id="d537e-109">可以在 Microsoft Office Excel 中開啟.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="d537e-109">The .csv file can be opened in Microsoft Office Excel.</span></span>  
  
   > [!NOTE]  
   >  <span data-ttu-id="d537e-110">在 Excel 中，您可能需要指定此.csv 檔案為文字檔。</span><span class="sxs-lookup"><span data-stu-id="d537e-110">In Excel, you may be required to specify that the .csv file is a text file.</span></span>  
  
   <span data-ttu-id="d537e-111">例如，下列命令會擷取資料的其中一個核心管理組件相關聯的監視：</span><span class="sxs-lookup"><span data-stu-id="d537e-111">For example, the following command retrieves data for the monitors associated with one of the core management packs:</span></span>   
   `get-scommanagementpack -DisplayName "BizTalk Server Monitoring" | Get-ScomMonitor | export-csv "c:\monitors.csv"`