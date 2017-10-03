---
title: "如何清除目標電腦 2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: cleaning target computer
ms.assetid: 0d25930e-0bee-4658-80e7-4a1ab4a8131d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b15614af9a42489693d535896245254208379d76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-clean-the-target-computer"></a><span data-ttu-id="e69f3-102">如何清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="e69f3-102">How to Clean the Target Computer</span></span>
<span data-ttu-id="e69f3-103">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="e69f3-103">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="e69f3-104">當您在目標電腦上部署繫結檔案 (和組件)，在匯入 XML 繫結檔案時，傳送埠和接收位置會被 XML 繫結檔案中的傳送埠和接收位置所取代。</span><span class="sxs-lookup"><span data-stu-id="e69f3-104">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
### <a name="to-clean-the-target-computer"></a><span data-ttu-id="e69f3-105">若要清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="e69f3-105">To clean the target computer</span></span>  
  
-   <span data-ttu-id="e69f3-106">移除協調流程所繫結的所有傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="e69f3-106">Remove any send ports and receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="e69f3-107">如果目標電腦上尚未安裝 Microsoft Visual Studio，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="e69f3-107">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
     <span data-ttu-id="e69f3-108">\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 傳送 Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="e69f3-108">\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
     <span data-ttu-id="e69f3-109">\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 接收 Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="e69f3-109">\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
     <span data-ttu-id="e69f3-110">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="e69f3-110">For example, at a command prompt, run:</span></span>  
  
     <span data-ttu-id="e69f3-111">**cscript RemoveSendPort.vbs\<傳送埠名稱 >**</span><span class="sxs-lookup"><span data-stu-id="e69f3-111">**cscript RemoveSendPort.vbs \<Send port name>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e69f3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e69f3-112">See Also</span></span>  
 [<span data-ttu-id="e69f3-113">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="e69f3-113">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies2.md)