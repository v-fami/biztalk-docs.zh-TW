---
title: 安裝 JMS MQRFH2 元件範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a5bd855-512f-40a4-8038-ae9b847b1097
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f04067ef6b2e1a057edc05601059d931b7ba7f28
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018599"
---
# <a name="installing-the-jms-mqrfh2-component-sample"></a>安裝 JMS MQRFH2 元件範例
若要使用此範例，其中含有[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，您也必須安裝下列：  
  
- IBM WebSphere MQ 5.3 （含 CSD12) WebSphere MQ 6.x 或 WebSphere MQ 7.0  
  
- IBM"RfhUtil"JMS 測試佇列，和擷取訊息的公用程式  
  
  JMS MQRFH2 元件範例需要 JMS MQRFH2 元件位於您的 Microsoft BizTalk Server 安裝資料夾，以及要在全域組件快取中的對應結構描述的 PipelineComponents 資料夾。 安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]core 會自動複製，並會將組件安裝到正確的位置。 不過，如有需要，您可以手動執行這些工作。  
  
  **若要手動安裝 JMS MQRFH2 元件和結構描述**  
  
1. 將組件 Microsoft.Practices.ESB.JMS.PipelineComponents.dll 複製到 PipelineComponents 資料夾的 BizTalk Server 安裝資料夾。  
  
2. 新增 Microsoft.Practices.ESB.JMS.Schemas.Property.dll 至全域組件快取使用.NET Framework 組態工具位於系統管理工具 區段的結構描述組件**啟動**功能表。  
  
   本節描述安裝 JMS MQRFH2 範例到 GlobalBank.JMS BizTalk 應用程式的程序。 安裝此範例之前，您必須先安裝 ESB Toolkit 核心，如中所述[安裝 BizTalk ESB 工具組核心](http://go.microsoft.com/fwlink/?LinkId=187612)([http://go.microsoft.com/fwlink/?LinkId=187612](http://go.microsoft.com/fwlink/?LinkId=187612))。  
  
   您可以從解決方案專案中安裝 JMS MQRFH2 元件範例，或使用包含的 Windows Installer 檔[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 本節包含下列主題：  
  
-   [使用安裝指令碼安裝 JMS MQRFH2 範例](../esb-toolkit/install-the-jms-mqrfh2-sample-using-the-install-scripts.md)  
  
-   [JMS MQRFH2 元件範例所安裝的組件和成品](../esb-toolkit/assemblies-and-artifacts-installed-by-the-jms-mqrfh2-component-sample.md)  
  
-   [測試 JMS MQRFH2 範例安裝](../esb-toolkit/test-the-jms-mqrfh2-sample-installation.md)