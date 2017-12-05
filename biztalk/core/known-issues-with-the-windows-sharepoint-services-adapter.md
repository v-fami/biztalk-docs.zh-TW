---
title: "Windows SharePoint Services 配接器的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c20eda7-643d-484c-bf5d-59ff69604cea
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ed4f0961bc80a3fe858caaca1d4aa51644912be
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="known-issues-with-the-windows-sharepoint-services-adapter"></a><span data-ttu-id="62d28-102">Windows SharePoint Services 配接器的已知問題</span><span class="sxs-lookup"><span data-stu-id="62d28-102">Known Issues with the Windows SharePoint Services Adapter</span></span>
<span data-ttu-id="62d28-103">本節包含可幫助您避免錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="62d28-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="62d28-104">已知問題</span><span class="sxs-lookup"><span data-stu-id="62d28-104">Known Issues</span></span>  
  
#### <a name="wss-adapter-fails-to-start-a-workflow-attached-to-a-doc-librarysharepoint-list"></a><span data-ttu-id="62d28-105">WSS 配接器無法啟動附加至文件庫/Sharepoint 清單的工作流程</span><span class="sxs-lookup"><span data-stu-id="62d28-105">WSS Adapter Fails to Start a Workflow attached to a Doc Library/Sharepoint List</span></span>  
 <span data-ttu-id="62d28-106">使用 WSS 配接器從 BizTalk 將文件或清單項目提交到文件庫/Sharepoint 清單時，WSS 配接器無法啟動附加到該清單的工作流程。</span><span class="sxs-lookup"><span data-stu-id="62d28-106">When using the WSS Adapter from BizTalk to submit either a document or list item to a Doc Library/Sharepoint List, it fails to start the workflow attached to that List.</span></span> <span data-ttu-id="62d28-107">因應措施是將下列 XML 程式碼複製到 \Program Files\Microsoft BizTalk Server 20xx\Business Activity Services\BTSharePointV3AdapterWS\web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="62d28-107">The workaround is to copy the XML code below into the \Program Files\Microsoft BizTalk Server 20xx\Business Activity Services\BTSharePointV3AdapterWS\web.config file.</span></span>  <span data-ttu-id="62d28-108">下列 XML 程式碼必須插入內部\<組態\>項目。</span><span class="sxs-lookup"><span data-stu-id="62d28-108">The below XML code must be inserted inside of the \<configuration\> element.</span></span>  
  
```  
<configSections>  
    <sectionGroup name="System.Workflow.ComponentModel.WorkflowCompiler" type="System.Workflow.ComponentModel.Compiler.WorkflowCompilerConfigurationSectionGroup, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35">  
      <section name="authorizedTypes" type="System.Workflow.ComponentModel.Compiler.AuthorizedTypesSectionHandler, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
    </sectionGroup>  
  </configSections>  
  <System.Workflow.ComponentModel.WorkflowCompiler>  
    <authorizedTypes>  
      <authorizedType Assembly="System.Workflow.Activities, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Namespace="System.Workflow.*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Namespace="System.Workflow.*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="System.Workflow.Runtime, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Namespace="System.Workflow.*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="Microsoft.SharePoint, Version=12.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" Namespace="Microsoft.SharePoint.Workflow" TypeName="SPWorkflowActivationProperties" Authorized="True" />  
      <authorizedType Assembly="Microsoft.SharePoint, Version=12.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" Namespace="Microsoft.SharePoint.Workflow" TypeName="SPWorkflowTaskProperties" Authorized="True" />  
      <authorizedType Assembly="Microsoft.SharePoint, Version=12.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" Namespace="Microsoft.SharePoint.Workflow" TypeName="SPWorkflowHistoryEventType" Authorized="True" />  
      <authorizedType Assembly="Microsoft.SharePoint.WorkflowActions, Version=12.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" Namespace="Microsoft.SharePoint.WorkflowActions" TypeName="*" Authorized="True" />  
    </authorizedTypes>  
  </System.Workflow.ComponentModel.WorkflowCompiler>  
  
```