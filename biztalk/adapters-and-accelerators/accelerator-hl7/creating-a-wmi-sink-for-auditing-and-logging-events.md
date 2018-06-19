---
title: 建立 WMI 的稽核和記錄的事件接收器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WMI sink
- auditing, WMI sink
- WMI sink, auditing
- logging, WMI sink
- WMI sink, logging
ms.assetid: 5feb1e98-32ed-4505-878e-274028d50c3c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d9592bb8fc140fc088906d9d7e565c5cbc40bb3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204550"
---
# <a name="creating-a-wmi-sink-for-auditing-and-logging-events"></a><span data-ttu-id="4d97e-102">建立稽核和記錄事件的 WMI 接收</span><span class="sxs-lookup"><span data-stu-id="4d97e-102">Creating a WMI Sink for Auditing and Logging Events</span></span>
<span data-ttu-id="4d97e-103">您可以使用下列範例程式碼來建立[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]Management Instrumentation (WMI) 接收監視稽核和記錄的事件：</span><span class="sxs-lookup"><span data-stu-id="4d97e-103">You can use the following sample code to create a [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI) sink to monitor auditing and logging events:</span></span>  
  
 `//Create the WMI query and Event watcher and subscribe to events`  
  
 `ManagementEventWatcher watcher = new ManagementEventWatcher ("root/Default", "select * from  PackageEvent");`  
  
 `ManagementBaseObject evtObj = watcher.WaitForNextEvent();`  
  
 `//Do what you want with the event`  
  
## <a name="see-also"></a><span data-ttu-id="4d97e-104">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d97e-104">See Also</span></span>  
 [<span data-ttu-id="4d97e-105">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4d97e-105">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)