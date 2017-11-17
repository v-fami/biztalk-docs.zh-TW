---
title: "如何發佈 Web 安裝套件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, Web services
- Web services, distributing
- Web services, deploying
ms.assetid: 0db71fdf-80d9-4ad5-b0d4-730d0bb549d4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed7e6277045593360cbdfe57848f7313054b60f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-distribute-the-web-setup-package"></a><span data-ttu-id="7dcc3-102">如何發佈 Web 安裝套件</span><span class="sxs-lookup"><span data-stu-id="7dcc3-102">How to Distribute the Web Setup Package</span></span>
<span data-ttu-id="7dcc3-103">在建立安裝套件之後，您必須建立發佈資料夾，以便在其中複製 MSI 檔案和 BindingInfo.xml 檔案來安裝 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="7dcc3-103">After you create the installation package, you need to create a distribution folder where a MSI file and a BindingInfo.xml file are copied to set up the Web service.</span></span>  
  
### <a name="to-distribute-the-web-setup-package"></a><span data-ttu-id="7dcc3-104">若要發佈 Web 安裝套件</span><span class="sxs-lookup"><span data-stu-id="7dcc3-104">To distribute the Web setup package</span></span>  
  
1.  <span data-ttu-id="7dcc3-105">建立發佈資料夾以包含安裝檔案。</span><span class="sxs-lookup"><span data-stu-id="7dcc3-105">Create a distribution folder to contain your setup files.</span></span>  
  
2.  <span data-ttu-id="7dcc3-106">將 .MSI 檔案從 Web 安裝專案輸出資料夾複製到發佈資料夾。</span><span class="sxs-lookup"><span data-stu-id="7dcc3-106">Copy the .MSI file from the Web Setup project output folder to the distribution folder.</span></span>  
  
3.  <span data-ttu-id="7dcc3-107">將 BindingInfo.xml 檔案從 ASP.NET Web 服務專案資料夾中的暫存資料夾複製到發佈資料夾。</span><span class="sxs-lookup"><span data-stu-id="7dcc3-107">Copy the BindingInfo.xml file from the temp folder in the ASP.NET Web Service project folder to the distribution folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dcc3-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dcc3-108">See Also</span></span>  
 [<span data-ttu-id="7dcc3-109">部署在非 Visual Studio 電腦上的已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="7dcc3-109">Deploying Published Web Services on a Non-Visual Studio Computer</span></span>](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)