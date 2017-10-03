---
title: "組件和成品安裝例外狀況管理範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af580992-73d4-4b16-a1cc-fa819b441fca
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65bcb2681cceb450995b18b7dc00d3d8f5a44d30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="assemblies-and-artifacts-installed-by-the-exception-management-samples"></a>組件和成品安裝例外狀況管理範例
下表列出的組件和其他成品 ESB 例外狀況管理範例的安裝。  
  
|位置|類別目錄|名稱和版本的元件|  
|--------------|--------------|---------------------------------------|  
|BizTalk 應用程式 GlobalBank.ESB|協調流程|GlobalBank.ESB.ExceptionHandling.Processes.EAIProcess|  
|||GlobalBank.ESB.ExceptionHandling.Handlers.EAIGenericHandler|  
|||GlobalBank.ESB.ExceptionHandling.Handlers.EAIProcessHandler|  
|BizTalk 應用程式 GlobalBank.ESB|傳送埠|EAIProcessHandler.RepairSubmit|  
|||EAIGenericHandler.PostTmpMsg|  
|||EAIProcess.PostApproval|  
|||EAIProcessHandler.PostDecline|  
|||所有。Exceptions_FILE （參考 GlobalFaultProcessor 管線）|  
|BizTalk 應用程式 GlobalBank.ESB|接收埠|EAIProcess.RequestPort|  
|BizTalk 應用程式 GlobalBank.ESB|接收位置|EAIProcess.RequestPort_FILE|  
|||EAIProcess.ReSubmit_HTTP|  
|BizTalk 應用程式 GlobalBank.ESB|結構描述|GlobalBank.ESB.ExceptionHandling.Schemas.System_Properties 2.0.0.0 版|  
|||GlobalBank.ESB.ExceptionHandling.Schemas.Request 2.0.0.0 版|  
|||GlobalBank.ESB.ExceptionHandling.Schemas.RequestDenied 2.0.0.0 版|  
|BizTalk 應用程式 GlobalBank.ESB|管線|GlobalBank.ESB.ExceptionHandling.Pipelines.GlobalFaultProcessor 2.0.0.0 版|  
|BizTalk 應用程式 GlobalBank.ESB|資源|GlobalBank.ESB.ExceptionHandling.Handlers 2.0.0.0 版|  
|||GlobalBank.ESB.ExceptionHandling.Processes 2.0.0.0 版|  
|||GlobalBank.ESB.ExceptionHandling.Schemas 2.0.0.0 版|  
|||GlobalBank.ESB.ExceptionHandling.Pipelines 2.0.0.0 版|  
|BizTalk 應用程式 GlobalBank.ESB|原則||  
|BizTalk 應用程式 GlobalBank.ESB|地圖|GlobalBank.ESB.ExceptionHandling.Schemas.MapToReqDenied 2.0.0.0 版|  
|全域組件快取|組件|GlobalBank.ESB.ExceptionHandling.Handlers 2.0.0.0 版|  
|||GlobalBank.ESB.ExceptionHandling.Processes 2.0.0.0 版|  
|||GlobalBank.ESB.ExceptionHandling.Schemas 2.0.0.0 版|  
|||GlobalBank.ESB.ExceptionHandling.Pipelines 2.0.0.0 版|  
|%Program Files %\\[!INCLUDE[prague](../includes/prague-md.md)]\Pipeline 元件|管線元件||