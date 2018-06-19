---
title: 如何顯示所有管理組件規則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7fdec550-6713-4f5f-8c04-d9218bf2df3c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08ec94eb3adb87bf6feaff032e00a61bc9b0fead
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298214"
---
# <a name="how-to-display-all-management-pack-rules"></a><span data-ttu-id="5fc06-102">如何顯示所有管理組件規則</span><span class="sxs-lookup"><span data-stu-id="5fc06-102">How to Display All Management Pack Rules</span></span>
<span data-ttu-id="5fc06-103">您可以使用下列程序來顯示您匯入的管理組件的規則清單。</span><span class="sxs-lookup"><span data-stu-id="5fc06-103">Use the following procedure to display a list of rules for the management packs that you imported.</span></span> <span data-ttu-id="5fc06-104">在 Office Excel 中，您可以檢視的規則清單。</span><span class="sxs-lookup"><span data-stu-id="5fc06-104">The list of rules can be viewed in Office Excel.</span></span>  
  
### <a name="to-display-management-pack-rules"></a><span data-ttu-id="5fc06-105">若要顯示管理組件規則</span><span class="sxs-lookup"><span data-stu-id="5fc06-105">To display management pack rules</span></span>  
  
1.  <span data-ttu-id="5fc06-106">在 管理伺服器中，按一下 **程式**，然後按一下  **System Center**。</span><span class="sxs-lookup"><span data-stu-id="5fc06-106">In your management server, click **Programs**, and then click **System Center**.</span></span>  
  
2.  <span data-ttu-id="5fc06-107">按一下**命令殼層**。</span><span class="sxs-lookup"><span data-stu-id="5fc06-107">Click **Command Shell**.</span></span>  
  
3.  <span data-ttu-id="5fc06-108">在命令殼層中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="5fc06-108">In the Command Shell, type the following command:</span></span>   
    `get-scommanagementpack -DisplayName "BizTalk Server Monitoring" | Get-SCOMRule | export-csv "c:\rules.csv"`  
  
4.  <span data-ttu-id="5fc06-109">建立.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="5fc06-109">A .csv file is created.</span></span> <span data-ttu-id="5fc06-110">您可以在 Office Excel 中開啟.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="5fc06-110">You can open the .csv file in Office Excel.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5fc06-111">在 Office Excel 時，您可能需要指定此.csv 檔案為文字檔。</span><span class="sxs-lookup"><span data-stu-id="5fc06-111">In Office Excel, you may be required to specify that the .csv file is a text file.</span></span>