---
title: "安裝 「 JMS MQRFH2 元件 」 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a5bd855-512f-40a4-8038-ae9b847b1097
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b522d986524c77a53cf5a847f749a9ce41e2c50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-jms-mqrfh2-component-sample"></a>安裝 JMS MQRFH2 元件範例
若要使用這個範例使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，您也必須安裝下列：  
  
-   IBM WebSphere MQ 5.3 （具有 CSD12) WebSphere MQ 6.x 或 WebSphere MQ 7.0  
  
-   IBM"RfhUtil"JMS 測試佇列和擷取訊息的公用程式  
  
 JMS MQRFH2 元件範例需要 JMS MQRFH2 元件放在您的 Microsoft BizTalk Server 安裝資料夾，以及要在全域組件快取中的對應結構描述的 PipelineComponents 資料夾中。 安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心自動複製和組件安裝到正確的位置。 不過，如果需要，您可以手動執行這些工作。  
  
 **若要手動安裝的 JMS MQRFH2 元件和結構描述**  
  
1.  將組件 Microsoft.Practices.ESB.JMS.PipelineComponents.dll 複製到 PipelineComponents 資料夾，您的 BizTalk Server 安裝資料夾。  
  
2.  加入至全域組件快取使用.NET Framework 組態工具 Microsoft.Practices.ESB.JMS.Schemas.Property.dll 找到系統管理工具 部分中的結構描述組件**啟動**功能表。  
  
 本章節描述 JMS MQRFH2 範例安裝到 GlobalBank.JMS BizTalk 應用程式的程序。 中所述安裝此範例之前，您必須安裝 ESB Toolkit 核心[安裝 BizTalk ESB Toolkit 核心](http://go.microsoft.com/fwlink/?LinkId=187612)([http://go.microsoft.com/fwlink/?LinkId=187612](http://go.microsoft.com/fwlink/?LinkId=187612))。  
  
 您可以從方案專案中安裝 「 JMS MQRFH2 元件 」 範例，或使用隨附的 Windows Installer 檔案[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 本節包含下列主題：  
  
-   [安裝 JMS MQRFH2 範例使用安裝指令碼](../esb-toolkit/install-the-jms-mqrfh2-sample-using-the-install-scripts.md)  
  
-   [組件和成品安裝 JMS MQRFH2 元件範例](../esb-toolkit/assemblies-and-artifacts-installed-by-the-jms-mqrfh2-component-sample.md)  
  
-   [測試 JMS MQRFH2 範例的安裝](../esb-toolkit/test-the-jms-mqrfh2-sample-installation.md)