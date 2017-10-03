---
title: "匯入繫結 Files2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- assemblies, removing from database
- importing binding files
- target computers, cleaning
- BizTalk assemblies, removing from database
ms.assetid: 9e552a4b-06ec-4887-b17b-a625c137699f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3783b21385c210c454bcd3d4c951f2200a6ec866
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-binding-files"></a><span data-ttu-id="9d02c-102">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="9d02c-102">Importing Binding Files</span></span>
<span data-ttu-id="9d02c-103">本節提供有關部署 BizTalk Adapter for JD Edwards EnterpriseOne 時之匯入程序的資訊。</span><span class="sxs-lookup"><span data-stu-id="9d02c-103">This topic provides some information concerning the import process when you deploy BizTalk Adapter for JD Edwards EnterpriseOne.</span></span> <span data-ttu-id="9d02c-104">當您在目標電腦上重新部署繫結檔案 (和組件)，傳送埠和接收位置會在重新匯入 XML 繫結檔案時，被取代為 XML 繫結檔案中的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="9d02c-104">When you redeploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are reimported.</span></span>  
  
### <a name="to-clean-the-target-computer"></a><span data-ttu-id="9d02c-105">若要清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="9d02c-105">To clean the target computer</span></span>  
  
-   <span data-ttu-id="9d02c-106">移除協調流程所繫結的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="9d02c-106">Remove Send ports and Receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="9d02c-107">如果目標電腦上未安裝 Visual Studio，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="9d02c-107">If you do not have Visual Studio installed on the target computer, you can remove the ports by running the scripts:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="9d02c-108">SDK\Samples\Admin\WMI\\</span><span class="sxs-lookup"><span data-stu-id="9d02c-108">SDK\Samples\Admin\WMI\\</span></span>  
  
     <span data-ttu-id="9d02c-109">Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="9d02c-109">Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="9d02c-110">SDK\Samples\Admin\WMI\\</span><span class="sxs-lookup"><span data-stu-id="9d02c-110">SDK\Samples\Admin\WMI\\</span></span>  
  
     <span data-ttu-id="9d02c-111">Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="9d02c-111">Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
     <span data-ttu-id="9d02c-112">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="9d02c-112">For example, from a command prompt run:</span></span>  
  
     <span data-ttu-id="9d02c-113">**cscript RemoveSendPort.vbs\<傳送埠名稱 >**</span><span class="sxs-lookup"><span data-stu-id="9d02c-113">**cscript RemoveSendPort.vbs \<Send port name>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d02c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d02c-114">See Also</span></span>  
 [<span data-ttu-id="9d02c-115">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="9d02c-115">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies3.md)